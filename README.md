# Descrição do projeto

Uma empresa de telecomunicações, necessita analisar um parâmetro referente aos seus clientes. 

O parâmetro a ser analisado é o Churn, ou seja, a taxa de evasão os clientes. O objetivo do projeto é, utilizando métodos de classificação, definir se um determinado cliente, tem o potencial de permanecer ou não com a empresa.

Três modelos serão analisados, são eles:

* KNN (K_Nearest Neighbor);  
* BNB (Bernoulli Naive Byes);  
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

A segunda etapa, foi o balanceamento dos dados da classe 'Churn', referente a taxa de evasão dos clientes da empresa. Como mostra o gráfico a seguir, há aproximadamente 5000 dados com valor 0, e aproximadamente 2000 com valor 1, o que caracteriza um desbalanceio:

<div align="center">
<img src="img/origem.png" />
</div>

A técnica de balanceamento de dados utilizada foi a 'Oversampling', que consiste em realizar a criação de novas observações da classe quando há menos amostras, tendo como objetivo igualar a proporção entre as categorias. Para esse caso, a técnica SMOTE* foi escolhida.

O gráfico abaixo, mostra o balanceamento dos dados, após a aplicação da técnica SMOTE:

<div align="center">
<img src="img/origem.png" />
</div>

Por fim, a normalização dos dados foi realizada, com o método 'StandardScaler*'.

Smote*: Consiste em criar observações intermediárias entre os dados que estão próximos. Por exemplo, se minutos totais por dia são 129.1 e 146.3, então será criada uma amostra com os minutos totais por dia com 137.7. [1]

StandardScaler*: Padroniza os atributos removendo a média e escala a variância a uma unidade. Isso significa que para cada atributo, a média seria 0, e o desvio Padrão seria 1. Desta forma, os atributos são padronizadas, tornando-os mais manejáveis para os modelos de Machine Learning. [2]

# 3. Implementação dos modelos

Inicialmente, para aplicação dos três modelos analisados, os dados foram divididos, sendo 70% para treino e 30% para teste.

## 3.1 KNN - K Nearest Neighbors

O KNN tenta classificar cada amostra de um conjunto de dados avaliando sua distância em relação aos vizinhos mais próximos. Se os vizinhos mais próximos forem majoritariamente de uma classe, a amostra em questão será classificada nesta categoria. [3]

A métrica utilizada para o cálculo das distância entre os pontos, foi a distância euclidiana, cuja a fórmula é apresentada logo abaixo:

O resultado das previsões realizadas pelo modelo, são apresentadas na forma de matriz de confusão.

<div align="center">
<img src="img/origem.png" />
</div>

Conclui-se:

* A primeira linha e primeira coluna, representam os verdadeiros positivos, com 1241 sendo um valor relativamante alto;  
* A segunda coluna e primeira linha, representam os falsos negativos, com um valor de 328;  
* A segunda linha e primeira coluna, representam os falsos positivos, com um valor de 247;  
* A segunda linha e segunda coluna, representam, os verdadeiros negativos, com um valor de 1289.

## 3.2 BNB - Bernoulli Naive Bayes

Bernoulli-Naive-Bayes é um método de machine learning que usa as frequências das ocorrências em uma base de dados para prever uma variável de interesse. Seu nome vem do modelo estatístico bayesiano, que diz que o grau com que se deve acreditar em uma afirmação vai ser ligeiramente alterado por novas evidências. [4]

A fórmula probabilística utilizada pelo modelo é apresentado a seguir:

O resultado das previsões realizadas pelo modelo, são apresentadas na forma de matriz de confusão.

<div align="center">
<img src="img/origem.png" />
</div>

Conclui-se:

* Verdadeiros positivos, com valor de 1048, inferior em relação ao modelo KNN;  
* Falsos negativos, com valor de 521, superior em relação ao modelo KNN;  
* Falsos positivos, com valor de 242, inferior, porém bem próximo, ao modelo KNN;  
* Verdadeiros negativos, com valor ded 1294, levemente superior, ao modelo KNN.

## 3.3 DTC - Decision Tree Classifier

Árvores de decisão (ou árvores de classificação) são modelos de aprendizado supervisionado que representam regras de decisão baseadas nos valores dos atributos. Sua estrutura é composta por: 

• Nós internos que são rotulados com atributos;
• Folhas que são rotuladas com classes;
• Ramos que são rotulados com valores (atributos categóricos) ou com intervalos (atributos numéricos). [5]

O critério adotado para aferir a qualidade da divisão dos nós, foi a entropia, que mede a desordem dos dados.

O resultado das previsões realizadas pelo modelo, são apresentadas na forma de matriz de confusão.

<div align="center">
<img src="img/origem.png" />
</div>

Conclui-se: 

* Verdadeiros positivos, com valor 1249, superior aos dois modelos anteriores;  
* Falsos negativos, com valor de 320, inferior aos dois modelos anteriores;  
* Falsos positivos, com valor de 277, superior aos dois modelos anteriores;  
* Verdaeiros negativos, com valor de 1259, inferior aos dois modelos anteriores.


# 4. Métricas de validação


# 5. Selecionando o modelo

# 6. Conclusão

# 7. Referências

[1]

[2] https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html

[3]

[4] https://www.ibm.com/br-pt/topics/supervised-learning

[5]
