# Salários em Data Science (2019-2023)

Notebook: [IFood - Churn](https://raw.githubusercontent.com/fayoshida/data-science/main/Churn%20Prediction%20-%20IFood/IFood_Churn.ipynb)

## Objetivo
Entender as principais características/comportamento de um cliente que podem levar a Churn (não voltar a comprar na plataforma). A solução proposta poderá ser utilizada para atuar sobre esses clientes com promoções, descontos ou melhorias na plataforma.

Como a frequência de compras dos clientes do IFood é relativamente alta, o modelo será construído usando features construídas em um período fechado de 1 mês. A métrica principal de avaliação do modelo é a AUC.

**Palavras-chaves:** data science, data engineering, machine learning, churn prediction, churn, lead time

## Features

* `media_order_lead_at_login`: Média mensal da diferença entre o dia de um pedido e o dia do próximo pedido.
* `media_order_lag_at_login`: Média mensal da diferença entre o dia de um pedido e o dia do pedido anterior.
* `soma_receita_1m`: Receita dos pedidos no período de 1 mês.
* `qtd_pedidos_1m`: Quantidade de pedidos no período de 1 mês.
* `media_qtd_item_normal`: Média da quantidade de itens não-promocionais.
* `media_qtd_item_promo`: Média da quantidade de itens promocionais.
* `media_credito_existente`: Média do valor total de desconto no pedido.

## Conclusão
O objetivo proposto de identificar a probabilidade de churn de um cliente na plataforma foi satisfeito com o modelo proposto. Temos AUC que gira em torno de 80% ~ 90% indicando grande capacidade de diferenciação entre os grupos.

A variável `media_order_lead_at_login` foi identificada como feature com mais relevância conforme shap values do modelo, análise exploratória e correlações calculadas. Esta variável representa a quantidade de dias entre os pedidos.

Valores extremos desta feature impactam significativamente nas chances de Churn, portanto manter o cliente utilizando o app ou seja com promoções, cupons e notificações podem ser estratégias benéficas.

Como esperado de `qtd_pedidos_1m`, clientes com mais pedidos podem retornar e clientes que não fazem muitos pedidos podem ser churn no proximo período. Talvez uma estratégia de cupons ou descontos pode encorajar o cliente a realizar mais pedidos.

`soma_receita_1m` indica que clientes que gastam mais tem menores probabilidade de Churn do que clientes que gastam valores mais elevados, que está em linha com a tendência de Churn estar atrelado a capacidade financeira dos clientes.

O presente projeto buscou explorar as características de comportamento dos clientes visando a probabilidade de Churn. As features mais significativas foram exatamente relacionadas a realização dos pedidos, portanto há alta correlação entre clientes que pedem muito e vão voltar a pedir. Para estudos futuros seria interessante integrar modelos de segmentação de clientes para a predição.
