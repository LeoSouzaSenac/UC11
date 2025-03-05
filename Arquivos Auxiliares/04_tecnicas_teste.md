# **Técnicas de Teste**

As técnicas de teste são abordagens que ajudam os testers a estruturar e realizar testes eficazes, garantindo que o software atenda aos requisitos e funcione corretamente. Existem diferentes técnicas que podem ser aplicadas dependendo do tipo de teste e da natureza do sistema.

## 1. **Caixa Preta**

### Definição:
O **Teste de Caixa Preta** foca nas entradas e saídas do sistema, sem considerar como o código interno é implementado. O objetivo é verificar se o sistema responde corretamente aos dados de entrada fornecidos.

### Características:
- Testa a funcionalidade do sistema sem olhar o código-fonte.
- Foca nos requisitos do sistema, como funcionalidade, comportamento e usabilidade.
- Baseado nos requisitos de especificação.

### Exemplo:

Suponha que você tenha um sistema de login. O teste de caixa preta se concentraria nas entradas de login e senha e nos resultados que o sistema gera com base nesses dados. O tester não precisaria saber como o código de autenticação funciona internamente.

```java
public class SistemaDeLogin {

    private String usuarioValido = "admin";
    private String senhaValida = "1234";

    public boolean autenticar(String usuario, String senha) {
        return usuarioValido.equals(usuario) && senhaValida.equals(senha);
    }
}
```

**Teste de Caixa Preta:**

```java
import static org.junit.Assert.assertTrue;
import static org.junit.Assert.assertFalse;
import org.junit.Test;

public class SistemaDeLoginTest {

    @Test
    public void testLoginValido() {
        SistemaDeLogin login = new SistemaDeLogin();
        // Teste de entrada e saída sem olhar o código
        assertTrue(login.autenticar("admin", "1234")); // Esperado: true
    }

    @Test
    public void testLoginInvalido() {
        SistemaDeLogin login = new SistemaDeLogin();
        // Teste de entrada e saída sem olhar o código
        assertFalse(login.autenticar("admin", "senhaErrada")); // Esperado: false
    }
}
```

---

## 2. **Caixa Branca**

### Definição:
O **Teste de Caixa Branca** foca no código-fonte, analisando o fluxo de controle, funções e estrutura interna do software para garantir que o código esteja implementado corretamente.

### Características:
- Exige conhecimento do código-fonte.
- Testa o funcionamento interno do sistema, como loops, condições e fluxos.
- Foca na cobertura de código, como cobertura de caminho, de condição e de fluxo de dados.

### Exemplo:

Considerando a mesma classe de login do exemplo anterior, em um teste de caixa branca, o objetivo seria garantir que todas as ramificações do código, como condições, fossem testadas.

```java
public class SistemaDeLogin {

    private String usuarioValido = "admin";
    private String senhaValida = "1234";

    public boolean autenticar(String usuario, String senha) {
        if (usuario == null || senha == null) {
            return false;
        }
        return usuarioValido.equals(usuario) && senhaValida.equals(senha);
    }
}
```

**Teste de Caixa Branca:**

```java
import static org.junit.Assert.assertTrue;
import static org.junit.Assert.assertFalse;
import org.junit.Test;

public class SistemaDeLoginTest {

    @Test
    public void testLoginValido() {
        SistemaDeLogin login = new SistemaDeLogin();
        assertTrue(login.autenticar("admin", "1234")); // Testando uma condição do código
    }

    @Test
    public void testLoginInvalido() {
        SistemaDeLogin login = new SistemaDeLogin();
        assertFalse(login.autenticar("admin", "senhaErrada")); // Testando outra condição do código
    }

    @Test
    public void testLoginNull() {
        SistemaDeLogin login = new SistemaDeLogin();
        assertFalse(login.autenticar(null, null)); // Teste do código para valores nulos
    }
}
```

---

## 3. **Métodos de Teste**

### 3.1 **Partição de Equivalência**

#### Definição:
A **Partição de Equivalência** divide os dados de entrada em grupos ou classes de equivalência, onde os casos de teste dentro de um grupo se comportam da mesma maneira. Essa técnica visa reduzir o número de casos de teste, garantindo uma boa cobertura.

#### Exemplo:
Imagine que você tenha um campo de idade, onde a idade deve ser entre 18 e 60 anos. A partição de equivalência pode criar três classes:
1. Idades válidas: [18, 60]
2. Idades inválidas abaixo de 18: [0, 17]
3. Idades inválidas acima de 60: [61, ∞]

```java
public class SistemaDeCadastro {

    public boolean validarIdade(int idade) {
        return idade >= 18 && idade <= 60;
    }
}
```

**Teste de Partição de Equivalência:**

```java
import static org.junit.Assert.assertTrue;
import static org.junit.Assert.assertFalse;
import org.junit.Test;

public class SistemaDeCadastroTest {

    @Test
    public void testIdadeValida() {
        SistemaDeCadastro cadastro = new SistemaDeCadastro();
        assertTrue(cadastro.validarIdade(25)); // Teste para idade válida
    }

    @Test
    public void testIdadeInvalidaAbaixo() {
        SistemaDeCadastro cadastro = new SistemaDeCadastro();
        assertFalse(cadastro.validarIdade(17)); // Teste para idade abaixo de 18
    }

    @Test
    public void testIdadeInvalidaAcima() {
        SistemaDeCadastro cadastro = new SistemaDeCadastro();
        assertFalse(cadastro.validarIdade(61)); // Teste para idade acima de 60
    }
}
```

---

### 3.2 **Análise de Valor Limite**

#### Definição:
A **Análise de Valor Limite** testa os valores extremos de um intervalo de entrada. Geralmente, o software pode comportar-se de maneira diferente em torno desses valores, como o menor e o maior valor aceito.

#### Exemplo:
Se o campo de idade permite valores entre 18 e 60 anos, você testaria os valores nos limites (18 e 60) e próximos a eles (17 e 61).

```java
public class SistemaDeCadastro {

    public boolean validarIdade(int idade) {
        return idade >= 18 && idade <= 60;
    }
}
```

**Teste de Análise de Valor Limite:**

```java
import static org.junit.Assert.assertTrue;
import static org.junit.Assert.assertFalse;
import org.junit.Test;

public class SistemaDeCadastroTest {

    @Test
    public void testIdadeLimiteInferior() {
        SistemaDeCadastro cadastro = new SistemaDeCadastro();
        assertTrue(cadastro.validarIdade(18)); // Testando o limite inferior
    }

    @Test
    public void testIdadeLimiteSuperior() {
        SistemaDeCadastro cadastro = new SistemaDeCadastro();
        assertTrue(cadastro.validarIdade(60)); // Testando o limite superior
    }

    @Test
    public void testIdadeForaLimiteInferior() {
        SistemaDeCadastro cadastro = new SistemaDeCadastro();
        assertFalse(cadastro.validarIdade(17)); // Testando abaixo do limite inferior
    }

    @Test
    public void testIdadeForaLimiteSuperior() {
        SistemaDeCadastro cadastro = new SistemaDeCadastro();
        assertFalse(cadastro.validarIdade(61)); // Testando acima do limite superior
    }
}
```

---

### 3.3 **Tabelas de Decisão**

#### Definição:
As **Tabelas de Decisão** são usadas para mapear combinações de entradas e suas saídas correspondentes, utilizando regras lógicas para definir diferentes cenários de teste.

#### Exemplo:
Imagine um sistema que valida descontos com base no tipo de cliente e no valor da compra. A tabela de decisão pode ser estruturada da seguinte forma:

| Tipo de Cliente | Valor da Compra | Desconto |
|-----------------|-----------------|----------|
| Regular         | > 100           | 10%      |
| Regular         | ≤ 100           | 5%       |
| VIP             | > 100           | 20%      |
| VIP             | ≤ 100           | 15%      |

```java
public class SistemaDeDesconto {

    public double calcularDesconto(String tipoCliente, double valorCompra) {
        if ("VIP".equals(tipoCliente)) {
            return valorCompra > 100 ? 0.20 : 0.15;
        } else {
            return valorCompra > 100 ? 0.10 : 0.05;
        }
    }
}
```

**Teste com Tabela de Decisão:**

```java
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class SistemaDeDescontoTest {

    @Test
    public void testDescontoVIPAcima100() {
        SistemaDeDesconto desconto = new SistemaDeDesconto();
        assertEquals(0.20, desconto.calcularDesconto("VIP", 150), 0.01);
    }

    @Test
    public void testDescontoVIPAbaixo100() {
        SistemaDeDesconto desconto = new SistemaDeDesconto();
        assertEquals(0.15, desconto.calcularDesconto("VIP", 80), 0.01);
    }

    @Test
    public void testDescontoRegularAcima100() {
        SistemaDeDesconto desconto = new SistemaDeDesconto();
        assertEquals(0.10, desconto.calcularDesconto("Regular", 150), 0.01);
    }

    @Test
    public void testDescontoRegularAbaixo100() {
        SistemaDeDesconto desconto = new SistemaDeDesconto();
        assertEquals(0.05, desconto.calcularDesconto("Regular", 80), 0.01);
    }
}
```

---

### 3.4 **Transição de Estado**

#### Definição:
A **Transição de Estado** avalia o comportamento do sistema em diferentes estados. O sistema pode ter múltiplos estados e transitar entre eles com base em eventos ou entradas.

#### Exemplo:
Suponha um sistema que gerencia pedidos. O pedido pode ter os estados "Novo", "Processando" e "Concluído". A transição entre esses estados deve ser corretamente gerenciada.

```java
public class SistemaDePedido {

    public enum Estado {
        NOVO, PROCESSANDO, CONCLUIDO;
    }

    private Estado estado;

    public SistemaDePedido() {
        this.estado = Estado.NOVO;
    }

    public void processarPedido() {
        if (estado == Estado.NOVO) {
            estado = Estado.PROCESSANDO;
        }
    }

    public void concluirPedido() {
        if (estado == Estado.PROCESSANDO) {
            estado = Estado.CONCLUIDO;
        }
    }

    public Estado getEstado() {
        return estado;
    }
}
```

**Teste de Transição de Estado:**

```java
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class SistemaDePedidoTest {

    @Test
    public void testTransicaoDeEstado() {
        SistemaDePedido pedido = new SistemaDePedido();
        
        // Estado inicial
        assertEquals(SistemaDePedido.Estado.NOVO, pedido.getEstado());
        
        // Transição para PROCESSANDO
        pedido.processarPedido();
        assertEquals(SistemaDePedido.Estado

.PROCESSANDO, pedido.getEstado());

        // Transição para CONCLUÍDO
        pedido.concluirPedido();
        assertEquals(SistemaDePedido.Estado.CONCLUIDO, pedido.getEstado());
    }
}
```

---

Essas são algumas das técnicas de teste mais comuns e suas respectivas implementações em Java, com exemplos e explicações claras. Com essas abordagens, é possível testar diversos aspectos do software, desde a lógica interna até o comportamento de entradas e saídas.
