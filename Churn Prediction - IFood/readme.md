# Salários em Data Science (2019-2023)

Notebook: [IFood - Churn](https://raw.githubusercontent.com/fayoshida/data-science/main/Churn%20Prediction%20-%20IFood/IFood_Churn.ipynb)

## Objetivo
Entender as principais características/comportamento de um cliente que podem levar a Churn (não voltar a comprar na plataforma). A solução proposta poderá ser utilizada para atuar sobre esses clientes com promoções, descontos ou melhorias na plataforma.

Como a frequência de compras dos clientes do IFood é relativamente alta, o modelo será construído usando features construídas em um período fechado de 1 mês. A métrica principal de avaliação do modelo é a AUC.

**Palavras-chaves:** data science, data engineering, machine learning, churn prediction, churn, lead time

## Features

* `media_order_lead_at_login`: Tempo de entrega do pedido a contar do login no app.
* `recencia`: Quantidade de dias desde o último pedido.
* `media_order_lag_at_login`: Tempo até realizar o pedido a contar do login no app.
* `soma_receita_1m`: Receita dos pedidos no período de 1 mês.
* `qtd_pedidos_1m`: Quantidade de pedidos no período de 1 mês.

## Conclusão
O objetivo proposto de identificar a probabilidade de churn de um cliente na plataforma foi satisfeito com o modelo proposto. Temos AUC que gira em torno de 85% ~ 90% indicando grande capacidade de diferenciação entre os grupos.

A variável `media_order_lead_at_login` foi identificada como feature com mais relevância conforme shap values do modelo, análise exploratória e correlações calculadas. Esta variável representa o tempo de entrega de um pedido apartir do login do cliente na plataforma, sendo assim diminuir o "lead time" é essencial para visitas frequentes dos clientes.

Valores extremos desta feature impactam significativamente nas chances de Churn, portanto em casos onde haja imprevistos na confecção ou entrega do pedido, um suporte ágil e eficaz se faz necessário.

As demais features do modelo estão em linha com o pressuposto, como no exemplo de `qtd_pedidos_1m` em que clientes que não fazem muitos pedidos podem ser churn no proximo período.

Sendo assim, concluímos que a experiência do cliente na plataforma pode ser explorada em duas frentes.

1. Tempo de escolha de um pedido.
2. Tempo de entrega do pedido.
