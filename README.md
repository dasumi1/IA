# Disciplina de Inteligência Artificial , Professor Munif , Unicesumar 2026
## 📚 Turma
**ESOFT7S-N-A**

## 👩‍💻 Alunas

- **Daniely Suemi Mikami**  
  RA: 23175979-2  

- **Mariana Barnabé da Silva**  
  RA: 23123538-2  

- **Nathacha Alexsandra Cardoso Calsavara**  
  RA: 23141737-2

### Acesse o Dataset por meio deste link e faça o dowload
  
https://www.kaggle.com/datasets/jayaantanaath/student-habits-vs-academic-performance


## 1. Contextualização e Hipótese

O tema escolhido para a realização do trabalho final foi **“Hábitos de Estudantes vs Performance Acadêmica”**.

Com essa base de dados, buscamos explorar como diferentes estilos de vida dos estudantes podem impactar seus resultados acadêmicos. Para isso, foram analisadas métricas como idade, gênero, horas de sono, horas de estudo diário, tempo de tela e se o estudante trabalha ou não.

A variável alvo da base de dados é a **nota final**, que varia de 0 a 100.

A hipótese da equipe é que estudantes que não trabalham e dedicam mais horas ao sono e ao estudo diário tendem a apresentar melhor desempenho acadêmico.

---

## 2. Dataset

O dataset escolhido se chama **“Students vs Academic Habits”** e está disponível na plataforma **Kaggle**.

### Origem dos Dados

Os dados são sintéticos e foram criados utilizando bibliotecas Python, com distribuições aleatórias e dependências lógicas para simular cenários próximos da vida real.

### Quantidade de Registros

Para o treinamento dos modelos, foi utilizada uma base de dados com **1000 registros**.

### Principais Atributos

Os principais atributos presentes na base são:

- Idade
- Gênero
- Horas de estudo por dia
- Tempo de tela
- Horas de Netflix por dia
- Trabalho
- Horas de sono
- Frequência

### Variável Alvo

A variável alvo utilizada foi a **nota da avaliação final**, representada pela coluna `exam_score`.

---

## Tratamento dos Dados

### Árvore de Decisão

Primeiramente, foi realizada uma análise inicial dos dados para identificar a quantidade de colunas, os tipos de dados e a existência de valores nulos ou duplicados.

Os valores nulos foram tratados de acordo com o tipo da coluna. Nas colunas categóricas, os valores ausentes foram preenchidos com a moda, ou seja, o valor mais frequente. Já nas colunas numéricas, o preenchimento seria feito com a mediana, reduzindo o impacto de valores extremos. Porém, a base de dados não possuía valores nulos nessas colunas.

Em seguida, como o modelo de Árvore de Decisão trabalha melhor com valores numéricos, foi feita a conversão dos dados em formato de texto. Esse processo foi realizado com a função `pd.get_dummies`, que cria novas colunas para cada categoria textual, representando os valores com 0 ou 1.

Após o tratamento, a coluna `exam_score` foi separada como variável alvo, representando a nota final que o modelo deveria prever. As demais colunas foram utilizadas como variáveis de entrada.

Por fim, os dados foram divididos em **80% para treino** e **20% para teste**.

---

### RNA

No modelo de Rede Neural Artificial, as variáveis numéricas e categóricas foram tratadas separadamente.

Depois, foi criada a coluna `score_class`, que transformou a nota `exam_score` em três categorias:

- Baixo
- Médio
- Alto

Essa transformação permitiu utilizar o modelo também para uma tarefa de classificação.

Em seguida, foram separadas as variáveis de entrada e saída. A coluna `student_id` foi removida, pois era apenas um identificador. A coluna `exam_score` foi utilizada como alvo da regressão, enquanto a coluna `score_class` foi utilizada como alvo da classificação.

As colunas numéricas foram tratadas com preenchimento pela mediana e padronização utilizando `StandardScaler`. Já as colunas categóricas foram preenchidas com o valor mais frequente e convertidas em números com `OneHotEncoder`.

Todo esse processo foi organizado em um `Pipeline`, fazendo com que o pré-processamento fosse aplicado automaticamente antes do treinamento da Rede Neural.

---

## 3. Modelos Obrigatórios

O trabalho foi desenvolvido utilizando dois modelos principais:

### Parte 1: Árvore de Decisão Regressora

A Árvore de Decisão Regressora foi utilizada para prever a nota final dos estudantes com base em seus hábitos e características.

### Parte 2: Rede Neural Artificial

A Rede Neural Artificial foi utilizada tanto para regressão, usando a nota final como alvo, quanto para classificação, utilizando a coluna `score_class`.

## 7. Avaliações dos Modelos

### Árvore:

#### -Métricas: MAE, MSE, RMSE e R²
MAE: 6.96
MSE: 74.64
RMSE: 8.7
R: 0.61

#### -Gráfico de dispersão comparando nota real e nota prevista:
<img width="989" height="490" alt="image" src="https://github.com/user-attachments/assets/be830d51-8f5d-47e6-af8a-23623933182c" />

#### -Importância das variáveis:
<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/bbf253ca-e3c2-4280-95b4-8ae3374a24b3" />

#### -Árvore de decisão:
<img width="1769" height="790" alt="image" src="https://github.com/user-attachments/assets/2c549e6a-a5c9-46fa-955d-03b72acf8e3a" />

### RNA

## Comparação Entre Modelos

A comparação entre os modelos foi feita usando métricas de regressão). 

Como o problema é de regressão, não existe uma “acurácia” tradicional como em problemas de classificação. Por isso, a taxa de acerto foi interpretada pelo R², que mostra o quanto o modelo conseguiu explicar os resultados reais das notas.

### RNA Regressora:
O modelo obteve MAE de 4,02, RMSE de 5,16 e R² de 0,90. 
Isso significa que a RNA teve uma taxa aproximada de acerto de 90%, pois conseguiu explicar cerca de 90% da variação das notas dos alunos. Em média, ela errou aproximadamente 4 pontos na previsão da nota final.

### Árvore de Decisão: 
Teve uma taxa aproximada de acerto de 71%. Em média, o modelo errou cerca de 6,96 pontos na previsão da nota final dos estudantes.

Comparando os dois modelos, a RNA Regressora apresentou melhor desempenho preditivo.
Além disso, a RNA também apresentou menores valores de erro. O MAE da Árvore de Decisão foi de 6,96, enquanto o da RNA foi de 4,02. Isso mostra que a RNA errou, em média, quase 3 pontos a menos que a Árvore de Decisão.





