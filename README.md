# AirBnB data analysis and price forecast

Este repositório tem a proposta de analisar e prever qual é o preço de imóveis registrados no AirBnB na região do Rio de Janeiro.

Podemos utilizar as perguntas abaixo para entender como esta modelagem é realizada:

### Como foi a definição da estratégia de modelagem?

Para definir a estratégia de modelagem, primeiro fui verificar como os dados estavam dispostos e verifiquei que todos dados estavam em formato tabular.
Diversos dados não eram numéricos, sendo alguns categoricos, textuais, links de imagens, etc. Então, fiz um tratamento (limpeza, extração de features, seleção de features) para fazer com que estes dados ficassem num formato mais simples para treinar um modelo de machine learning.

### Como foi definida a função de custo a ser utilizada?

Como modelo, escolhi utilizer o XGBoost Regressor, idealmente deveria ser feita uma comparação entre outros modelos, mas para manter o problema simples apenas um tipo de modelo foi utilizado, sua escolha se deu pelo alto desempenho de generalização do XGBoost.  No caso, como se trata de um problema de regressão (definir o preço), a função de custo foi o erro quadrático médio (MSE).

### Qual foi o critério utilizado na seleção do modelo final?

Como dito na ultima pergunta, idealmente vários modelos poderiam ser comparados. E afim de otimizar o modelo escolhido, foi feita uma Random Search para escolher bons parâmetros para XGBoost buscando otimizar o r2_score no conjunto de validação.

### Qual foi o critério utilizado para a validação do modelo?

Para validar o modelo, o conjunto de dados foi separado em treino, validação e teste. Sendo o modelo treinado com o conjunto de treinamento, otimizado com o conjunto de validação e por fim avaliado nas métricas de teste. Idealmente, poderia haver uma validação cruzada para garantir a generalização do modelo variando os dados.

### Quais evidências você possui de que seu modelo é suficientemente bom?

O modelo foi capaz de explicar por volta de 29% da variancia do preço. O que a princípio não parece uma métrica alta. Além disso, temos um erro absoluto médio de R$375, o que também parece alto. No entanto, estas métricas representam que o modelo foi capaz de realizar aprendizado a partir dos dados disponíveis, tornando o modelo viável. Diversas melhorias poderiam ser realizadas para aumentar a performance do modelo, a maioria delas está listada no decorrer do passo a passo descrito no Notebook. Sendo as principais:

- Utilizar informações textuais extrainfo features com word2vec, análise de sentimento, etc.
- Utilizar dados relativos a datas, extraindo features temporais
- Utilizar as possibilidades dentro de 'amenities'
- Fazer uma análise de correlações mais detalhada
- Fazer uso de dados diferentes, possivelmente imagens das acomodações disponíveis