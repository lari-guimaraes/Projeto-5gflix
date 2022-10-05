# Projeto-5gflix
Projeto elaborado para o desafio técnico para a vaga de Data Engineer da e-core

O objetivo desse projeto é oferecer uma solução para a equipe de BI, que tem como atividade realizar um estudo do mercado das suas principais concorrentes, sendo elas Amazon e Netflix. 
O projeto apresenta todo o fluxo de ETL realizando na estrutura Google Cloud Platform. Para o processamento foi utilizado a ferramenta Dataproc, para os fluxos de trabalho o Dataflow e como Datawarehouse o Bigquery. A imagem abaixo apresenta a estrutura proposta. 

![image](https://user-images.githubusercontent.com/90985564/194126783-1a0bc3f2-bfee-4a27-98c1-294624b54091.png)


Os dados para este projetos foram disponibilizados publicamente, estão disponiveis no link abaixo:

Netflix - https://www.kaggle.com/netflix-inc/netflix-prize-data

Amazon - https://s3.amazonaws.com/amazon-reviews-pds/readme.html

## **Extração**

No processo de extração dos dados foi realizado um scrap, os dados foram extraidos e armazenados em um datalake no cloud storage.

## **Tratamento**
A etapa de processamento dos dados foi realizado em um cluster SPARK no google Dataproc. Já para o tratamento foi realizado com Pyspark, aplicando os seguintes tratamentos:

- Eliminação de colunas que não agregam valor ao objetivo do projeto
- Tratamento da coluna de títulos, removendo espaços,caracters inválidos.
- União dos datasets
- Transformação para o formato Parket (o objetivo é aumentar o poder de processamento, visto que este formato irá reduzir o "tamanho" dos datasets)

A imagem abaixo apresenta o diagrama lógico para o processmaneto dos dados de acordo com as etapas aqui descritas.

![image](https://user-images.githubusercontent.com/90985564/194124914-ad5e78ea-b282-436d-a8eb-0e54fd253919.png)

Por fim, foi realizado querys para responder as seguintes questões:

    Quantos filmes estão disponíveis na Amazon?

    Quantos filmes estão disponíveis na Netflix?

    Dos filmes disponíveis na Amazon, quantos % estão disponíveis na Netflix?

    O quão perto a médias das notas dos filmes disponíveis na Amazon está dos filmes disponíveis na Netflix?

    Qual ano de lançamento possui mais filmes na Amazon?

    Qual ano de lançamento possui mais filmes na Netflix?

    Quais filmes que não estão disponíveis no catálogo da Netflix foram melhor avaliados (notas 4 e 5)?

    Quais filmes que não estão disponíveis no catálogo da Amazon foram melhor avaliados (notas 4 e 5)?
