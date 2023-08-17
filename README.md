# Descrição do projeto

Uma empresa de telecomunicações, necessita analisar um parâmetro referente aos seus clientes. 

O parâmetro a ser analisado é o Churn, ou seja, a taxa de evasão os clientes. O objetivo do projeto é, utilizando métodos de classificação, definir se um determinado cliente, tem o potencial de permanecer ou não com a empresa.

Três modelos serão analisados, são eles:

* KNN (K_Nearest Neighbor);  
* BNB (Bernoulli Navier Byes);  
* DTC (Decision Tree Classifier).  

E três métricas de validação serão utilizadas:

* Accuracy Score;  
* Recall Score;  
* Precision Score.  

A partir disso, um modelo será selecionado, para definir se uma nova cliente, com o nome de Maria, irá permanecer ou não com a empresa.



# 1. Base de dados

A base de dados utilizada para esse projeto, foi obtida da plataforma Kaggle, e está disponível no link abaixo:

Kaggle: https://www.kaggle.com/datasets/mnassrib/telecom-churn-datasets?select=churn-bigml-20.csv

Essa base de dados, possui o cadastro de 7043 clientes, com os seguintes atributos:

| **Atributos** | **Descrição** |
| ------------------- | ------------------- |
| Maior 65 Anos | Se o cliente possui mais de 65 anos ou não |
| Conjuge | Se o cliente é casado(a) ou não |
| Dependentes | Se o cliente possui filhos ou pessoas dependentes |
| Meses De Contrato | Tempo de contrato em vigor |
| Telefone Fixo | Possui telefone fico ou não |
| Varias Linhas Telefonicas | Possui mais de uma linha telefonica |
| Servico De Internet | Tipo de serviço de internet contratado (Fibra, cabo, DSL) |
| Seguranca Online | Possui serviço de segurança online ou não |
| Backup Online | Possui serviço de Backup Online ou não |
| Seguro No Dispositivo | Possui contrato de seguro no dispositivo |
| Suporte Tecnico | Serviço de suport técnico |
| TV a Cabo | Serviço de TV a cabo |
| Streaming De Filmes | Serviço de Streaming |
| Tipo De Contrato | Ciclo de pagamento (mensal, semestral, anual) |
| Pagamento Online | Se o pagamento é feito de forma online ou não |
| Forma De Pagamento | Forma de pagamento do contrato |
| Conta Mensal | Valor pago mensalmente |
| Churn | Se o cliente permanece com a empresa ou não |

# 2. Tratamento de dados

A primeira etapa do processo de tratamento de dados, foi a transformação de variáveis categóricas, em binárias, para que assim fosse possível a aplicação dos modelos de Machine Learning.

A segunda etapa
