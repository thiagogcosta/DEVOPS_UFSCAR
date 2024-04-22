# EML 1.2 - Do notebook para produção

API para detecção de fraudes no cartão de crédito, esta é uma API construída com Flask utilizando algumas características inerentes a alguns clientes de um banco disponibilizada no Kaggle. Inclusive, o notebook contendo as análises e os códigos para o treinamento do modelo de Machine Learning foi confeccionado durante a disciplina de IML1. 

Além disso, as fetures que são utilizadas pelo modelo de Aprendizado de máquina são as seguintes:
* amt
* merchant_1
* merchant_2
* category
* year
* city_pop
* is_fraud (target)

Não menos importante, as features foram selecionadas conforme uma Análise de Dados prévia que está contida no notebook presente neste repositório.

## Pré-requisitos
Python 3.11 instalado no sistema. Além disso, é necessário a instalação das bibliotecas presentes no requirements.txt

## Execução local

## Execução via API
* Execute o arquivo app.py para que seja iniciado o servidor Flask:
  ```python 
  python3 app.py
  ```
* Logo após o servidor ter sido iniciado, a API estará disponível em: http://localhost:8000/predict

## Construção da imagem e execução do container
* Para construir a imagem:
  ```bash 
  docker build -t api_deteccao_fraude .
  ```
* Para executar o container:
  ```bash 
  docker run api_deteccao_fraude
  ```
* Desse modo, para que seja possível a execução da API de detecção de fraudes basta enviar requisições GET para a rota /predict com os seguintes parâmetros: amt, merchant_1, merchant_2, category, year, city_pop.

* A seguir há um exemplo utilizando o software Insonmia, no qual proporciona a execução de testes em API.

  * Exemplo de caso de fraude:

    * URL: http://172.17.0.2:8000/predict?amt=884.54&merchant_1=626&merchant_2=116&category=12&year=1983&city_pop=178
    * Imagem:
   
  * Exemplo de caso em que não é fraude:

    * URL: http://172.17.0.2:8000/predict?amt=40.31&merchant_1=567&merchant_2=75&category=2&year=1987&city_pop=12335
    * Imagem:
