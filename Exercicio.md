### **Exercício Prático: Criação de Plano de Teste Completo para um Sistema Simples**

#### **Objetivo:**
Criar um plano de testes completo para um sistema fictício de **"Cadastro de Usuários"**, com base nos conceitos discutidos nas aulas anteriores (tipos de teste, técnicas de teste, ferramentas, etc.).

#### **Passo a Passo:**

1. **Contexto do Sistema:**
   - O sistema consiste em um **formulário de cadastro de usuários**, onde o usuário deve preencher seu nome, e-mail e senha. Após o cadastro, ele deve ser redirecionado para uma página de boas-vindas.

2. **Instruções para os alunos:**
   - **Especificações do Teste:** Criar objetivos e escopo para os testes, além de listar os recursos e cronograma. (15 minutos)
     - **Objetivo:** Verificar se o sistema de cadastro está funcionando corretamente.
     - **Escopo:** Testar o cadastro com dados válidos e inválidos, verificar os campos obrigatórios e testar a resposta do sistema.
     - **Recursos:** Ferramentas de teste como Selenium ou JUnit, um ambiente de teste (pode ser simulado em papel ou usando ferramentas online).
     - **Cronograma:** Preparar o plano em 15 minutos, com execução dos testes em 45 minutos.

3. **Tipos de Teste a Serem Incluídos:**
   - **Funcionais**: Testar se o cadastro é realizado com sucesso e se erros são mostrados quando informações inválidas são fornecidas.
   - **Não Funcionais**: Testar o tempo de resposta do sistema ao realizar o cadastro.
   - **Regressão**: Verificar se as alterações no sistema não afetam a funcionalidade de cadastro.
   - **Segurança**: Testar se o sistema protege as senhas dos usuários durante o processo de cadastro.
   - **Exploratório**: Testar cenários não previstos, como campos preenchidos de maneira inesperada (ex: nome com caracteres especiais).

4. **Técnicas de Teste:**
   - **Partição de Equivalência**: Criar grupos de entradas válidas e inválidas para o campo "e-mail".
   - **Análise de Valor Limite**: Testar com e-mails no formato correto e incorreto (com 1 caractere, 255 caracteres, etc.).
   - **Transição de Estado**: Testar o fluxo de cadastro, validando os estados do sistema (campo vazio, e-mail já cadastrado, senha fraca).
   - **Tabelas de Decisão**: Criar uma tabela de decisões para testar diferentes combinações de entrada (campo de nome vazio, senha inválida, etc.).

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
   
7. **Apresentação Final (15 minutos):**
   - Os alunos devem compartilhar seus planos de teste com a turma, explicando os tipos de teste escolhidos, as técnicas aplicadas e os critérios de aceitação.
   - Discussão sobre como os planos de teste podem ser melhorados.

### **Materiais Necessários:**
- Papel e caneta (para simular os testes)
- Computadores (se a atividade for feita com ferramentas automáticas como Selenium ou JUnit)

### **Tempo Estimado:**
- **15 minutos**: Especificação do teste (objetivos, escopo, cronograma)
- **45 minutos**: Criação dos casos de teste, aplicação de técnicas de teste e registro de resultados
- **15 minutos**: Apresentação e discussão dos planos de teste

### **Objetivo do Exercício:**
- Ajudar os alunos a consolidar os conhecimentos adquiridos sobre a criação de planos de teste.
- Aplicar práticas de documentação e relatórios de resultados de maneira clara e objetiva.
- Demonstrar a importância de testar o sistema de maneira abrangente, cobrindo diferentes tipos de teste e técnicas.

