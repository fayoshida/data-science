# Salários em Data Science (2019-2023)

Notebook: [Risco_de_Crédito_Nubank](https://github.com/fayoshida/data-science/blob/main/Credit_Scoring_Imbalanced/Risco_de_Credito_Nubank.ipynb)

Dados: [acquisition_train.csv](http://dl.dropboxusercontent.com/s/xn2a4kzf0zer0xu/acquisition_train.csv?dl=0)

## Objetivo
O negócio bancário tem como principal know-how a capacidade de gerenciamento de risco financeiro. O cálculo da taxa de inadimplência de um carteira de crédito desempenha papel fundamental no desempenho e planejamento de uma instituição financeira. <br><br>
O objetivo destes cálculos é identificar a probabilidade de um cliente entrar em default que é o não cumprimento de uma obrigação ou condição de um empréstimo, sendo que normalmente sua causa é a incapacidade financeira do cliente.<br><br>
Instituições pelo mundo têm incorporado o uso de modelos de machine learning para o aprimoramento de sua avaliação de risco. Neste contexto, temos uma base de dados da fintech Nubank que será utilizada para modelagem afim de predizer a probabilidade de default para seus clientes.

**Palavras-chaves:** data science, data engineering, machine learning, credit scoring, default, imbalanced dataset, sampling

# Features consideradas para treino.

* `credit_limit`: Limite de crédito.
* `external_data_provider_credit_checks_last_month`: Quantidade de checagens no bureau de crédito no último mês.
* `external_data_provider_credit_checks_last_year`: Quantidade de checagens no bureau de crédito no último ano.
* `facebook_profile`: Perfil do facebook conhecido/informado.
* `income`: Renda.
* `last_amount_borrowed`: Último valor emprestado.
* `last_borrowed_in_months`: Quantos meses do último empréstimo.
* `marketing_channel`: Canal de marketing utilizado na oferta.
* `n_bankruptcies`: quantidade de falências/defaults.
* `n_defaulted_loans`: Quantidade de empréstimos com default.
* `n_accounts`: Número de contas.
* `n_issues`: Número de solicitações de crédito.
* `reported_income`: Renda informada pelo cliente.
* `risk_rate`: proporção de risco (?)
* `score_1, score_2, score_3, score_4, score_5, score_6`: Outros scores de crédito.

## Conclusão

Na análise de correlação e valores de IV, encontramos cerca de 4 features com algum nível de relevância, `score_1, score_2, facebook_profile e risk_rate`. Avaliando a feature importance no treinamento do modelo, evidenciamos que as demais features pouco agregam nos modelos. Temos aqui a necessidade de inclusão de mais features no modelo, como por exemplo a utilização de outros produtos de crédito, tempo de atraso nos pagamentos, pagamento parcial de fatura, informações de open banking, etc.

Com relação aos problemas encontrados na amostra (desbalanceamento da variável target) foram testados dois métodos de regularização sendo eles: o UnderSampling que busca reduzir a amostra da classe majoritaria e o OverSampling que busca eequalizar a amostra da classe minoritária a majoritária. Com resultados melhores para o teino com amostra OverSampled.

Houve a tentativa de otimização dos hiperparâmetros porém não foram encontrados melhoras signficativas nos scores.

Foram obtidos resultados satisfatórios com relação ao modelo inicialmente proposto, tendo o KS e AUC aumentado consideravelmente.

* Desbalanceado - Melhor Modelo: XGBoost<br>
Recall: 7.41%

* UnderSampling - Melhor Modelo: Gradient Boosting<br>
Recall: 64.8%

* OverSampling - Melhor Modelo: Gradient Boosting<br>
Recall: 67.4%

Estudando as faixas de probabilidade geradas, podemos verificar uma grande proporção da amostra de "bons clientes" sendo marcados como "ruins", desta forma o negócio deixaria dinheiro na mesa. Foi proposto um novo ponto de corte que concede mais crédito (e consequentemente também para clientes que podem entrar em default) mas que mantém a proporção de crédito ruim ou seja mantemos o apetite de risco.

* Ponto de Corte > 0.5<br><br>
Default Predito: 41%<br>
Clientes bons com crédito negado: 30%<br>
Clientes ruins com crédito aprovado: 5%

* Ponto de Corte > 0.627<br><br>
Default Predito: 16%<br>
Clientes bons com crédito negado: 10%<br>
Clientes ruins com crédito aprovado: 10%





