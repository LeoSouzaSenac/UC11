# **Níveis de Teste**

Os testes de software são essenciais para garantir a qualidade e o funcionamento correto de um sistema. Abaixo estão os quatro principais níveis de teste, com suas definições e exemplos práticos em **Java**.

## 1. **Teste Unitário**

### Definição:
O **Teste Unitário** verifica partes isoladas do código, como funções ou métodos. O objetivo principal é garantir que essas unidades de código funcionem corretamente de forma independente.

### Características:
- Testa uma unidade individual de código (geralmente funções ou métodos).
- Pode ser automatizado.
- Realizado frequentemente por desenvolvedores.
- Utiliza frameworks como JUnit.

### Exemplo:

Considere uma classe simples que tem um método para somar dois números. O teste unitário seria feito para garantir que o método funcione corretamente.

**Classe a ser testada:**

```java
public class Calculadora {

    public int somar(int a, int b) {
        return a + b;
    }
}
```

**Teste Unitário com JUnit:**

```java
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class CalculadoraTest {

    @Test
    public void testSomar() {
        Calculadora calc = new Calculadora();
        
        // Testando somas positivas
        assertEquals(5, calc.somar(2, 3));
        
        // Testando soma com números negativos
        assertEquals(0, calc.somar(-1, 1));
        
        // Testando soma com zero
        assertEquals(0, calc.somar(0, 0));
    }
}
```

---

## 2. **Teste de Integração**

### Definição:
O **Teste de Integração** testa a interação entre diferentes módulos ou componentes do sistema. O objetivo é verificar se os módulos funcionam corretamente juntos.

### Características:
- Testa a integração entre múltiplos componentes.
- Foca em verificar a troca de dados e interações entre os módulos.
- Pode envolver sistemas externos, como APIs ou bancos de dados.

### Exemplo:

Imagine que você tem um sistema de login que depende de uma autenticação. O teste de integração verifica se a autenticação e o banco de dados estão funcionando corretamente juntos.

**Classe de Autenticação:**

```java
public class Autenticacao {

    private Database database;

    public Autenticacao(Database database) {
        this.database = database;
    }

    public boolean autenticar(String usuario, String senha) {
        return database.verificarUsuario(usuario, senha);
    }
}
```

**Classe de Banco de Dados (simulada):**

```java
public class Database {

    public boolean verificarUsuario(String usuario, String senha) {
        // Simula a verificação do banco de dados
        return "admin".equals(usuario) && "1234".equals(senha);
    }
}
```

**Teste de Integração:**

```java
import static org.junit.Assert.assertTrue;
import static org.junit.Assert.assertFalse;
import org.junit.Test;

public class AutenticacaoTest {

    @Test
    public void testAutenticar() {
        Database db = new Database();
        Autenticacao auth = new Autenticacao(db);

        // Testando autenticação bem-sucedida
        assertTrue(auth.autenticar("admin", "1234"));
        
        // Testando autenticação falha
        assertFalse(auth.autenticar("admin", "wrongpassword"));
    }
}
```

---

## 3. **Teste de Sistema**

### Definição:
O **Teste de Sistema** avalia o sistema completo para garantir que ele atenda aos requisitos funcionais e não funcionais. Esse teste envolve a verificação do comportamento geral do sistema e a interação de todos os seus componentes.

### Características:
- Testa o sistema como um todo.
- Verifica se o sistema atende aos requisitos do cliente e aos requisitos técnicos.
- Pode ser realizado manualmente ou com testes automatizados mais avançados.

### Exemplo:

Imagine que você tenha um sistema de e-commerce. O teste de sistema garantiria que o processo de compra funcione desde a escolha do produto até o pagamento.

**Classe de Sistema de Compras:**

```java
public class SistemaDeCompras {

    public String realizarCompra(String produto, String usuario, boolean pagamentoConfirmado) {
        if (produto != null && pagamentoConfirmado) {
            return "Compra realizada com sucesso!";
        }
        return "Falha na compra!";
    }
}
```

**Teste de Sistema:**

```java
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class SistemaDeComprasTest {

    @Test
    public void testRealizarCompra() {
        SistemaDeCompras sistema = new SistemaDeCompras();

        // Testando compra bem-sucedida
        assertEquals("Compra realizada com sucesso!", sistema.realizarCompra("Produto XYZ", "usuario1", true));
        
        // Testando falha na compra
        assertEquals("Falha na compra!", sistema.realizarCompra("Produto XYZ", "usuario1", false));
    }
}
```

---

## 4. **Teste de Aceitação**

### Definição:
O **Teste de Aceitação** é realizado pelo cliente ou usuário final para validar se o sistema atende aos requisitos do negócio. O objetivo principal é garantir que o sistema esteja alinhado com as expectativas do cliente.

### Características:
- Realizado pelo cliente ou equipe de QA.
- Foca em validar se o sistema resolve os problemas de negócios.
- Pode ser realizado manualmente, geralmente com a participação do cliente.

### Exemplo:

Imagine que o cliente deseja verificar se a funcionalidade de login está funcionando corretamente em um sistema. O teste de aceitação garante que o sistema funcione como o cliente espera.

**História de Usuário:**

Como um usuário do sistema, quero poder fazer login com meu nome de usuário e senha para acessar minha conta.

**Critérios de Aceitação:**

- O sistema deve verificar se o nome de usuário e a senha estão corretos.
- O sistema deve permitir o login se os dados estiverem corretos.

**Teste de Aceitação (manual):**

1. O cliente insere "admin" como nome de usuário e "1234" como senha.
2. O cliente clica no botão "Login".
3. O sistema deve permitir o login e exibir a mensagem "Bem-vindo, admin!".
4. O cliente insere "user" como nome de usuário e "wrongpassword" como senha.
5. O cliente clica no botão "Login".
6. O sistema deve exibir a mensagem de erro "Usuário ou senha incorretos".

---

Com isso, temos uma visão mais detalhada dos **Níveis de Teste**, incluindo definições, características e exemplos práticos utilizando **Java**.
