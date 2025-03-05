### **Exercício Prático: Criação de Plano de Teste Completo para um Sistema Simples**

#### **Objetivo:**
Criar um plano de testes completo para um sistema fictício de **"Cadastro de Usuários"**, com base nos conceitos discutidos nas aulas anteriores (tipos de teste, técnicas de teste, ferramentas, etc.).

#### **Passo a Passo:**

1. **Contexto do Sistema:**
   - O sistema consiste em um **formulário de cadastro de usuários**, onde o usuário deve preencher seu nome, e-mail e senha. Após o cadastro, ele deve ser redirecionado para uma página de boas-vindas.
  


#### **Descrição do Sistema:**
O sistema de cadastro de usuários tem os seguintes campos:
1. **Nome**: Não pode ser vazio.
2. **E-mail**: Deve ter o formato correto (contendo "@" e "." após o "@").
3. **Senha**: Deve ter no mínimo 6 caracteres.


 **Criação das Classes**:
   Você deverá criar a classe `Cadastro`, que contém três métodos para validar os campos de **nome**, **e-mail** e **senha**. A classe está sem a implementação da lógica de validação, e você deve completá-la.

 **Classe `Cadastro.java`**:
   Preencha a lógica dos métodos para que eles validem os campos conforme as regras descritas acima.

   ```java
   public class Cadastro {

       // Valida o nome (não pode ser vazio)
       public boolean validarNome(String nome) {
           // Lógica de validação vai aqui
       }

       // Valida o e-mail (deve conter "@" e ".")
       public boolean validarEmail(String email) {
           // Lógica de validação vai aqui
       }

       // Valida a senha (deve ter pelo menos 6 caracteres)
       public boolean validarSenha(String senha) {
           // Lógica de validação vai aqui
       }
   }
   ```




2. **Instruções para os alunos:**
   - **Especificações do Teste:** Criar objetivos e escopo para os testes, além de listar os recursos e cronograma. (15 minutos)
     - **Objetivo:** Verificar se o sistema de cadastro está funcionando corretamente.
     - **Escopo:** Testar o cadastro com dados válidos e inválidos, verificar os campos obrigatórios e testar a resposta do sistema.
     - **Recursos:** Ferramentas de teste JUnit.
    

3. **Tipos de Teste que podem ser Incluídos:**
   - **Funcionais**: Testar se o cadastro é realizado com sucesso e se erros são mostrados quando informações inválidas são fornecidas.
   - **Não Funcionais**: Testar o tempo de resposta do sistema ao realizar o cadastro.
   - **Regressão**: Verificar se as alterações no sistema não afetam a funcionalidade de cadastro.
   - **Segurança**: Testar se o sistema protege as senhas dos usuários durante o processo de cadastro.
   - **Exploratório**: Testar cenários não previstos, como campos preenchidos de maneira inesperada (ex: nome com caracteres especiais).

4. **Técnicas de Teste:**
   - **Partição de Equivalência**: Criar grupos de entradas válidas e inválidas para o campo "e-mail".
   - **Análise de Valor Limite**: Testar com e-mails no formato correto e incorreto (com 1 caractere, 255 caracteres, etc.).
   - **Transição de Estado**: Testar o fluxo de cadastro, validando os estados do sistema (campo vazio, e-mail já cadastrado, senha fraca).
  
5. **Especificação e Relato de Teste:**
   - Criar casos de teste e resultados esperados para diferentes cenários. Exemplo:
     - **Caso de Teste 1**: Preencher o formulário com dados válidos (nome, e-mail, senha).
       - **Entrada**: "Nome: João", "E-mail: joao@email.com", "Senha: 123456"
       - **Resultado Esperado**: Cadastro realizado com sucesso, usuário redirecionado para a página de boas-vindas.
     - **Caso de Teste 2**: Preencher o formulário com um e-mail inválido.
       - **Entrada**: "Nome: Maria", "E-mail: mariaemail.com", "Senha: 123456"
       - **Resultado Esperado**: Mensagem de erro informando que o e-mail é inválido.

6. **Registros de Teste:**
   - Criar um histórico de execução para cada caso de teste, com as observações feitas durante a execução.
   - **Exemplo**:
     - **Teste 1**: Preenchimento correto dos campos.
       - **Status**: Passou.
       - **Data**: 05/03/2025
       - **Comentários**: Cadastro bem-sucedido.
   


### **Objetivo do Exercício:**
- Ajudar os alunos a consolidar os conhecimentos adquiridos sobre a criação de planos de teste.
- Aplicar práticas de documentação e relatórios de resultados de maneira clara e objetiva.
- Demonstrar a importância de testar o sistema de maneira abrangente, cobrindo diferentes tipos de teste e técnicas.

