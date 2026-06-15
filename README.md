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
  
https://www.kaggle.com/datasets/jayaantanaath/student-habits-vs-academic-performance


## 1- Contextualização e Hipótese
	
O tema escolhido para a realização do trabalho final foi “Hábitos de Estudantes vs Performance Acadêmica”. Com essa base de dados, visamos explorar como diferentes estilos de vida dos estudantes impactam seus resultados acadêmicos, utilizando métricas como idade, gênero, horas de sono e estudo diário, tempo de tela e se o estudante trabalha. O target da base de dados é a nota final, que varia de 0 a 100. 
	A nossa equipe tem como hipótese que os estudantes que não trabalham e dedicam maiores horas de sono e estudo diário são, consequentemente, os que terão melhor desempenho acadêmico. 

## 2- Dataset
	O dataset escolhido se chama “Students vs Academic Habits” e é disponibilizado pela plataforma “Kaggle”.

### -Origem dos Dados: os dados são sintéticos e foram criados usando bibliotecas Python com distribuições aleatórias e dependências lógicas para simular cenários da vida real.

### -Quantidade de Registros ou Amostras: 
  Para o treinamento dos modelos foi utilizado uma database com 1000 registros.

-Principais atributos ou características: idade, gênero, horas de estudo por dia, tempo de tela, horas de netflix por dia, trabalho, horas de sono e frequência.

-Variável alvo: nota da avaliação final

## -Tratamento dos dados: 
  -Árvore: 
     - Primeiro foi feita uma análise dos dados para identificar a quantidade de colunas, os tipos de dados é se possui valores nulos ou duplicados. 
      Os valores nulos foram tratados de acordo com o tipo da coluna. Nas colunas categóricas, os valores ausentes foram preenchidos com a moda (valor mais frequente). Já nas numéricas, o preenchimento seria feito com a mediana, reduzindo o impacto de valores extremos, mas a database não possuía nenhuma.
    - Em seguida, como o modelo da árvore trabalha melhor com valores numéricos, foi feita a conversão dos valores em formato de texto. Esse processo foi feito utilizando a função “pd.get_dummies”, que cria uma nova coluna para cada categoria de texto, trocando dados por 0 ou 1.
    - Após o tratamento, a coluna “exam_score” foi separada como variável alvo, representando a nota final que o modelo deveria prever. As demais colunas foram utilizadas como variáveis de entrada.
    - Por fim, os dados foram divididos em 80% para treino e 20% para teste

-RNA:
   - As variáveis numéricas e categóricas foram tratadas separadamente.
   - Depois, foi criada a coluna score_class, que transformou a nota exam_score em três categorias: Baixo, Médio e Alto, permitindo usar o modelo para classificação.
  - Em seguida, foram separadas as variáveis de entrada e saída. A coluna student_id foi removida porque era apenas um identificador. A coluna exam_score foi usada como alvo da regressão, e score_class como alvo da classificação.
   - As colunas numéricas foram tratadas com preenchimento pela mediana e padronização com StandardScaler. Já as colunas categóricas foram preenchidas com o valor mais frequente e convertidas em números com OneHotEncoder.
   - Todo esse processo foi organizado em um Pipeline, para que o pré-processamento fosse aplicado automaticamente antes do treinamento da Rede Neural.
