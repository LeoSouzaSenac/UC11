# **Plano de Teste**

O **Plano de Teste** é um documento essencial que descreve a estratégia, abordagem e execução dos testes para garantir que o sistema atenda aos requisitos estabelecidos e funcione corretamente. Ele é uma parte fundamental do ciclo de vida do desenvolvimento, pois ajuda a definir as expectativas e garantir que o produto final seja robusto e livre de falhas críticas.

## 1. **Especificações do Teste**

### Definição:
As **Especificações do Teste** detalham os objetivos, escopo, recursos e cronograma dos testes. Elas fornecem uma visão geral de como os testes serão realizados, quais funcionalidades ou requisitos serão testados e quais recursos (como ferramentas e equipe) estarão envolvidos.

### Objetivos:
Definir claramente o que se espera alcançar com os testes, como a validação de funcionalidades específicas, a melhoria da performance ou a garantia de segurança.

### Escopo:
Estabelecer as funcionalidades ou módulos que serão testados, bem como os que estão fora do escopo, para garantir foco e eficiência.

### Recursos:
Identificar as ferramentas, ambientes e pessoas necessárias para a execução dos testes.

### Cronograma:
Definir o tempo necessário para cada fase do teste, incluindo a preparação, execução e análise dos resultados.

### Exemplo de Especificação de Teste:
- **Objetivo**: Validar que o sistema de login está funcionando corretamente.
- **Escopo**: Testar o processo de login com diferentes combinações de usuários e senhas.
- **Recursos**: Utilização do Selenium para automação de testes e equipe de QA para análise dos resultados.
- **Cronograma**: Execução dos testes de login entre os dias 10 e 12 de março, com análise dos resultados até o dia 14 de março.

---

## 2. **Tipos de Teste no Procedimento**

### Definição:
Os **Tipos de Teste no Procedimento** descrevem as categorias de testes que serão realizados, e podem ser classificados em **funcionais** e **não funcionais**, além de serem **manuais** ou **automatizados**.

### Tipos de Teste Funcionais e Não Funcionais:
- **Funcionais**: Testam as funcionalidades do sistema, verificando se o software faz o que foi projetado para fazer.
- **Não Funcionais**: Avaliam aspectos como desempenho, segurança, usabilidade, e escalabilidade do sistema.

### Tipos de Teste Manuais e Automatizados:
- **Manuais**: Testes realizados por testers humanos, que interagem diretamente com o sistema.
- **Automatizados**: Testes executados com o auxílio de ferramentas, como o Selenium, para validar o comportamento do sistema de forma repetitiva e eficiente.

### Exemplos de Tipos de Teste:
- **Funcional**: Teste de login para verificar se um usuário pode acessar o sistema com credenciais válidas.
- **Não Funcional**: Teste de carga para garantir que o sistema suporta um número elevado de usuários simultâneos.
- **Manual**: Teste de integração onde o tester interage com o sistema para verificar se dois módulos estão funcionando corretamente juntos.
- **Automatizado**: Teste de regressão usando scripts automáticos para validar que alterações no código não afetaram funcionalidades anteriores.

---

## 3. **Especificação e Relato de Teste**

### Definição:
A **Especificação e Relato de Teste** são a documentação detalhada de como cada teste será realizado, incluindo os casos de teste, os critérios de aceitação e os resultados obtidos.

### Casos de Teste:
Cada **caso de teste** descreve um cenário específico que deve ser validado. Isso inclui a descrição do que será testado, os dados de entrada, as condições e o comportamento esperado.

### Critérios de Aceitação:
Estabelecem as condições que devem ser atendidas para que o teste seja considerado aprovado.

### Resultados:
Após a execução do teste, os resultados devem ser registrados, indicando se o teste passou ou falhou, e os motivos para o resultado.

### Exemplo de Casos de Teste:
- **Caso de Teste**: Testar o login de um usuário com credenciais corretas.
    - **Entrada**: Nome de usuário e senha válidos.
    - **Ação**: O usuário insere suas credenciais na tela de login e clica no botão de login.
    - **Resultado Esperado**: O usuário deve ser redirecionado para a página inicial.
    - **Critério de Aceitação**: O login deve ser bem-sucedido, e o usuário deve acessar a página inicial do sistema.

---

## 4. **Registros de Teste**

### Definição:
Os **Registros de Teste** são a documentação que mantém um histórico detalhado de todas as execuções de testes, incluindo os defeitos encontrados e as correções aplicadas. Eles são essenciais para análise posterior e para garantir que todas as falhas sejam tratadas adequadamente.

### Histórico de Execuções:
É importante registrar o resultado de cada execução de teste, incluindo o status (passou, falhou), a data de execução e a versão do software testado.

### Defeitos Encontrados:
Quando um defeito é identificado, ele deve ser documentado com detalhes sobre sua natureza, impacto e a área do sistema afetada.

### Correções Aplicadas:
O processo de correção dos defeitos deve ser registrado, incluindo as ações tomadas para resolver o problema e os testes adicionais realizados para garantir que a correção foi eficaz.

### Exemplo de Registro de Teste:
- **Teste de Login**:
    - **Data de Execução**: 12 de março de 2023.
    - **Resultado**: Falhou.
    - **Defeito Encontrado**: O sistema não validou a senha corretamente, mesmo com uma senha válida.
    - **Correção Aplicada**: A lógica de validação de senha foi corrigida no backend. Um novo teste foi realizado com sucesso.

---

### Comparação entre Procedimentos:

| **Aspecto**                | **Especificações do Teste**               | **Tipos de Teste no Procedimento**          | **Especificação e Relato de Teste**       | **Registros de Teste**                   |
|----------------------------|------------------------------------------|--------------------------------------------|------------------------------------------|------------------------------------------|
| **Objetivo**                | Definir o escopo e recursos do teste     | Especificar o tipo de teste a ser executado| Detalhar os casos de teste e resultados  | Manter o histórico das execuções         |
| **Foco**                    | Planejamento do teste                    | Execução de testes manuais ou automatizados| Documentação detalhada de testes         | Histórico de falhas e correções          |
| **Exemplo**                 | Objetivos, cronograma, recursos          | Testes funcionais, de carga, manuais, etc. | Caso de teste com dados de entrada e resultados| Registro de falha de login e correção    |

---

Esses itens juntos compõem um **Plano de Teste** robusto e bem estruturado, fundamental para garantir a qualidade e confiabilidade de um sistema.
