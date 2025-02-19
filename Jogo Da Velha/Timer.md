O **Timer** em Java é uma classe que permite agendar a execução de uma ação em intervalos de tempo definidos. Ele funciona de forma assíncrona, ou seja, enquanto o **Timer** está aguardando para disparar a ação, o restante do programa continua sendo executado normalmente. 

```java

private void reiniciarJogo() {
        // Desabilita os botões durante o atraso
    for (Component c : getContentPane().getComponents()) {
        if (c instanceof JButton) {
            c.setEnabled(false);
        }
    }

    // Exibe uma mensagem que o jogo está sendo reiniciado
    lblMensagem.setText("Reiniciando...");

    // Cria um Timer que executa a reinicialização após 1 segundo (1000 ms)
    new Timer(1000, new ActionListener() {
        
        @Override
        public void actionPerformed(ActionEvent e) {
            // Reinicia o tabuleiro e a interface
            tabuleiro = new String[3][3];
            jogadas = 0;
            vez = "X";
            lblMensagem.setText("Vez do Jogador X");

            // Limpa o texto dos botões
            for (Component c : getContentPane().getComponents()) {
                if (c instanceof JButton) {
                    ((JButton) c).setText("");
                }
            }

            // Habilita os botões novamente após o atraso
            for (Component c : getContentPane().getComponents()) {
                if (c instanceof JButton) {
                    c.setEnabled(true);
                }
            }
        }
    }).start(); // Inicia o Timer
    }

```


### Como o Timer funciona neste código:

1. **Timer(1000, new ActionListener())**:
   - O primeiro parâmetro (`1000`) define o tempo de espera em milissegundos (1 segundo = 1000 ms).
   - O segundo parâmetro é um **ActionListener**, que contém o código a ser executado após o tempo determinado.
   
   Ou seja, o **Timer** vai esperar 1 segundo (1000 ms) e, em seguida, vai executar a ação dentro do método `actionPerformed`.

2. **Por que usar o ActionListener?**
   - O **ActionListener** é usado para definir o comportamento que ocorre quando o **Timer** dispara. O **Timer** sozinho não executa nada até que um **ActionListener** seja fornecido.
   - Dentro do método `actionPerformed`, você coloca o que deseja fazer depois de um certo tempo, no caso, reiniciar o tabuleiro e atualizar a interface.

### Passo a passo de como o **Timer** e o **ActionListener** funcionam:

- **Timer é criado**: O Timer é instanciado com o intervalo de tempo (1000ms) e o **ActionListener** que define o que vai acontecer quando o tempo acabar.
- **Timer espera o tempo definido (1 segundo)**: Durante esse tempo, o código fora do Timer continua funcionando normalmente.
- **ActionListener é executado**: Quando o tempo de 1 segundo passa, o método `actionPerformed` é chamado, reiniciando o jogo.

### Para resumir:
- **Timer**: Agendando um evento para ser executado após um certo tempo.
- **ActionListener**: Especificando o que deve acontecer quando o evento ocorrer (nesse caso, o reinício do jogo).

Isso é útil quando você quer adicionar um "atraso" ou esperar um tempo antes de realizar alguma ação, como reiniciar o jogo sem que o jogador precise clicar em nada.
