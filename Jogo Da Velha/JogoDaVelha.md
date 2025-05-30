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
private String vez = "X"; // Marca quem está jogando (X ou O)
private String[][] tabuleiro = new String[3][3]; // Tabuleiro do jogo
private int jogadas = 0; // Contador de jogadas
```
`private String[][] tabuleiro = new String[3][3];`
Que tipo de array é esse?

Ele é o que chamamos de Matriz. 
Uma matriz é uma estrutura de dados usada para armazenar múltiplos valores em uma tabela com várias linhas e colunas. Você pode pensar nela como uma tabela ou uma grade, onde cada "caixa" na tabela armazena um valor.

Por exemplo, uma matriz 3x3 é como uma tabela com 3 linhas e 3 colunas, que pode ser representada assim:


![image](https://github.com/user-attachments/assets/0406dd3b-0683-418f-90b9-a2d5eca741f9)




Aqui:

A primeira linha tem os valores 1, 2 e 3.
A segunda linha tem os valores 4, 5 e 6.
A terceira linha tem os valores 7, 8 e 9.

Em programação, você acessa os elementos da matriz usando índices, que indicam a posição da linha e da coluna. Por exemplo, matriz[0][2] acessaria o valor na primeira linha e terceira coluna, que é o número 3.

Matrizes são úteis para armazenar e manipular dados que precisam de uma organização em mais de uma dimensão, como no caso do jogo da velha, onde o tabuleiro é representado por uma matriz 3x3.


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
private void marcarJogada(JButton botao, int linha, int coluna) {
        // Marca a jogada no botão e no tabuleiro
        if (tabuleiro[linha][coluna] == null) {
            tabuleiro[linha][coluna] = vez;
            botao.setText(vez); // Marca o botão com "X" ou "O"
            jogadas++; // Aumenta o contador de jogadas

            // Verifica se alguém venceu
            if (verificaVitoria()) {
                //JOptionPane.showMessageDialog(this, "Jogador " + vez + " venceu!");
                reiniciarJogo();
            } else if (jogadas == 9) {
                //JOptionPane.showMessageDialog(this, "Empate!");
                reiniciarJogo();
            } else {
                // Troca a vez entre os jogadores
               vez = vez.equals("X") ? "O" : "X";
                
               
                
                lblMensagem.setText("Vez do Jogador " + vez);
            }
        }
    }
```

### Função para Verificar o Vencedor

Esta função verifica se há um vencedor após cada jogada. Ela verifica as linhas, colunas e diagonais para ver se algum jogador preencheu toda a linha/coluna/diagonal com seu símbolo ("X" ou "O").

```java
        private boolean verificaVitoria() {
    // Inicia o método que verifica se há uma vitória no jogo da velha.

    // Verifica as linhas (horizontalmente)
    for (int i = 0; i < 3; i++) {
        // Verifica se as três casas da linha i são iguais (não nulas e iguais entre si)
        if (tabuleiro[i][0] != null && tabuleiro[i][0].equals(tabuleiro[i][1]) && tabuleiro[i][0].equals(tabuleiro[i][2]))
            // Se as três casas da linha forem iguais, retorna 'true' indicando que houve vitória
            return true;
    }

    // Verifica as colunas (verticalmente)
    for (int i = 0; i < 3; i++) {
        // Verifica se as três casas da coluna i são iguais (não nulas e iguais entre si)
        if (tabuleiro[0][i] != null && tabuleiro[0][i].equals(tabuleiro[1][i]) && tabuleiro[0][i].equals(tabuleiro[2][i]))
            // Se as três casas da coluna forem iguais, retorna 'true' indicando que houve vitória
            return true;
    }

    // Verifica a diagonal principal (do canto superior esquerdo para o canto inferior direito)
    if (tabuleiro[0][0] != null && tabuleiro[0][0].equals(tabuleiro[1][1]) && tabuleiro[0][0].equals(tabuleiro[2][2]))
        // Se as casas da diagonal principal forem iguais, retorna 'true' indicando vitória
        return true;

    // Verifica a diagonal secundária (do canto superior direito para o canto inferior esquerdo)
    if (tabuleiro[0][2] != null && tabuleiro[0][2].equals(tabuleiro[1][1]) && tabuleiro[0][2].equals(tabuleiro[2][0]))
        // Se as casas da diagonal secundária forem iguais, retorna 'true' indicando vitória
        return true;

    // Se nenhuma das condições anteriores for verdadeira, retorna 'false', indicando que não houve vitória
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

`Component:` 
É a classe base para todos os componentes de interface gráfica no Swing. Ou seja, ela representa qualquer elemento de UI, como botões, campos de texto, rótulos, etc.

`getContentPane():`

Esse método retorna o painel de conteúdo de um JFrame, que é a área onde você adiciona os componentes da interface gráfica. O JFrame é a janela principal de uma aplicação Java Swing, e o contentPane é a área do JFrane onde você organiza e exibe os componentes dentro dessa janela. Em resumo, ele é a parte visível do JFrame.

`getComponents():`

Esse método retorna um array de objetos Component, que são todos os componentes filhos do contêiner onde o método é chamado. No caso de getContentPane().getComponents(), ele retorna todos os componentes que foram adicionados ao painel de conteúdo do JFrame. Isso pode incluir botões, campos de texto, labels, etc.

`instanceof:`

O operador instanceof é usado para verificar se um objeto é uma instância de uma determinada classe. No exemplo, if (c instanceof JButton) verifica se o componente c é um botão (JButton). Se for, a ação dentro do bloco if será executada. Caso contrário, o código ignora aquele componente.



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

