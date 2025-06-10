# Enunciado dos Testes para o Jogo da Cobra (Snake Game)

Este documento apresenta os testes que você deverá garantir que seu jogo da cobra passe. Cada teste corresponde a uma funcionalidade ou comportamento esperado no jogo.

---

## Testes Gerais

### 1. Testar tamanho do tabuleiro (`testBoardSize`)
**Objetivo:** Verificar se o tabuleiro foi criado com as dimensões corretas (largura e altura).

> **Dica:** Garanta que o construtor do seu jogo inicialize corretamente as variáveis de tamanho do tabuleiro.

---

### 2. Testar posição inicial da cabeça da cobra (`testSnakeHeadPosition`)
**Objetivo:** Confirmar que a cabeça da cobra inicia na posição esperada (por exemplo, x=5, y=5).

> **Dica:** Defina a posição inicial da cabeça da cobra no construtor ou método de inicialização.

---

### 3. Testar posição da comida (`testFoodPosition`)
**Objetivo:** Verificar se a comida inicia na posição correta.

> **Dica:** Inicialize a comida em uma posição fixa no início e crie um método para reposicioná-la aleatoriamente depois.

---

### 4. Testar estado do jogo (`testGameOver`)
**Objetivo:** Garantir que o jogo comece com `gameOver = false`.

> **Dica:** Inicialize a variável `gameOver` como `false` ao criar o jogo.

---

## Funções Específicas

### 5. Testar posicionamento aleatório da comida (`testPlaceFood`)
**Objetivo:** Verificar se o método `placeFood()` altera a posição da comida para uma nova posição aleatória.

> **Dica:** Use um gerador de números aleatórios para definir a nova posição da comida dentro dos limites do tabuleiro.

---

### 6. Testar movimentação da cobra (`testMove`)
**Objetivo:** Verificar se a cobra se move corretamente de acordo com a direção atual.

> **Dica:** Atualize a posição da cabeça da cobra somando a velocidade (`velocityX`, `velocityY`) à posição atual.

---

## Entrada de Teclado

### 7. Testar mudança de direção com a tecla UP (`testKeyPressedUP`)
**Objetivo:** Quando a tecla UP for pressionada, a direção da cobra deve ser para cima (velocidade Y = -1).

> **Dica:** Implemente um método que altere `velocityX` e `velocityY` conforme a tecla pressionada, evitando que a cobra volte para trás.

---

### 8. Testar mudança de direção com a tecla DOWN (`testKeyPressedDown`)
**Objetivo:** A tecla DOWN deve mudar a direção para baixo (velocidade Y = 1).

---

### 9. Testar mudança de direção com a tecla LEFT (`testKeyPressedLeft`)
**Objetivo:** A tecla LEFT deve fazer a cobra andar para a esquerda (velocidade X = -1).

---

### 10. Testar mudança de direção com a tecla RIGHT (`testKeyPressedRight`)
**Objetivo:** A tecla RIGHT deve fazer a cobra andar para a direita (velocidade X = 1).

---

## Detecção de Colisão

### 11. Testar colisão da cabeça com o corpo (`testCollisionWithBody`)
**Objetivo:** Verificar se a função de colisão detecta corretamente quando a cabeça da cobra colide com alguma parte do corpo.

> **Dica:** Faça um método que compare as coordenadas da cabeça com as coordenadas de cada segmento do corpo da cobra.





