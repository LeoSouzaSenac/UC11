# Exercício Prático: Testando a Classe Estoque com JUnit

## Objetivo
O objetivo deste exercício é praticar testes unitários em Java utilizando **JUnit**, explorando todas as anotações disponíveis, como `@Test`, `@BeforeEach`, `@AfterEach`, `@BeforeAll`, `@AfterAll` e `@Disabled`. **O objetivo aqui é criar os testes da forma mais eficiente possível.**

Ou seja, você deve decidir **quando e onde utilizar cada uma dessas anotações**, garantindo um conjunto de testes bem estruturado e eficiente.

## Passo a Passo

### 1. Criando o Projeto
- Criar um novo projeto no NetBeans (não esqueça do nome começando com letra minúscula).
- Criar uma classe chamada **Estoque.java** que gerenciará uma lista de produtos.
- Criar uma classe auxiliar **Produto.java** para representar cada produto.

### 2. Implementando a Classe Estoque
A classe Estoque deve conter os seguintes métodos:

- **adicionarProduto(String nome, int quantidade)**: Adiciona um novo produto ao estoque ou aumenta a quantidade de um produto existente.
- **removerProduto(String nome, int quantidade)**: Remove uma quantidade específica de um produto. Se a quantidade removida for maior que a disponível, deve lançar uma exceção.
- **consultarQuantidade(String nome)**: Retorna a quantidade atual de um produto no estoque.
- **produtoMaisEstocado()**: Retorna o nome do produto com maior quantidade no estoque.
- **limparEstoque()**: Remove todos os produtos do estoque.

**Dica:** Use `ArrayList` para criar o estoque. [Acesse a aula sobre ArrayLists neste link](https://github.com/LeoSouzaSenac/UC8/blob/main/Arrays.md).


### 3. Criando a Classe de Teste EstoqueTest
- Criar uma classe de teste chamada **EstoqueTest.java** no diretório adequado.
- Escrever testes para cada um dos métodos da classe Estoque.
- Utilizar as **anotações do JUnit** para verificar se os métodos funcionam corretamente.
- Explorar o uso de **exceções (throw new IllegalArgumentException)** para casos inválidos, como remover um produto que não existe ou tentar remover mais do que o disponível.

### 4. Explorando as Anotações do JUnit
Você deve decidir:
- **Quando usar `@BeforeEach` e `@AfterEach`?**
- **`@BeforeAll` e `@AfterAll` são necessários? Em quais cenários?**
- **Quais testes poderiam ser temporariamente desativados com `@Disabled`?**
- **Como garantir que exceções são lançadas corretamente?**

### 5. Executando os Testes
- Executar os testes no NetBeans e analisar os resultados.
- Se algum teste falhar, identificar e corrigir os erros na implementação.
- Refatorar os testes para torná-los mais eficientes, se necessário.

## Desafios Extras (Para Alunos Avançados)
✅ Implementar um método **reabastecerEstoque(int quantidade)** que adiciona essa quantidade a todos os produtos e criar testes para ele.  
✅ Criar um método **listarProdutos()** que retorna uma lista com os nomes de todos os produtos e escrever testes para garantir que a lista está correta após diversas operações.





