# Guia da Apresentação - BattAIHealth

## 📋 Informações Gerais
- **Duração estimada**: 15-20 minutos
- **Audiência**: Professores e colegas de Engenharia Eletrotécnica
- **Objetivo**: Apresentar o projeto final sobre estimação de parâmetros de baterias usando IA

---

## 🎯 Estrutura da Apresentação

### 1. Slide de Título
- **O que dizer**: "Bom dia/Boa tarde. Vou apresentar o meu projeto final sobre BattAIHealth - estimação de condição de baterias em aplicações automóveis e ferroviárias usando inteligência artificial."
- **Tempo**: 30 segundos

### 2. Conteúdos
- **O que dizer**: "A apresentação está estruturada desta forma..." (apontar brevemente os tópicos)
- **Tempo**: 30 segundos

---

## 📖 Secção: Introdução

### 3. Motivação
- **Pontos-chave a mencionar**:
  - "A eletrificação dos transportes cria necessidade de monitorização precisa das baterias"
  - "Três parâmetros críticos: SOC (quanto resta), SOH (estado de saúde), RUL (vida útil)"
  - "Processos químicos complexos que mudam com uso e envelhecimento"
  - "Métodos tradicionais têm limitações em condições reais"
- **Tempo**: 2 minutos

### 4. Objetivos do Trabalho
- **O que dizer**: 
  - "O objetivo principal é desenvolver métodos baseados em IA para prever estes três parâmetros simultaneamente"
  - "SOC é a energia remanescente, SOH compara capacidade atual vs original, RUL prevê ciclos até falha"
  - "As contribuições incluem comparação de redes neurais e adaptação do TimesNet"
- **Tempo**: 1.5 minutos

---

## 🔬 Secção: Fundamentos Teóricos

### 5. Conceitos Fundamentais
- **O que dizer**:
  - "SOC é calculado como carga remanescente sobre capacidade máxima"
  - "SOH compara capacidade atual com a original"
  - "Ambos são estimativas devido à complexidade química das baterias"
- **Tempo**: 1 minuto

### 6. Visualização da Degradação
- **O que dizer**: "Estas imagens mostram como os parâmetros evoluem ao longo dos ciclos de operação"
- **Tempo**: 30 segundos

### 7. Degradação e Envelhecimento
- **Pontos-chave**:
  - "Formação SEI, perda de lítio, degradação estrutural são mecanismos principais"
  - "Temperatura, profundidade de descarga e número de ciclos afetam a degradação"
- **Tempo**: 1 minuto

---

## 📚 Secção: Estado da Arte

### 8. Métodos Tradicionais
- **O que dizer**:
  - "Métodos tradicionais incluem modelos de circuito, coulomb counting e filtros de Kalman"
  - "Funcionam bem em laboratório mas têm limitações em condições reais"
- **Tempo**: 1 minuto

### 9. Métodos Baseados em IA
- **Pontos-chave**:
  - "RNNs e LSTMs melhoram a modelação temporal"
  - "Transformers e MoE são arquiteturas mais avançadas"
  - "IA captura padrões complexos e adapta-se a diferentes condições"
- **Tempo**: 1 minuto

---

## 🛠️ Secção: Desenvolvimento

### 10. Modelação MATLAB
- **O que dizer**: "Implementei também um filtro de Kalman estendido em Simulink como baseline tradicional"
- **Tempo**: 30 segundos

### 11-12. Arquiteturas Baseline
- **Pontos-chave**:
  - "Testei Transformer com mecanismos de atenção - alta precisão mas computacionalmente intensivo"
  - "MoE usa especialistas para diferentes padrões - eficiente para multi-tarefas"
- **Tempo**: 1 minuto cada

### 13. Comparação de Desempenho
- **O que dizer**: "Os resultados mostram que o Transformer conseguiu melhor desempenho com RMSE de 0.0297"
- **Tempo**: 30 segundos

### 14. Visualização dos Resultados
- **O que dizer**: "Estes gráficos mostram as previsões vs valores reais para ambos os modelos"
- **Tempo**: 30 segundos

### 15-16. Método Escolhido: TimesNet
- **Pontos-chave**:
  - "Escolhi TimesNet por ser especializado em séries temporais"
  - "Multi-periodicidade deteta vários padrões simultaneamente"
  - "Transformação 2D permite uso de CNNs em dados temporais"
  - "Captura padrões de curto prazo (ciclos) e longo prazo (degradação)"
- **Tempo**: 2 minutos total

### 17. Dataset CALCE CS2
- **O que dizer**: "Usei dataset público com ~880 ciclos por bateria, incluindo tensão, corrente, temperatura"
- **Tempo**: 30 segundos

### 18. Pré-processamento
- **O que dizer**: "Calculei SOC, SOH e RUL a partir da capacidade, segmentei em ciclos, dividi 70-15-15%"
- **Tempo**: 30 segundos

### 19-20. Otimização de Hiperparâmetros
- **Pontos-chave**:
  - "Usei Optuna e Weights & Biases para otimização"
  - "50 tentativas de 50 épocas cada, minimizando MSE de validação"
  - "Otimizei camadas, fatores de expansão, frequências"
- **Tempo**: 1 minuto

---

## 📊 Secção: Resultados

### 21. Configuração e Desempenho
- **Pontos-chave**:
  - "43 épocas de treino, 37.5M parâmetros, 140MB memória"
  - "SOC teve melhor desempenho (RMSE 0.2251), seguido de SOH e RUL"
  - "~120k amostras treino, ~5k cada para validação e teste"
- **Tempo**: 1.5 minutos

### 22. Análise de Resultados
- **O que dizer**:
  - "SOC é mais fácil pois correlaciona diretamente com medições elétricas"
  - "RUL é mais difícil por ser previsão de futuro"
  - "Modelos especializados (0.0297) superam multi-tarefa (0.5311)"
- **Tempo**: 1.5 minutos

### 23. Desafios Multi-tarefa
- **Pontos-chave**:
  - "Escalas temporais diferentes: SOC curto prazo vs SOH/RUL longo prazo"
  - "Gradientes conflitantes entre tarefas durante treino"
  - "Modelo muito grande para sistemas embebidos"
  - "Penalidade de 18x no desempenho comparado a modelos especializados"
- **Tempo**: 2 minutos

---

## 🎯 Secção: Discussão

### 24. Limitações e Direções Futuras
- **Pontos-chave**:
  - "Limitações: só testado num dataset, gap laboratório-realidade"
  - "Direções futuras: ensemble methods, transfer learning, compressão de modelos"
  - "**Lição principal**: resolver tudo simultaneamente pode não ser ideal"
- **Tempo**: 2 minutos

---

## 🎉 Finalização

### 25. Slide de Agradecimento
- **O que dizer**: "Obrigado pela atenção. Estou disponível para perguntas e discussão."
- **Tempo**: 15 segundos

---

## 💡 Dicas Gerais

### Durante a Apresentação:
- **Mantém contacto visual** com a audiência
- **Usa o ponteiro** para destacar elementos importantes
- **Fala devagar e claramente**
- **Pausa após pontos importantes**

### Possíveis Perguntas:
1. **"Porque não funcionou bem a abordagem multi-tarefa?"**
   - Resposta: Escalas temporais diferentes, gradientes conflitantes, complexidade demasiada

2. **"Como aplicarias isto na prática?"**
   - Resposta: Sistemas embebidos precisam de modelos especializados e comprimidos

3. **"Que dataset usaste e porquê?"**
   - Resposta: CALCE CS2, público, bem documentado, ~880 ciclos por bateria

4. **"Qual a contribuição principal?"**
   - Resposta: Demonstração de que especialização supera generalização neste domínio

### Timing Breakdown:
- **Introdução**: 4 minutos
- **Fundamentos**: 2.5 minutos  
- **Estado da Arte**: 2 minutos
- **Desenvolvimento**: 7 minutos
- **Resultados**: 5 minutos
- **Discussão**: 2 minutos
- **Total**: ~22 minutos (ajustar conforme necessário)

---

## 📝 Notas Finais
- **Pratica a apresentação** pelo menos 2-3 vezes
- **Cronometra cada secção** para não ultrapassar tempo
- **Prepara-te para perguntas técnicas** sobre implementação
- **Confiança é fundamental** - conheces o teu trabalho melhor que ninguém!
