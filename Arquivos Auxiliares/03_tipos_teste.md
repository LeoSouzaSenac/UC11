# **Tipos de Teste**

Os testes de software são cruciais para garantir que o sistema funcione corretamente e de forma eficiente. Existem vários tipos de testes, cada um com um objetivo específico. Abaixo estão os principais tipos de teste, suas definições e exemplos práticos.

## 1. **Teste Funcional**

### Definição:
O **Teste Funcional** valida se o sistema atende aos requisitos especificados, verificando se ele realiza as funções de maneira correta.

### Características:
- Foca na funcionalidade do sistema.
- Verifica se o sistema faz o que foi especificado.
- Realizado a partir de requisitos de negócios e documentos técnicos.

### Exemplo:
Imagine um sistema de login. O teste funcional verifica se, ao fornecer um nome de usuário e senha corretos, o sistema concede acesso ao usuário.

**Classe de Login:**

```java
public class SistemaDeLogin {

    private String usuarioValido = "admin";
    private String senhaValida = "1234";

    public boolean autenticar(String usuario, String senha) {
        return usuarioValido.equals(usuario) && senhaValida.equals(senha);
    }
}
```

**Teste Funcional:**

```java
import static org.junit.Assert.assertTrue;
import static org.junit.Assert.assertFalse;
import org.junit.Test;

public class SistemaDeLoginTest {

    @Test
    public void testAutenticar() {
        SistemaDeLogin login = new SistemaDeLogin();

        // Teste funcional de login bem-sucedido
        assertTrue(login.autenticar("admin", "1234"));
        
        // Teste funcional de falha no login
        assertFalse(login.autenticar("admin", "senhaerrada"));
    }
}
```

---

## 2. **Teste Unitário**

### Definição:
O **Teste Unitário** testa unidades isoladas do código, como funções ou métodos. Ele verifica se uma pequena parte do código funciona corretamente.

### Características:
- Foca em funções ou métodos individuais.
- Realizado para garantir que cada unidade de código funcione corretamente.
- Geralmente automatizado.

**Exemplo:**

Referente ao exemplo de **Teste Unitário** dado anteriormente, onde testamos uma função que soma dois números, o código seria o mesmo para validar esse tipo de teste.

---

## 3. **Teste de Regressão**

### Definição:
O **Teste de Regressão** garante que as alterações no sistema não afetam funcionalidades existentes. Após cada modificação ou adição de recursos, o teste de regressão é executado para verificar que nada foi quebrado.

### Características:
- Foca em verificar se novas mudanças não prejudicam o funcionamento antigo.
- Muito importante após grandes atualizações de código.
- Testes automatizados são frequentemente usados.

**Exemplo:**

Após alterar a função `somar` para incluir um novo recurso de logging, o teste de regressão verificaria se a soma ainda funciona corretamente.

```java
public class Calculadora {

    public int somar(int a, int b) {
        System.out.println("Soma: " + (a + b));  // Novo recurso de logging
        return a + b;
    }
}
```

---

## 4. **Teste de Desempenho**

### Definição:
O **Teste de Desempenho** avalia a eficiência do software sob carga. Ele verifica como o sistema responde quando uma grande quantidade de dados ou usuários é processada.

### Características:
- Mede o tempo de resposta e a utilização de recursos.
- Avalia o comportamento do sistema sob diferentes condições de carga.
- Usado para identificar gargalos e áreas de melhoria.

### Exemplo:
Um teste de desempenho poderia medir o tempo de resposta de um sistema de login com diferentes quantidades de usuários simulados.

---

## 5. **Teste de Aceitação**

### Definição:
O **Teste de Aceitação** é realizado pelo usuário final para validar se o sistema atende aos requisitos do negócio. O objetivo é garantir que o software satisfaça as expectativas do cliente.

### Características:
- Validado por clientes ou usuários finais.
- Foca em verificar se o sistema resolve os problemas de negócios.
- Pode ser manual ou automatizado.

**Exemplo:**

O cliente deseja testar se o sistema de login está funcionando corretamente conforme os requisitos de acesso.

```java
public class SistemaDeLogin {

    public String autenticar(String usuario, String senha) {
        if ("admin".equals(usuario) && "1234".equals(senha)) {
            return "Login bem-sucedido!";
        } else {
            return "Usuário ou senha inválidos!";
        }
    }
}
```

**Teste de Aceitação (manual):**

1. O usuário fornece "admin" como nome de usuário e "1234" como senha.
2. O sistema deve responder com "Login bem-sucedido!".

---

## 6. **Smoke Test**

### Definição:
O **Smoke Test** é uma verificação inicial e básica para garantir que o sistema está estável o suficiente para testes mais profundos. Ele avalia as funções principais de forma rápida.

### Características:
- Teste superficial que não entra em detalhes.
- Verifica se as funcionalidades principais estão funcionando.
- Usado para garantir que o sistema não tenha falhas críticas antes de iniciar testes mais detalhados.

---

## 7. **Teste Exploratórios**

### Definição:
O **Teste Exploratórios** é realizado de forma dinâmica, sem casos de teste predefinidos. O objetivo é explorar o software em busca de falhas desconhecidas, com base no conhecimento do tester.

### Características:
- Teste não estruturado, onde o tester explora a aplicação livremente.
- O tester usa seu conhecimento do sistema para descobrir falhas.
- Não depende de scripts de teste.

---

## 8. **Teste de Confirmação**

### Definição:
O **Teste de Confirmação** reexecuta os testes que falharam anteriormente para garantir que os defeitos foram corrigidos e que o sistema continua funcionando corretamente.

### Características:
- Realizado após a correção de um defeito.
- Confirma se a falha foi realmente corrigida.
- Pode ser parte do ciclo de testes de regressão.

---

## 9. **Teste de Estresse**

### Definição:
O **Teste de Estresse** testa o sistema sob condições extremas, verificando sua capacidade de lidar com uma carga muito superior à esperada, com o objetivo de identificar os pontos de falha.

### Características:
- Avalia a resiliência do sistema sob condições extremas.
- Identifica falhas que ocorrem quando o sistema é pressionado ao máximo.
- Pode incluir alto volume de dados ou usuários simultâneos.

---

## 10. **Teste de Carga**

### Definição:
O **Teste de Carga** mede a resposta do sistema quando há um grande número de usuários simultâneos ou grandes volumes de dados sendo processados.

### Características:
- Mede a resposta do sistema sob carga contínua.
- Avalia a escalabilidade do sistema.

---

## 11. **Teste de Volume**

### Definição:
O **Teste de Volume** avalia o desempenho do sistema quando há um grande volume de dados processados. O objetivo é verificar a capacidade do sistema de lidar com grandes quantidades de informações.

### Características:
- Testa como o sistema lida com grandes volumes de dados.
- Avalia a capacidade de armazenamento e a performance.

---

## 12. **Teste de Recuperação**

### Definição:
O **Teste de Recuperação** verifica a capacidade do sistema de se recuperar após falhas, como quedas de energia ou falhas de hardware.

### Características:
- Testa a resiliência do sistema a falhas.
- Avalia se o sistema consegue se recuperar sem perda de dados.

---

## 13. **Teste de Segurança**

### Definição:
O **Teste de Segurança** verifica a proteção do sistema contra ataques, garantindo que dados sensíveis e funcionalidades do sistema estejam protegidos.

### Características:
- Foca em identificar vulnerabilidades de segurança.
- Avalia o sistema contra ameaças externas, como ataques de injeção, CSRF, XSS, etc.

---

## 14. **Teste Manual e Automatizado**

### Definição:
- **Teste Manual**: Realizado por uma pessoa, sem o uso de ferramentas automatizadas. Ele é útil para testes exploratórios e de aceitação.
- **Teste Automatizado**: Realizado com o auxílio de ferramentas e scripts, sendo ideal para testes repetitivos, como testes unitários, regressão, etc.

---

Esses são os principais **Tipos de Teste** com explicações e exemplos práticos para cada um. O objetivo de cada tipo de teste é garantir que o sistema funcione conforme o esperado, seja de forma isolada ou em conjunto com outros sistemas, e que ele possa suportar as condições do mundo real.
