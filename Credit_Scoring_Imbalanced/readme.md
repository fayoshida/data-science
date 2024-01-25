# Salários em Data Science (2019-2023)

Notebook: [Risco_de_Crédito_Nubank](https://raw.githubusercontent.com/fayoshida/data-science/main/Credit_Scoring_Imbalanced/Risco_de_Cr%C3%A9dito_Nubank.ipynb)

Dados: [acquisition_train.csv](http://dl.dropboxusercontent.com/s/xn2a4kzf0zer0xu/acquisition_train.csv?dl=0)

## Objetivo
Instituições pelo mundo têm incorporado o uso de modelos de machine learning para o aprimoramento de sua avaliação de risco. Neste contexto, temos uma base de dados da fintech Nubank que será utilizada para modelagem afim de predizer a probabilidade de default para seus clientes.

**Palavras-chaves:** data science, data engineering, machine learning, credit scoring, default, imbalanced

# Insights sobre as features.

Considerando a informação contida e sua utilidade removeremos as seguintes colunas:

*   Variáveis cadastrais/contato de clientes: <br>
`['ids', 'profile_phone_number', 'email', 'marketing_channel']`
*   Valores codificados: <br>
`['ids', 'score_1', 'score_2','reason', 'state', 'zip', 'channel', 'job_name', 'real_state']`
*   Telemetria: <br>
`['user_agent','application_time_applied', 'application_time_in_funnel']`
*   Demandam maior aprofundamento: <br>
`['ok_since','external_data_provider_email_seen_before','external_data_provider_credit_checks_last_2_year', 'external_data_provider_first_name',  'lat_lon', 'shipping_state', 'shipping_zip_code']`
* Scores sem informação sobre origem ou método de cálculo: <br>
`['risk_rate', 'score_3', 'score_4', 'score_5', 'score_6', 'external_data_provider_fraud_score']`
* Variável target para detecção de fraude: <br>
`['target_fraud]`

Teremos então as seguintes features para o treinamento do modelo:

* `last_amount_borrowed`: Último valor emprestado.
* `last_borrowed_in_months`: Quantos meses do último empréstimo.
* `credit_limit`: Limite de crédito.
* `income`: Renda.
* `reported_income`: Renda informada pelo cliente.
* `facebook_profile`: Perfil do facebook conhecido/informado.
* `n_bankruptcies`: quantidade de falências/defaults.
* `n_defaulted_loans`: Quantidade de empréstimos com default.
* `n_accounts`: Número de contas.
* `n_issues`: Número de solicitações de crédito.
* `external_data_provider_credit_checks_last_month`: Quantidade de checagens no bureau de crédito no último mês.
* `external_data_provider_credit_checks_last_year`: Quantidade de checagens no bureau de crédito no último ano.

## Conclusão
Apesar da numerosa quantidade de features disponíveis na base de dados, não foi possível obter mais informações sobre a sistemática de origem destes dados. Portanto para o treinamento do modelo temos um número reduzido de features.

Na análise correlação com a variável target, não foram identificados correlações fortes ou até mesmo medianas, ressaltando a necessidade da inclusão de mais features para treinamento. Considerando estes fatos, não foi realizado o tuning dos hiperparâmetros nem o aprofundamento das features dropadas no início do estudo.

Com relação aos problemas encontrados na amostra (desbalanceamento da variável target) foram testados dois métodos sendo eles: o UnderSampling que busca reduzir a amostra da classe majoritaria e o OverSampling que busca duplicar a amostra da classe minoritária.

Foram obtidos resultados satisfatórios com relação ao modelo inicialmente proposto, tendo o KS e AUC aumentado consideravelmente.

* Desbalanceado<br>
KS: 0.0215 - ROC AUC: 0.5108

* UnderSampling<br>
KS: 0.2486 - ROC AUC: 0.6243

* OverSampling<br>
KS: 0.2447 - ROC AUC: 0.6223
