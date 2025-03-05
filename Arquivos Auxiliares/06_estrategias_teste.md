# **Estratégias de Teste**

As **estratégias de teste** são abordagens usadas para planejar, organizar e executar os testes no ciclo de vida do desenvolvimento do software. Elas determinam como e quando os testes serão realizados, com o objetivo de garantir a qualidade e robustez do sistema.

## 1. **Teste Preventivo**

### Definição:
O **Teste Preventivo** é realizado antes ou durante o desenvolvimento do software, com o objetivo de prevenir defeitos e garantir que o código atenda aos requisitos desde o início. Ele visa a identificação de problemas de forma proativa, evitando falhas no produto final.

### Objetivo:
Evitar que os defeitos se manifestem em estágios posteriores do desenvolvimento, reduzindo o custo de correção e melhorando a qualidade geral do software.

### Exemplos de Ações Preventivas:
- **Planejamento de Testes**: Criar um plano de testes detalhado antes do início do desenvolvimento.
- **Revisões de Código**: Realizar análises de código contínuas para identificar problemas logo no início.
- **Testes de Unidades**: Implementar testes unitários desde o início para verificar o comportamento de funções e métodos.
- **Automação de Testes**: Criar scripts de automação que validem funcionalidades à medida que são desenvolvidas.

### Exemplo de Uso:

1. **Planejamento de Testes**: Durante a fase de design de um sistema, a equipe de testes começa a planejar quais testes unitários e de integração serão necessários. Por exemplo, antes de implementar uma nova funcionalidade, é possível escrever os testes que validam essa funcionalidade para que, assim que o código estiver pronto, os testes possam ser executados automaticamente.

2. **Revisão de Código**: A equipe de desenvolvimento realiza revisões contínuas do código durante o processo de desenvolvimento para evitar a introdução de defeitos. Isso pode incluir a verificação de boas práticas de codificação, como o uso adequado de variáveis e a estruturação lógica do código.

---

## 2. **Teste Reativo**

### Definição:
O **Teste Reativo** ocorre após o desenvolvimento ou implementação de uma funcionalidade ou sistema. Ele é baseado na detecção de defeitos e falhas já presentes no software, sendo realizado com base nos problemas que surgem durante ou após a fase de implementação.

### Objetivo:
Identificar e corrigir defeitos após o desenvolvimento do sistema. Ele é realizado de forma mais reativa, com base em falhas ou comportamentos inesperados que são encontrados durante os testes.

### Exemplos de Ações Reativas:
- **Testes de Integração**: Testar como diferentes módulos ou componentes do sistema interagem entre si após a implementação.
- **Testes de Sistema**: Validar o sistema como um todo após a implementação de novas funcionalidades.
- **Testes de Aceitação**: Validar se o sistema atende aos requisitos do cliente ou usuário após a entrega.
- **Testes de Regressão**: Validar que mudanças no código não afetaram funcionalidades existentes.

### Exemplo de Uso:

1. **Testes de Integração**: Após a implementação de novos módulos em um sistema de e-commerce, os testes de integração são realizados para garantir que o novo código interage corretamente com o sistema existente, como o processo de pagamento e a atualização de inventário.

2. **Testes de Regressão**: Quando uma nova versão do sistema é lançada, os testes de regressão são realizados para garantir que novas funcionalidades não tenham afetado funcionalidades antigas, como o processo de login ou a navegação entre páginas.

---

### Comparação entre Estratégias:

| **Aspecto**               | **Teste Preventivo**                               | **Teste Reativo**                                 |
|---------------------------|----------------------------------------------------|---------------------------------------------------|
| **Objetivo**               | Prevenir defeitos antes que aconteçam              | Identificar defeitos após a implementação         |
| **Momento de Execução**    | Durante o planejamento e desenvolvimento inicial  | Após a implementação ou modificação do software   |
| **Custo de Correção**      | Menor, pois os defeitos são evitados               | Maior, pois defeitos são detectados mais tarde    |
| **Exemplo de Teste**       | Testes unitários, revisão de código, automação     | Testes de integração, testes de sistema, testes de aceitação |
| **Foco**                   | Garantir a qualidade desde o início                | Resolver problemas encontrados após a implementação|

---

Essas duas abordagens de teste são complementares e devem ser usadas de forma integrada para garantir um software de alta qualidade. Enquanto o **teste preventivo** ajuda a minimizar o risco de defeitos, o **teste reativo** é fundamental para corrigir problemas e garantir que o software atenda às expectativas dos usuários finais.
