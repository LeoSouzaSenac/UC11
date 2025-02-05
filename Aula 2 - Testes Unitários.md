# Aula 2 - Introdução aos Testes Unitários

## O que são Testes Unitários?

Testes unitários são uma prática essencial no desenvolvimento de software. Eles consistem em verificar se **cada unidade individual** do código funciona como esperado. Normalmente, essas unidades são métodos ou funções específicas dentro de uma classe.

### Objetivo dos Testes Unitários

O principal objetivo dos testes unitários é garantir que **cada parte do software funcione isoladamente**, ajudando a:

✅ Identificar erros precocemente.  
✅ Facilitar a manutenção do código.  
✅ Melhorar a confiabilidade do software.  
✅ Documentar o comportamento esperado do código.  

### Como Funciona um Teste Unitário?

Um teste unitário geralmente segue três etapas:
1. **Configuração**: Define-se o ambiente e os dados necessários para o teste.
2. **Execução**: Chama-se o método que se deseja testar.
3. **Verificação**: Compara-se o resultado obtido com o esperado.

### Exemplo Simples

Vamos supor que temos uma classe `Calculadora` com um método `somar`:

```java
public class Calculadora {
    public int somar(int a, int b) {
        return a + b;
    }
}
```

Podemos criar um teste unitário para garantir que a soma está correta:

```java
import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;

public class CalculadoraTest {
    @Test
    public void testSomar() {
        Calculadora calc = new Calculadora();
        int resultado = calc.somar(2, 3);
        assertEquals(5, resultado, "A soma de 2 + 3 deve ser 5");
    }
}
```

Se o código da `Calculadora` estiver correto, o teste **passará**. Se houver um erro, o teste **falhará**, indicando que o comportamento esperado não foi atendido.

### Conclusão

Testes unitários são uma ferramenta poderosa para garantir a qualidade do software. Ao usá-los regularmente, os desenvolvedores podem evitar problemas e melhorar a confiabilidade do código.

