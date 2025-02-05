### 📌 **Exercício Prático: Criando e Executando Testes no NetBeans**  

---

### 📌 **Passo a Passo do Exercício**  

#### 1️⃣ Criando o Projeto  
- Criar um novo projeto no NetBeans com suporte ao Gradle.  
- Criar uma classe `Calculadora.java`.  

#### 2️⃣ Implementando a Classe `Calculadora`  
Os alunos devem implementar a classe com os seguintes métodos: 
- somar
- subtrair
- multiplicar
- dividir

**Dica:** Use ```java throw new IllegalArgumentException("Divisão por zero não permitida");``` para garantir que a divisão por zero não ocorra.

---

#### 3️⃣ Criando a Classe de Teste `CalculadoraTest`  
Agora os alunos devem criar uma classe de teste dentro do diretório correto para testes e escrever os testes unitários utilizando JUnit.

---

#### 4️⃣ Executando os Testes no NetBeans  
- Rode os testes utilizando a interface de testes do NetBeans.  
- Analise os resultados e verifique se algum teste falha.  
- Caso falhem, identificar o erro e corrigir a implementação.  

---

### 📌 **Desafios Extras (Para Alunos Avançados)**  
✅ Criar um novo método `potencia(int base, int expoente)` e escrever um teste para ele.  
✅ Implementar um novo método `raizQuadrada(int numero)`, garantindo que lance exceção para números negativos.  
