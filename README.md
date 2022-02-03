# Vida útil remanescente (RUL)

- O objetivo deste estudo foi realizar experimentos para criar um regressor capaz de prever a vida útil de motores a partir de seus hitóricos de sensores.  Para tal, foi realizada uma análise exploratória dos dados (EDA) onde foram encontrados variáveis que não apresentavam valor para a modelagem. Como exemplo, é possível citar a falta de variância, ou seja, variáveis que possuem apenas um valor em todas as observações, e a presença de variáveis que foram preenchidas apenas com o valor NA.

- Durante a EDA, observou-se que os motores apresentavam comportamentos distintos, apesar de serem do mesmo modelo.  Em outras palavras, um mesmo sensor poderia ser importante na predição da RUL de um motor mas não ser para outro. A teoria foi provada das seguintes formas:
    1. Comparando a correlação do sensor_14 com todos os motores e realizando a correlação desse mesmo sensor mas considerando os motores separadamente. O primeiro deu uma correlação de -0.3 que é considerada fraca. Entretanto, a segunda correlação deu valores que variaram de -0.75 à 0.75.
    2. Plotando o boxplot da variável "sensor_14" de cada motor lado a lado. Mais uma vez foi notório a diferenteça entre cada um, além da presença de uma quantidade considerável de outliers.

- Os próximo passos foram a preparação dos dados, onde os mesmo foram normalizados, e a modelagem, com o algoritmo RandomForest. Este algoritmo foi escolhido porque no geral apresenta bom desempenho. Ressalta-se que foi modelos foram criados:
    1. O primeiro englobava todos os motores;
    2. O segundo apresentava apenas as observações do motor 1.

- Por fim, os modelos foram testados na base de teste. Foram estimadas a vida útil remanescente de cada observação. A vida último final foi calculada através da médica das 5 ultimas observações de cada motor. Ambos os modelos citados acima foram testados no motor 1. O primeiro que considerava todas os motores no treinamento, previu uma RUL de 172 ciclos, enquanto que o regressor que foi treinado apenas com o motor 1 previu uma RUL de 139. Como o valor real era de 112 ciclos, isso significa que o primeiro regressor teve um erro de 60 ciclos e o segundo de 27 ciclos. Podemos concluir então que a modelagem individual apresentou melhor performance.

- Como atividades futuras posso citar algumas possíveis melhorias, como, por exemplo:
    1. Trabalhar melhor a base no sentindo de explorar melhor os sensores e remover ruídos usando transformada de Fourier;
    2. Explorar melhor as semelhances e divergências entre os motores;
    3. Testar outros algoritmos de classificação e tunar seus parâmetros.
