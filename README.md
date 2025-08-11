# Previsão do preço do ouro

## Introdução
O ouro é um dos ativos mais antigos e simbólicos do sistema financeiro mundial, utilizado há milênios como meio de troca, reserva de valor e proteção contra crises econômicas. Diferente de ativos produtivos, como ações ou imóveis, seu valor está fortemente associado à percepção de escassez, à demanda industrial e, principalmente, ao seu papel como “porto seguro” em momentos de instabilidade política e financeira.
Historicamente, o ouro apresentou movimentos de preço influenciados por fatores macroeconômicos, como inflação, taxas de juros e variações cambiais. No entanto, há um debate constante sobre sua previsibilidade: seria possível estimar seus preços futuros a partir do comportamento passado, ou ele se comporta como um random walk, com variações essencialmente aleatórias?

Este estudo tem como objetivo investigar a estrutura temporal dos preços do ouro nos últimos 20 anos, avaliando:

·	A estacionariedade da série de preços.

·	A presença de autocorrelação nas variações.

·	A capacidade de modelos ARIMA simples em capturar dependências temporais.

Utilizando dados diários obtidos pela API do Yahoo Finance, foram aplicados testes estatísticos (Dickey-Fuller aumentado e Ljung-Box) e modelos ARIMA em diferentes configurações. Os resultados indicam que:

·	A série de preços, em nível, não é estacionária.

·	A série diferenciada (variações diárias) é estacionária, mas apresenta apenas uma dependência significativa de curtíssimo prazo (lag 1).

·	Modelos ARIMA(0,1,1) e ARIMA(1,1,0) capturam toda a dependência detectável, deixando resíduos compatíveis com ruído branco.

Esses achados reforçam a hipótese de que o preço do ouro segue um processo próximo a um passeio aleatório, com previsibilidade extremamente limitada no curto prazo.

## Metodologia

1. Coleta de Dados

Foram obtidos preços diários de fechamento do contrato futuro de ouro (símbolo GC=F) diretamente pela biblioteca yfinance, que acessa a API pública do Yahoo Finance.

O período considerado foi de 20 anos, cobrindo diversos ciclos econômicos, crises financeiras e eventos geopolíticos relevantes.

2. Análise Exploratória Inicial

·	Visualização da série em nível: inspeção do comportamento do preço ao longo do tempo.

·	Cálculo de estatísticas descritivas: média, desvio-padrão, assimetria e curtose.

·	Transformação em variações diárias (diff()) para avaliação da estacionariedade e possíveis padrões de retorno.

3. Teste de Estacionariedade (ADF)

Foi aplicado o Teste de Dickey-Fuller Aumentado (ADF) para verificar:

·	Hipótese nula (H₀): a série não é estacionária.

·	Hipótese alternativa (H₁): a série é estacionária.

Critério de decisão: rejeitar H₀ se o p-valor < 0.05.

Resultados:

·	Em nivel: p-valor = 0.99 (não estacionária)

·	Diferença de 1ª ordem: p-valor = 9.7 x 10^{-24} (estacionária)

A necessidade de diferenciação confirma a presença de tendência no preço do ouro, possivelmente ligada a fatores macroeconômicos como inflação, taxa de juros e dólar.

As previsões ARIMA indicam que o preço futuro segue mais estável quando modelamos as variações em vez do valor absoluto.

O desempenho similar entre os modelos sugere que o comportamento do ouro é relativamente simples no curto prazo, mas pode precisar de variáveis externas (modelos ARIMAX) para capturar influências econômicas.

