# Salários em Data Science (2019-2023)

Notebook: https://tinyurl.com/y4jpk2es

Dados: https://raw.githubusercontent.com/carlosfab/escola-data-science/master/datasets/acidentes_sp_clean.csv

## Objetivo
Temos um dataset que contém dados de salário na carreira de ciência de dados e mais 11 features associadas a estes profissionais. Nosso objetivo é compreender as relações entre os diferentes atributos destes trabalhadores, especialmente no que pode definir a remuneração destes indíviduos.

**Palavras-chaves:** data science, data engineering, machine learning, salários, carreira, trabalho remoto

## Metodologia
**Análise Exploratória de Dados (PYTHON)**

# Insights sobre as features.

As varíaveis categóricas possuem concentração em determinados tipos, sendo eles:

- **Ano Base**: 2022 e 2023 representam 92% dos registros.<br>
- **Categoria**: Data Engineering, Data Science e Machine Learning somam 87% dos profissionais.<br>
- **Experiência**: 67% tem nível d experiência "senior".<br>
- **Cargos**: Os cargos mais comuns são Data Engineer, Data Scientist e Data Analyst são 66% da base.<br>
- **Contrato**: 99% possuem Full-Time.<br>
- **Porte da Cia**: 82% são médias.<br>
- **Trabalho Remoto**: Somente 5% fazem semi-presencial, 51.2% presencial e 43.9% totalmente remotos.<br>
- Com relação a **localização de empregados e empregadoras**, a maior parte (~80%) se concentram nos EUA bem como recebem em USD.<br>

A variável **target (salários em USD)** possui 22 outliers considerando o método Z-Score para detecção e apresenta o seguinte:<br>

- 22 registros com salários outliers. Menor outlier: 329500 Maior outlier: 450000 Para média 137570 e desvio padrão 63055<br>
- 3733 registros sem salários outliers. Menor salário: 5132 Maior salário: 325000 Para média 136145 e desvio padrão 60383<br>

A existência de outliers em pouca quantidade de registros não impacta a média ou variância da amostra de forma significativa, também não foram encontrados determinantes para estes salários outliers.<br>

## Conclusão
A presente análise evidencia o impacto das categorias de atuação, porte e região geográfica sobre os salários. Entendendo estes padrões, recrutadores e profissionais em busca de oportunidades podem tomar decisões mais assertivas em suas estratégias.<br>

Relacionando salário médio com as features encontramos os seguintes conclusões:

- A categoria com maior salário é Data Architecture, porém esta não possuem registros em cargos de entrada (que possuem salários menores).<br>

- Data Science apresenta os melhores salários iniciais e melhor progressão salarial no contexto global. Retirando trabalhadores da Índia da análise, temos Machine Learning como primeira opção.<br>

- Apesar de Machine Learning oferecer os melhores salários, temos menos registros de oportunidades nesta àrea. Ficam em primeiro lugar Data Engineering, seguido por Data Science.<br>

- Companhias de pequeno porte pagam salários menores nas posições iniciais, porém ultrapassam os valores de grandes empresas nas posições executivas. Pode indicar a falta dos inputs salariais de executivos deste segmento ou o alto investimento das companias em dados para estes cargos chave.<br>

- Com a emergência global de COVID-19 e suas medidas de restrição, houve um aumento na proporção de trabalhadores completamente remotos, fato este que se inverteu em 2023 com a volta aos escritórios. Com relação aos salários é importante destacar que trabalho remoto tende a reduzir os montantes recebidos mesmo em países com salários mais homogêneos.<br>

- Os EUA apresentam melhores salários, mais trabalhadores remotos e residentes em outros países. Seus residentes também recebem os maiores salários na média. Alguns países possuem salários maiores, porém podem ser entendidos como outliers dado número reduzido de registros (0.001% da amostra.)<br>



Com relação à amostra, vale ressaltar que ela possui dados concentrados em valores específicos como região geográfica, cargos, níveis de experiência o que pode indicar deficiências na coleta de dados.<br>
