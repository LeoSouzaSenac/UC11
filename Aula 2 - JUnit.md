# Aula 2 - JUnit: O que é, Anotações e Métodos Principais

## O que é JUnit?

JUnit é um **framework de testes unitários para Java** amplamente utilizado. Ele permite que os desenvolvedores escrevam testes automatizados para verificar se pequenos blocos de código funcionam corretamente.

### Por que usar JUnit?

✅ Facilita a automação dos testes.\
✅ Ajuda a identificar e corrigir erros rapidamente.\
✅ Permite testes independentes e reprodutíveis.\
✅ Integra-se facilmente com ferramentas de CI/CD.

---

## O que são Anotações no JUnit?

No JUnit, as **anotações** são usadas para definir o comportamento dos testes. Elas ajudam a configurar o ambiente antes, durante e depois da execução dos testes.

### Principais Anotações do JUnit 5

#### @Test

Marca um método como um teste unitário.

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class CalculadoraTest {
    @Test
    public void testSomar() {
        Calculadora calc = new Calculadora();
        int resultado = calc.somar(2, 3);
        assertEquals(5, resultado);
    }
}
```

#### @BeforeEach

Executa um código **antes de cada teste**, ideal para inicializar objetos.

```java
import org.junit.jupiter.api.BeforeEach;

public class CalculadoraTest {
    private Calculadora calc;

    @BeforeEach
    public void setUp() {
        calc = new Calculadora();
    }
}
```

#### @AfterEach

Executa um código **após cada teste**, útil para limpar dados temporários.

```java
import org.junit.jupiter.api.AfterEach;

public class CalculadoraTest {
    @AfterEach
    public void tearDown() {
        System.out.println("Teste finalizado");
    }
}
```

#### @BeforeAll

Executa um código **antes de todos os testes**, geralmente usado para inicializações globais.

```java
import org.junit.jupiter.api.BeforeAll;

public class BancoDeDadosTest {
    @BeforeAll
    public static void configurarBancoDeDados() {
        System.out.println("Configurando banco de dados");
    }
}
```

#### @AfterAll

Executa um código **após todos os testes**, útil para liberar recursos.

```java
import org.junit.jupiter.api.AfterAll;

public class BancoDeDadosTest {
    @AfterAll
    public static void limparBancoDeDados() {
        System.out.println("Limpando banco de dados");
    }
}
```

#### @Disabled

Ignora um teste específico, útil para testes temporariamente desativados.

```java
import org.junit.jupiter.api.Disabled;

public class CalculadoraTest {
    @Test
    @Disabled("Ainda não implementado")
    public void testMultiplicacao() {
    }
}
```

---

## Métodos Principais do JUnit

JUnit oferece diversos métodos para validar os resultados esperados nos testes. Alguns dos principais são:

### assertEquals

Compara dois valores e verifica se são iguais.

```java
assertEquals(5, calculadora.somar(2, 3));
```

### assertNotEquals

Verifica se dois valores **não** são iguais.

```java
assertNotEquals(4, calculadora.somar(2, 3));
```

### assertTrue

Verifica se uma expressão booleana é verdadeira.

```java
assertTrue(numero > 0);
```

### assertFalse

Verifica se uma expressão booleana é falsa.

```java
assertFalse(numero < 0);
```

### assertThrows

Verifica se uma exceção esperada é lançada.

```java
assertThrows(ArithmeticException.class, () -> calculadora.dividir(5, 0));
```

---

## Conclusão

JUnit é uma ferramenta poderosa para testes unitários em Java. Com suas anotações e métodos, podemos garantir que nosso código funciona corretamente e evitar problemas antes que cheguem ao usuário final.

