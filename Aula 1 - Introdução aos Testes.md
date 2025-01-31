# Aula 1: Introdução aos Testes de Software


## 1. Por que Testamos Software?

Imagine que você comprou um celular novo e, ao abrir a câmera, ela simplesmente não funciona. Como você se sentiria?

Testes de software servem para **evitar problemas como esse**, garantindo que os programas funcionem corretamente antes de serem entregues aos usuários.

### Benefícios dos Testes:
✅ Reduzem erros no software.  
✅ Aumentam a segurança e confiabilidade.  
✅ Economizam tempo e dinheiro a longo prazo.  
✅ Garantem que as funcionalidades atendam aos **requisitos**.

---

## 2. Conceitos Fundamentais de Testes

### 2.1 Caso de Teste
▶ Um **cenário específico** projetado para verificar se uma funcionalidade do software está funcionando corretamente.  
**Exemplo:** Testar se um usuário pode fazer login com senha correta.

### 2.2 Plano de Teste
▶ Documento que descreve **o que será testado, como e quais são os critérios de sucesso**.  
**Exemplo:** Definir que será testado o login de um sistema com diferentes credenciais.

### 2.3 Defeito, Falha e Erro
- **Defeito (Bug):** Erro no código-fonte que pode causar falhas.  
- **Falha:** Quando um defeito é executado e causa um problema no software.  
- **Erro:** Equívoco do desenvolvedor ao escrever o código.

**Exemplo:** O desenvolvedor escreveu "soma = x - y" em vez de "soma = x + y". Isso é um erro de programação (defeito). Se o programa executar esse erro e exibir um resultado incorreto, isso se torna uma falha.

### 2.4 Teste Estático vs. Teste Dinâmico
- **Teste Estático:** Revisar o código, documentação ou requisitos sem executar o programa.  
- **Teste Dinâmico:** Executar o software e verificar seu comportamento.

### 📝 **Exemplo de Teste Estático** (Sem executar o código)  
**Revisão de Código (Code Review)**  

Imagine que um desenvolvedor escreveu este código em Java:  
```java
public class Usuario {
    private String nome;
    
    public Usuario(String nome) {
        this.nome = nome;
    }
    
    public void exibirNome() {
        System.out.println(nome);
    }
}
```
🔎 **Teste Estático:** Antes mesmo de rodar o programa, outro desenvolvedor pode revisar o código e perceber que:  
- O nome do usuário pode ser `null`, pois não há validação.  
- Poderia ser adicionada uma verificação para evitar valores vazios.  

✅ **Correção sugerida no Code Review:**  
```java
public Usuario(String nome) {
    if (nome == null || nome.isEmpty()) {
        throw new IllegalArgumentException("Nome não pode ser vazio");
    }
    this.nome = nome;
}
```
Isso é um **teste estático**, pois os erros foram encontrados apenas analisando o código, sem executá-lo.

---

### 🏃 **Exemplo de Teste Dinâmico** (Executando o código)  
**Teste Unitário com JUnit**  

Agora, vamos executar um **teste dinâmico** para verificar se a soma em uma classe `Calculadora` funciona corretamente:  
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
Nesse caso, o código será **executado** e o JUnit verificará se o método `somar` retorna o valor esperado.  

🔎 Se houver um erro no código da `Calculadora`, o teste **falhará**, indicando que há um problema no comportamento do software.  

Esse é um **teste dinâmico**, pois envolve a execução do programa para verificar seu funcionamento.  

---

📌 **Resumo Rápido:**  
- ✅ **Teste Estático:** Revisão de código, análise sem executar o programa.  
- ✅ **Teste Dinâmico:** Teste unitário, execução real do código para verificar seu comportamento.  

### 2.5 Critério de Aceitação
▶ Conjunto de condições que um software precisa atender para ser aceito.

**Exemplo:** Um sistema bancário não pode permitir saques acima do saldo disponível.

---

## 3. Tipos de Artefatos de Teste
Artefatos de teste são **documentos e evidências** que ajudam a planejar, executar e relatar testes.

### Exemplos:
📌 Casos de teste escritos.  
📌 Planos de teste detalhados.  
📌 Relatórios de bugs encontrados.  
📌 Logs de execução dos testes.

---

## 4. Atividade Prática

### Dinâmica: "Encontre o Bug!"

1. **Divida a turma em grupos de 3 ou 4 alunos.**  
2. Apresente este trecho de código em Java, que tem um erro:
   
   ```java
   public class Calculadora {
       public int somar(int a, int b) {
           return a - b; // Tem um erro aqui!
       }
   }
   ```
   
3. **Pergunta para os grupos:** O que está errado nesse código?
4. Peça que os alunos expliquem como corrigir o erro.
5. Conclusão: Mostre como um pequeno erro pode levar a uma falha no sistema.

---



