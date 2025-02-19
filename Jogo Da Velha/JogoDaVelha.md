# Criando um Jogo da Velha em Java com NetBeans GUI Builder

Este guia ensina como criar um simples Jogo da Velha utilizando o **NetBeans GUI Builder**. Vamos construir o jogo do zero, e cada passo será explicado para garantir que você entenda como tudo funciona.

## Requisitos

- **NetBeans IDE**: O NetBeans é uma IDE popular para desenvolvimento em Java. A versão recomendada é a 12 ou superior.
- **Java SE**: Este projeto será desenvolvido utilizando o Java SE (Standard Edition).

## Passo 1: Criando um Novo Projeto

1. Abra o **NetBeans IDE**.
2. No menu superior, clique em **File > New Project...**.
3. Selecione **Java** na categoria e **Java Application** como tipo de projeto.
4. Dê um nome para o seu projeto (por exemplo, `JogoDaVelha`) e clique em **Finish**.

Isso criará a estrutura inicial do projeto, com uma classe principal chamada `JogoDaVelha`.

## Passo 2: Configurando a Interface Gráfica com o GUI Builder

1. **Adicionar um JFrame**:
    - No painel de projetos do NetBeans, clique com o botão direito na pasta **Source Packages**.
    - Selecione **New > JFrame Form**.
    - Dê um nome à classe (por exemplo, `TelaJogo`).

2. **Adicionando Botões para o Tabuleiro**:
    - Agora, na interface gráfica que apareceu, você verá uma tela em branco onde pode adicionar componentes.
    - No painel **Palette** (geralmente à direita), localize a categoria **Swing Controls**.
    - Arraste e solte 9 botões (`JButton`) para a tela para criar o tabuleiro do jogo da velha.
    - Organize-os em uma grade 3x3 (ou seja, 3 linhas e 3 colunas), de modo que fiquem como o tabuleiro de um jogo da velha.

3. **Renomeando os Botões**:
    - Selecione cada botão na tela e altere o texto para vazio (remova o texto padrão "Button").
    - Altere o nome de cada botão para algo como `btn00`, `btn01`, `btn02`, `btn10`, `btn11`, `btn12`, e assim por diante, para identificá-los facilmente (o número indica a linha e a coluna do botão no tabuleiro).

4. **Adicionando Rótulos e Mensagens**:
    - Adicione um `JLabel` acima do tabuleiro para exibir a mensagem de quem é a vez (por exemplo, "Vez do Jogador X").
    - Adicione também um botão `JButton` para reiniciar o jogo, que será usado ao final de cada partida.

## Passo 3: Criando a Lógica do Jogo

### Variáveis Necessárias

Na classe `TelaJogo`, você precisará de algumas variáveis para controlar o estado do jogo:

```java
private String[][] tabuleiro = new String[3][3];  // Tabuleiro 3x3
private int jogadas = 0;  // Contador de jogadas
private String vez = "X";  // Quem está jogando (X ou O)
```

### Inicializando o Jogo

Crie um método para inicializar o tabuleiro. Esse método será chamado no início do jogo e quando o jogo for reiniciado:

```java
private void inicializarJogo() {
    tabuleiro = new String[3][3];  // Reinicia o tabuleiro
    jogadas = 0;  // Reinicia o contador de jogadas
    vez = "X";  // Define que o jogador X começa
    lblMensagem.setText("Vez do Jogador X");  // Atualiza a mensagem
}
```

### Função para Atualizar o Jogo

Agora, criaremos a lógica que será executada toda vez que um botão do tabuleiro for clicado. Quando um jogador clicar em um botão, o texto do botão será atualizado com "X" ou "O", dependendo da vez do jogador, e a vez passará para o outro jogador.

```java
private void fazerJogada(JButton botao, int linha, int coluna) {
    if (botao.getText().equals("")) {  // Verifica se o botão ainda não foi clicado
        botao.setText(vez);  // Atualiza o texto do botão
        tabuleiro[linha][coluna] = vez;  // Atualiza o estado do tabuleiro
        jogadas++;  // Incrementa o contador de jogadas

        if (verificarVencedor()) {  // Verifica se alguém ganhou
            lblMensagem.setText("Jogador " + vez + " venceu!");
        } else if (jogadas == 9) {  // Verifica se o jogo empatou
            lblMensagem.setText("Empate!");
        } else {
            vez = (vez.equals("X")) ? "O" : "X";  // Alterna entre X e O
            lblMensagem.setText("Vez do Jogador " + vez);
        }
    }
}
```

### Função para Verificar o Vencedor

Esta função verifica se há um vencedor após cada jogada. Ela verifica as linhas, colunas e diagonais para ver se algum jogador preencheu toda a linha/coluna/diagonal com seu símbolo ("X" ou "O").

```java
private boolean verificarVencedor() {
    // Verifica linhas e colunas
    for (int i = 0; i < 3; i++) {
        if ((tabuleiro[i][0].equals(vez) && tabuleiro[i][1].equals(vez) && tabuleiro[i][2].equals(vez)) ||
            (tabuleiro[0][i].equals(vez) && tabuleiro[1][i].equals(vez) && tabuleiro[2][i].equals(vez))) {
            return true;
        }
    }
    // Verifica diagonais
    if ((tabuleiro[0][0].equals(vez) && tabuleiro[1][1].equals(vez) && tabuleiro[2][2].equals(vez)) ||
        (tabuleiro[0][2].equals(vez) && tabuleiro[1][1].equals(vez) && tabuleiro[2][0].equals(vez))) {
        return true;
    }
    return false;
}
```

### Função para Reiniciar o Jogo

Quando o botão de reiniciar for clicado, o tabuleiro será limpo, a contagem de jogadas será reiniciada e a vez será atribuída ao jogador X.

```java
private void reiniciarJogo() {
    // Limpa o tabuleiro e a interface
    for (Component c : getContentPane().getComponents()) {
        if (c instanceof JButton) {
            ((JButton) c).setText("");  // Limpa o texto dos botões
            ((JButton) c).setEnabled(true);  // Habilita os botões
        }
    }
    lblMensagem.setText("Vez do Jogador X");  // Exibe a mensagem
    inicializarJogo();  // Reinicia o jogo
}
```

## Passo 4: Conectando a Lógica aos Botões

Agora, conectamos os botões aos métodos. Para isso, no **NetBeans GUI Builder**, você pode usar o evento **ActionPerformed**. Para cada botão de tabuleiro, crie um método que chama `fazerJogada` e passa a linha e a coluna correspondentes ao botão:

```java
private void btn00ActionPerformed(java.awt.event.ActionEvent evt) {                                     
    fazerJogada(btn00, 0, 0);  // Passa o botão e as coordenadas
}                                    
```

Repita isso para todos os botões, ajustando as coordenadas de linha e coluna.

## Passo 5: Testando o Jogo

1. Clique com o botão direito na classe `TelaJogo` e selecione **Run File**.
2. Teste o jogo, clicando nos botões do tabuleiro. O jogo deve alternar entre os jogadores, verificar o vencedor e permitir reiniciar a partida.

