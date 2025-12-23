🌍 Climate Pulse: Global Environmental Analysis (2020-2025)

Um dashboard analítico e preditivo construído no Microsoft Power BI para monitorar indicadores críticos de mudanças climáticas globais. Este projeto transforma dados brutos de previsões climáticas em narrativas visuais de alto impacto, focando na correlação entre atividade humana (Emissões) e consequências ambientais (Nível do Mar e Temperatura).

O diferencial técnico deste projeto reside na Engenharia de Dados (ETL) rigorosa para corrigir granularidade para legibilidade de dados críticos.

📦 Tecnologias Utilizadas
Microsoft Power BI (Data Visualization & Storytelling)

Power Query / Linguagem M (ETL Avançado e Limpeza de Dados)

DAX (Data Analysis Expressions para medidas performáticas)

Modelagem Dimensional (Arquitetura Star Schema)

🦄 Features e Análises
Aqui está o que você pode explorar no Climate Pulse:

📈 Tendência de Nível do Mar: Monitoramento da aceleração média do aumento dos oceanos (mm) ao longo da linha do tempo, permitindo identificar a gravidade acumulada até 2025.

🔥 Correlação de Impacto (Scatter Plot): Uma análise estatística visual que cruza a Temperatura Média (°C) com as Emissões de CO2 (Mt). Este visual responde à pergunta: "Países mais quentes são necessariamente os maiores poluidores?"

🏆 Ranking Dinâmico de Emissões: Visualização de barras empilhadas que destaca os maiores contribuintes de CO2 globalmente, com capacidade de reordenamento dinâmico baseado em filtros de ano e continente.

⚠️ KPIs de Risco: Cartões de indicadores que calculam médias de Risco Climático e Variação YoY (Year over Year) das emissões.

Navegação Temporal: Filtros inteligentes gerados via dCalendario para drill-down por Ano, Trimestre e Mês.

🎯 Atalhos de Interação
Para extrair o máximo da ferramenta:

Cross-Filtering: Clique em um país no gráfico de barras para filtrar automaticamente a linha de tendência e ver o histórico específico daquela nação.

Tooltips (Dicas de Ferramenta): Passe o mouse sobre os pontos do gráfico de dispersão para ver os detalhes exatos de Emissão e Temperatura daquele cluster.

Análise de Tendência: Observe a linha tracejada nos gráficos temporais para entender a projeção matemática dos dados futuros.

👩🏽‍🍳 The Process (Bastidores Técnicos)
1. Engenharia de Dados (ETL com Power Query)
O dataset original apresentava desafios de granularidade, com múltiplas entradas por ano/país.

Utilizei a Linguagem M para normalizar a tabela fato (fClima), removendo colunas dimensionais redundantes.

Criei a dimensão dLocalidade através de técnicas de referência e remoção de duplicatas para garantir uma chave única, evitando erros de relacionamento "Muitos-para-Muitos".

Gerei uma tabela dCalendario via script M para garantir a continuidade temporal necessária para cálculos de Time Intelligence.

2. Modelagem (Star Schema)
Abandonei a estrutura de "tabelão" (Flat File) em favor do Esquema Estrela.

Fato: fClima (Métricas e Chaves).

Dimensões: dLocalidade (País/Continente) e dCalendario (Datas).

Relacionamentos: Garantia de cardinalidade 1:N (Um para Muitos) para performance otimizada do motor VertiPaq.

3. DAX (Inteligência de Negócio)
Fugi das colunas calculadas (que pesam no modelo) e foquei em Medidas Explícitas:

Criação de medidas base (SUM, AVERAGE) para reutilização (Measure Branching).

Uso de CALCULATE e SAMEPERIODLASTYEAR para análises de variação anual (YoY %).

Implementação de RANKX e ALL para rankings dinâmicos que respeitam ou ignoram filtros conforme a regra de negócio.


📚 O que eu aprendi
Este projeto refinou minha capacidade de tomar decisões de arquitetura de dados:

Tratamento de Granularidade: A importância vital de limpar dimensões no Power Query para evitar relacionamentos ambíguos.

Otimização DAX: O uso de Variáveis (VAR) para deixar o código mais limpo e performático, processando o cálculo apenas uma vez na memória.

Lógica de Negócio vs. Visual: Como traduzir uma pergunta complexa (Correlação Temp x CO2) em um visual simples (Gráfico de Dispersão) que qualquer usuário entende em segundos.

💭 Como pode ser melhorado?
Conectar a uma API de clima em tempo real (ex: OpenWeatherMap) para dados diários.

Adicionar uma página de Drill-through para detalhar as ações de mitigação de cada país.

Implementar parâmetros "What-If" para simular cenários: "O que acontece com o Nível do Mar se reduzirmos o CO2 em 20%?".

traffic_light: Executando o Projeto
Para visualizar o dashboard no seu ambiente local:

Clone este repositório ou baixe o arquivo .pbix.

Certifique-se de ter o Power BI Desktop instalado.

Abra o arquivo Climate_Pulse.pbix.

Caso os dados não carreguem, vá em Transformar Dados > Configurações da Fonte de Dados e aponte para o arquivo Global_Climate_Change_Data_2020_2025.csv presente na pasta /Data deste repositório.

🍿 Video / Dashboard em Ação

![CLIMA DASHBOARD](https://github.com/user-attachments/assets/8fe809e0-5a55-43cc-91f2-ced831dd4d90)
