# predicao-de-uma-serie-temporal
Realização da Ponderada: predição de uma série temporal

# 1. Introdução

&emsp;Este projeto tem como objetivo prever valores de fechamento de ações a partir de uma série temporal histórica. Foram utilizados dois métodos distintos para comparação de desempenho:

- **Prophet**: modelo estatístico para séries temporais, robusto em capturar tendência e sazonalidade.

- **LSTM (Long Short-Term Memory)**: rede neural recorrente, adequada para modelar dependências de longo prazo em dados sequenciais.


# 2. Dataset

&emsp; O Dataset do Kaggle utilizado para o desenvolvimento da atividade é o Microsoft Stock, disponível no Link: https://www.kaggle.com/datasets/vijayvvenkitesh/microsoft-stock-time-series-analysis?resource=download. 

&emsp; Além disso, o conjunto de dados contém informações de preços de uma ação ao longo do tempo:

| Coluna | Descrição               |
|--------|--------------------------|
| Date   | Data da observação       |
| Open   | Preço de abertura        |
| High   | Preço máximo no dia      |
| Low    | Preço mínimo no dia      |
| Close  | Preço de fechamento (alvo) |
| Volume | Volume negociado         |

- Total de registros: 1511

- Período: contínuo e diário

- Variável predita: Close

# 3. Modelos Desenvolvidos

**Prophet**

- Captura tendências e sazonalidades automaticamente.

- Ideal para séries temporais financeiras de longo prazo.

**LSTM**

- Rede neural profunda com memória de longo prazo.

- Capaz de capturar padrões não lineares e relações temporais complexa

## 3.1 Etapas do Projeto

**Exploração e Análise do Dataset**

- Verificação de valores nulos e consistência temporal.

- Estatísticas descritivas dos preços.

- Visualizações da série temporal de Close.

**Pré-processamento**

- Conversão da coluna Date para índice temporal.

- Normalização dos dados para LSTM.

- Divisão em conjunto de treino e teste.

**Treinamento e Validação**

- Ajuste do modelo Prophet.

- Construção e treinamento da rede LSTM.

- Previsões realizadas sobre os dados de teste.

**Avaliação com Métricas de Erro**

- RMSE (Root Mean Squared Error)

- MAE (Mean Absolute Error)

- MAPE (Mean Absolute Percentage Error)

# 4. Resultados

&emsp; A tabela a seguir indica os resultados obtidos em cada um dos modelos.

| Modelo   | RMSE  | MAE   | MAPE   |
|----------|-------|-------|--------|
| Prophet  | 14.66 | 11.89 | 6.37%  |
| LSTM     | 7.71  | 5.93  | 3.08%  |

- O LSTM superou o Prophet em todas as métricas, apresentando menor erro absoluto e percentual.

- O MAPE do LSTM (3.08%) indica que, em média, os erros de previsão ficaram próximos de 3% do valor real, o que é considerado um bom resultado em séries financeiras.

- O RMSE foi escolhido como principal métrica de comparação, pois penaliza mais fortemente grandes erros — característica importante em finanças, onde desvios grandes podem impactar significativamente as decisões


# 5. Justificativa das Métricas

- RMSE (Root Mean Squared Error): mede o erro médio em escala quadrática. É sensível a grandes erros, sendo útil para avaliar o impacto de previsões ruins em séries financeiras, onde desvios altos são críticos.

- MAE (Mean Absolute Error): representa o erro médio absoluto, fácil de interpretar na mesma escala da variável alvo. Mostra o erro típico esperado em cada previsão.

- MAPE (Mean Absolute Percentage Error): expressa o erro em termos percentuais, permitindo fácil comparação entre diferentes séries ou ativos.

&emsp;A escolha dessas métricas foi feita para equilibrar:

- Interpretação prática: MAE e MAPE ajudam a comunicar os erros em valores absolutos e percentuais.

- Sensibilidade a erros grandes: RMSE penaliza desvios elevados, relevantes em aplicações financeiras.

# 6. Conclusão

&emsp;O Prophet apresentou bom desempenho em capturar tendência, mas foi superado pela LSTM, que modelou melhor os padrões complexos da série.

&emsp; O uso combinado das métricas reforçou a robustez da avaliação.

&emsp;O LSTM é recomendado para aplicações em que alta precisão é essencial, como previsão de preços de ativos financeiros.

# 7. Próximos Passos:

- Testar arquiteturas mais profundas de LSTM e GRU.

- Avaliar o uso de features externas (indicadores técnicos).

- Explorar ensemble de modelos (Prophet + LSTM).

# 8. Referências
