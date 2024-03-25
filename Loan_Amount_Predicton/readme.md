# Loan Amount Prediction - Regressão

Notebook: [Loan_Amount_Prediction](https://github.com/fayoshida/data-science/blob/a6e23c5c4016fa6bff6a1949329be6eeb6235b28/Loan_Amount_Predicton/Loan_Amount_Prediction.ipynb)

## Objetivo
Modelos de Machine Learning onde se busca calcular a probabilidade de default (credit score) são abundantes e envolvem problemas de classificação. No entanto decidir o valor a ser concedido é de suma importância nesta tomada de decisão, intuitivamente tenta-se adequar o valor SOLICITADO com as métricas de risco dos clientes, aprovando, negando ou reduzindo o valor solicitado. Este projeto busca identificar as características determinantes para o valor das concessões de crédito através de regressões lineares, em modelos de árvore e ensembles.

**Palavras-chaves:** data science, data engineering, machine learning, linear regression, regressors, loan amount

## Features

 Dataset com 30.000 registros e 24 features.

- `Customer ID, Property ID` : Features de identificação do cliente e da propriedade do mesmo.
- `Loan Sanction Amount (USD)` : Feature target, valor da concessão de crédito.
- `Age` : Idade em Anos
- `Credit Score` : Score de Crédito.
- `Current Loan Expenses` : Gastos com juros, amortizações ou taxas relacionadas ao empréstimo.
- `Dependents` : Número de dependentes.
- `Expense Type 1 e Type 2` : Sem informação detalhada.
- `Gender` : Gênero, categorias Male ou Female.
- `Has Active Credit Card`: Se possui cartão de crédito.
- `Income (USD)` : Renda.
- `Income Stability (USD)` : Estabilidade da renda.
- `Location` : Tipo da localidade do cliente.
- `Loan Amount Request` : Valor da solicitação de concessão.
- `No of Defaults` : Número de defaults passados.
- `Profession`: Profissão.
- `Property Type` : Sem dados sobre significado das categorias [1,2,3,4].
- `Property Location` : Localidade do imóvel do cliente.
- `Property Price` : Preço do imóvel.
- `Type of Employment` : Categoria da ocupação do cliente.

## Conclusão

Inicialmente este projeto buscava predizer o valor das concessões de crédito com base em features que representam algumas de suas características. Ao verificarmos a variável target `Loan Sanction Amount (USD)` identificamos cerca de 1/3 da base de dados com valor zero, ou seja, concessão de crédito negada. <br>

Dados numerosos nesta categoria distorcem a regressão, onde os pesos das variáveis independentes podem não fazer sentido no cenário onde o crédito não é concedido. Incluímos portanto a feature `credito_aprovado` que é resultado de um modelo de classificação que utiliza as mesmas features para retornar se o crédito será concedido ou não. <br>

O teste do modelo de classificação retornou resultados animadores: <br>

- Acurácia: 88%
- Acurácia Balanceada: 81%
- Precisão: 86%
- Recall: 99%
- Especificidade: 63%
- F1: 92%
- ROC_AUC: 81%

Avaliando a dispersão dos erros no modelo de regressão, temos erros menos concentrados em crédito negado e também uma variância menor nas demais predições.<br>

![errors](https://github.com/fayoshida/data-science/blob/47d315eba0585842e7bcd806914e7fb5807d5feb/Loan_Amount_Predicton/residual_errors.PNG)

O modelo final de regressão possui as seguintes métricas:

 - Melhor Modelo: Gradient Boosting Regressor
 - R2: 67%
 - RMSE: 24.394,93
 - MAE: 9.007,96
 - MEDAE: 1.622,06

Como principais features temos `credito_aprovado`, `Loan Amount Request (USD)` e `Credit Score`. Confirmando a tese inicial de que os valores concedidos são diretamente relacionados ao valor solicitado, que pode sofrer redução ou mesmo negativa na concessão.


