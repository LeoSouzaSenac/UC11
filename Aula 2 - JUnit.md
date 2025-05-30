# **Aula 2 - JUnit: Configuração, Anotações e Métodos Principais**  

## **1️⃣ Configurando o JUnit no NetBeans com Gradle**  

### **Passo 1: Criar um Projeto Gradle no NetBeans**  
1. Abra o **NetBeans**.  
2. Vá em **File** > **New Project**.  
3. Selecione **Gradle** ou **Maven** > **Java Application** e clique em **Next**.  
4. Dê um nome ao projeto e escolha um local para salvá-lo.  
5. Clique em **Finish**.  

---

### **Passo 2: Adicionar Dependências do JUnit**  

Claro! Aqui está a **seção atualizada** com as dependências do JUnit **também na versão Maven**, além do Gradle:

---

## **1️⃣ Configurando o JUnit no NetBeans com Gradle ou Maven**

### **Passo 2: Adicionar Dependências do JUnit**

#### ✅ **Se estiver usando *Gradle***:

Abra o arquivo `build.gradle` e adicione dentro do bloco `dependencies {}`:

```gradle
dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter:5.9.3'
}
```

#### ✅ **Se estiver usando *Maven***:

Abra o arquivo `pom.xml` e adicione dentro da tag `<dependencies>`:

```xml
<dependencies>
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter</artifactId>
        <version>5.9.3</version>
        <scope>test</scope>
    </dependency>
</dependencies>
```

---

> ⚠️ **Dica Importante**: Certifique-se de que o *plugin de testes* do Maven esteja configurado corretamente para usar o JUnit 5. Você pode adicionar o seguinte bloco dentro de `<build>` no `pom.xml`:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>3.0.0-M8</version>
        </plugin>
    </plugins>
</build>
```


---

### **Passo 3: Criar a Estrutura de Testes**  

1. No **NetBeans**, vá até o painel **Projects**.  
2. Expanda o diretório **src/test/java**.  
3. Clique com o botão direito na pasta **test** e selecione **New > Java Class**.  
4. Dê um nome à classe de teste (exemplo: `ContaBancariaTest`) e clique em **Finish**.  

Agora sua estrutura está pronta para começar a escrever testes com JUnit! 🚀  

---

## **2️⃣ O que é JUnit?**  

JUnit é um **framework de testes unitários para Java** amplamente utilizado. Ele permite que os desenvolvedores escrevam testes automatizados para verificar se pequenos blocos de código funcionam corretamente.  

### **Por que usar JUnit?**  

✅ Facilita a automação dos testes.  
✅ Ajuda a identificar e corrigir erros rapidamente.  
✅ Permite testes independentes e reprodutíveis.  
✅ Integra-se facilmente com ferramentas de CI/CD.  

---

## **3️⃣ O que são Anotações no JUnit?**  

No JUnit, as **anotações** são usadas para definir o comportamento dos testes. Elas ajudam a configurar o ambiente antes, durante e depois da execução dos testes.  

### **Principais Anotações do JUnit 5**  

#### **@Test**  
Marca um método como um teste unitário.  

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class ContaBancariaTest {

    @Test
    void testDeposito() {
        ContaBancaria conta = new ContaBancaria(1000); // Saldo inicial
        conta.depositar(500);
        assertEquals(1500, conta.getSaldo(), "O saldo deve ser 1500 após o depósito.");
    }

    @Test
    void testSaque() {
        ContaBancaria conta = new ContaBancaria(1000);
        conta.sacar(200);
        assertEquals(800, conta.getSaldo(), "O saldo deve ser 800 após o saque.");
    }
}
```

---

#### **@BeforeEach**  
Executa um código **antes de cada teste**, ideal para inicializar objetos.  

```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class ContaBancariaTest {

    private ContaBancaria conta;

    @BeforeEach
    void setUp() {
        conta = new ContaBancaria(1000); // Inicializa com R$1000 antes de cada teste
    }

    @Test
    void testDeposito() {
        conta.depositar(500);
        assertEquals(1500, conta.getSaldo());
    }

    @Test
    void testSaque() {
        conta.sacar(200);
        assertEquals(800, conta.getSaldo());
    }
}
```

---

#### **@AfterEach**  
Executa um código **após cada teste**, útil para limpar dados temporários.  

```java
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

class BancoDeDadosTest {

    private BancoDeDados banco;

    @BeforeEach
    void conectarBanco() {
        banco = new BancoDeDados();
        banco.conectar();
    }

    @Test
    void testInsercaoDados() {
        banco.inserir("Usuário Teste");
        assertTrue(banco.existe("Usuário Teste"));
    }

    @AfterEach
    void limparBanco() {
        banco.limparDadosTeste();
    }
}
```

---

#### **@BeforeAll**  
Executa um código **antes de todos os testes**, geralmente usado para inicializações globais.  

```java
import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.Test;

class BancoDeDadosTest {

    private static BancoDeDados banco;

    @BeforeAll
    static void configurarBanco() {
        banco = new BancoDeDados();
        banco.inicializar(); // Cria tabelas e insere dados necessários
    }

    @Test
    void testConsultaDados() {
        assertTrue(banco.consultar("admin"));
    }
}
```

---

#### **@AfterAll**  
Executa um código **após todos os testes**, útil para liberar recursos.  

```java
import org.junit.jupiter.api.AfterAll;
import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.Test;

class BancoDeDadosTest {

    private static BancoDeDados banco;

    @BeforeAll
    static void configurarBanco() {
        banco = new BancoDeDados();
        banco.inicializar();
    }

    @Test
    void testInsercaoDados() {
        banco.inserir("João");
        assertTrue(banco.consultar("João"));
    }

    @AfterAll
    static void fecharBanco() {
        banco.fecharConexao();
    }
}
```

---

#### **@Disabled**  
Ignora um teste específico, útil para testes temporariamente desativados.  

```java
import org.junit.jupiter.api.Disabled;
import org.junit.jupiter.api.Test;

class EmailServiceTest {

    @Test
    @Disabled("Ainda não implementado")
    void testEnvioEmail() {
        // Código será implementado futuramente
    }
}
```

---

## **4️⃣ Métodos Principais do JUnit**  

JUnit oferece diversos métodos para validar os resultados esperados nos testes. Alguns dos principais são:  

### **assertEquals**  
Compara dois valores e verifica se são iguais.  

```java
assertEquals(5, calculadora.somar(2, 3));
```

### **assertNotEquals**  
Verifica se dois valores **não** são iguais.  

```java
assertNotEquals(4, calculadora.somar(2, 3));
```

### **assertTrue**  
Verifica se uma expressão booleana é verdadeira.  

```java
assertTrue(numero > 0);
```

### **assertFalse**  
Verifica se uma expressão booleana é falsa.  

```java
assertFalse(numero < 0);
```

### **assertThrows**  
Verifica se uma exceção esperada é lançada.  

```java
assertThrows(ArithmeticException.class, () -> calculadora.dividir(5, 0));
```

---

## **🔥 Resumo Rápido**  

| **Anotação**   | **Descrição** |
|---------------|--------------|
| `@Test`       | Define um método como um teste unitário. |
| `@BeforeEach` | Executa antes de cada teste (inicialização). |
| `@AfterEach`  | Executa depois de cada teste (limpeza). |
| `@BeforeAll`  | Executa antes de todos os testes (configuração global). |
| `@AfterAll`   | Executa depois de todos os testes (finalização). |
| `@Disabled`   | Ignora um teste temporariamente. |

---

## **5️⃣ Conclusão**  

JUnit é uma ferramenta poderosa para testes unitários em Java. Com suas anotações e métodos, podemos garantir que nosso código funciona corretamente e evitar problemas antes que cheguem ao usuário final. 🚀
