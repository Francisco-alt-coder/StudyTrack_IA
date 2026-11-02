# STUDYTRACK IA: seleção, preparação, análise e modelagem de dados

**Documento Técnico v3.0 — versão acumulativa consolidada para conferência acadêmica**  
**Instituição:** Centro Universitário de Balsas (UNIBALSAS)  
**Curso:** Análise e Desenvolvimento de Sistemas — 2026.2  
**Disciplina:** Big Data e Ciências de Dados  
**Professor:** Alex Rogaleski Marques  
**Autores:** Caio Vinícius Lima Soares; David Rodrigues Costa; Francisco Wesley de Souza Dias; Pedro Henrique Guedes.  
**Local e data:** Balsas, MA, 02 de novembro de 2026.

> **Condição de uso:** consolidação de registros já existentes das TEDs 01, 02 e 03, para conferência da equipe. Não constitui aprovação formal pelo professor ou validação coletiva documentada. O notebook foi executado localmente; execução no Google Colab não foi comprovada. Não se alteraram os resultados já publicados. Os PDFs originais das TEDs 01 e 02 permanecem no repositório como evidências integrais das etapas anteriores.

## 1. Introdução

O StudyTrack IA propõe apoiar estudantes na organização de disciplinas, avaliações, atividades e prazos. A pesquisa em Big Data e Ciências de Dados foi estruturada em etapas cumulativas: seleção do problema e dos dados (TED 01), preparação e análise exploratória (TED 02) e modelagem e avaliação (TED 03). A classificação de notas históricas nesta etapa é **retrospectiva**, não uma previsão antecipada nem a validação do sistema de priorização de tarefas.

## 2. Problema e solução propostos

O problema do projeto é a dificuldade de conciliar disciplinas, avaliações, trabalhos e prazos. O MVP prevê cadastro e acompanhamento de disciplinas e atividades, calendário, visualização de prioridades e painel acadêmico. A análise de dados de desempenho complementa a compreensão do contexto educacional, mas não constitui o algoritmo central de prioridade do MVP.

## 3. Necessidades de dados

| Informação | Finalidade da investigação |
|---|---|
| Horas de estudo | Caracterização da dedicação acadêmica |
| Frequência às aulas | Participação acadêmica |
| Preparação para avaliações | Hábitos de organização e estudo |
| Projetos e atividades | Percepção de impacto sobre o desempenho |
| Desempenho anterior e notas | Classificação retrospectiva de `grade` |

Para validar a priorização efetiva de atividades, o MVP ainda precisará de dados próprios de tarefas: prazos, pesos, disciplinas, status e esforço previsto. A base acadêmica selecionada não contém essas variáveis operacionais.

## 4. Conjunto de dados selecionado

A TED 01 selecionou **Higher Education Students Performance Evaluation**, do UCI Machine Learning Repository, com **145 observações** e **31 atributos preditores**. O CSV de origem contém 33 colunas, incluindo `student_id` e `grade`. A versão utilizada na modelagem possui 32 colunas: as 31 preditoras e o alvo `grade`.

- **Fonte:** UCI Machine Learning Repository, DOI [10.24432/C51G82](https://doi.org/10.24432/C51G82).
- **Formato:** CSV.
- **Licença informada no material:** CC BY 4.0.
- **Base de modelagem:** `data/processed/dataset_modelagem.csv`.
- **Hash Git da base preparada verificado nos registros técnicos:** `7859d534e981355b852a520b5e745aac121f9489`.

## 5. Variáveis principais

O conjunto contempla hábitos de estudo, leitura, frequência às aulas, preparação para provas, GPA do semestre anterior, expectativa de GPA, percepção sobre projetos e características acadêmicas, pessoais e familiares. A variável-alvo `grade` apresenta **oito classes**: `0=Fail`, `1=DD`, `2=DC`, `3=CC`, `4=CB`, `5=BB`, `6=BA` e `7=AA`.

Os códigos de classes são usados como **categorias** de classificação e não como medidas contínuas.

## 6. Justificativa da base e dos atributos

A base é pública, foi utilizada nas etapas anteriores e contém variáveis relacionadas ao contexto de desempenho acadêmico. A TED 03 manteve as **31 preditoras**, conforme protocolo previamente registrado pela equipe, para comparar três técnicas sob o mesmo conjunto de atributos, sem selecionar variáveis após observar os resultados do teste. A decisão não demonstra que todas as variáveis sejam igualmente relevantes, nem substitui uma análise futura de importância de atributos. Características demográficas e socioeconômicas demandam especial cautela quanto a vieses e privacidade.

A base não tem prazo, peso nem status de tarefa, portanto não pode avaliar diretamente a qualidade das prioridades geradas pelo MVP.

## 7. Qualidade e limitações levantadas na TED 01

A etapa inicial identificou 145 observações, predomínio de variáveis categóricas e ausência de dados faltantes segundo os registros documentados. A amostra reduzida e a existência de classes raras limitam a robustez das estimativas e a generalização a outros contextos educacionais.

## 8. Limpeza e preparação dos dados da TED 02

A TED 02 inspecionou 145 linhas e 33 colunas do arquivo original, sem encontrar valores ausentes, duplicatas ou códigos fora das faixas documentadas. Não houve imputação, exclusão de linhas ou remoção automática de supostos outliers categóricos. Os nomes das colunas foram padronizados. Para a modelagem, `student_id` foi retirado do conjunto de preditoras.

| Verificação | Registro da TED 02 |
|---|---:|
| Registros | 145 |
| Valores ausentes | 0 |
| Registros duplicados | 0 |
| Identificadores únicos no original | 145 |
| Códigos fora das faixas documentadas | 0 |
| Variáveis preditoras utilizadas na TED 03 | 31 |

A ausência de tratamentos adicionais decorreu da inspeção documentada e não de exclusão automática de registros. A base original e os dados tratados permaneceram separados.

## 9. Análise exploratória de dados da TED 02

### 9.1 Distribuição da variável-alvo

| Classe | Registros | Percentual |
|---|---:|---:|
| Fail | 8 | 5,5% |
| DD | 35 | 24,1% |
| DC | 24 | 16,6% |
| CC | 21 | 14,5% |
| CB | 10 | 6,9% |
| BB | 17 | 11,7% |
| BA | 13 | 9,0% |
| AA | 17 | 11,7% |

O desbalanceamento entre classes fundamentou o uso de **F1-macro** como métrica principal: a média dá peso igual ao desempenho em cada classe, diferentemente de uma acurácia agregada.

### 9.2 Horas semanais de estudo

| Grupo | N | Média do código de `grade` |
|---|---:|---:|
| Nenhuma | 29 | 2,90 |
| Menos de 5 horas | 74 | 3,45 |
| 6 a 10 horas | 30 | 3,27 |
| 11 a 20 horas | 8 | 2,88 |
| Mais de 20 horas | 4 | 2,00 |

As médias descritivas não mostram progressão linear simples, e os grupos com maior dedicação têm poucas observações.

### 9.3 Frequência às aulas

O grupo que declarou comparecer sempre teve 110 registros e média codificada de 3,40. O grupo que comparecia às vezes teve 35 registros e média 2,69. A comparação não permite concluir causalidade.

### 9.4 Percepção sobre projetos e atividades

A percepção positiva reuniu 128 estudantes (média 3,39), a negativa reuniu quatro (média 2,25) e a neutra reuniu 13 (média 1,92). A grande diferença entre os tamanhos dos grupos limita comparações.

### 9.5 GPA do semestre anterior

| Faixa de GPA anterior | N | Média de `grade` (código) |
|---|---:|---:|
| Abaixo de 2,00 | 17 | 2,24 |
| 2,00–2,49 | 38 | 2,29 |
| 2,50–2,99 | 25 | 3,92 |
| 3,00–3,49 | 40 | 3,48 |
| Acima de 3,49 | 25 | 4,24 |

A análise da TED 02 registrou coeficientes V de Cramér aproximados de 0,262 para GPA anterior, 0,201 para percepção de projetos, 0,169 para GPA esperado, 0,144 para horas de estudo e 0,138 para frequência. Associações descritivas não demonstram causalidade nem garantem capacidade preditiva.

## 10. Relação da exploração com o problema e o MVP

A exploração dá contexto a hábitos e histórico de desempenho, mas não testa o cálculo de prioridades de tarefas. Para esse componente, seriam necessários registros de atividades com prazos, pesos, status e outras informações operacionais.

## 11. Limitações da análise exploratória

A base é pequena, representa um contexto educacional restrito, possui variáveis autorrelatadas e grupos pouco representados. Não se devem generalizar relações descritivas para outras instituições ou atribuir efeito causal sem desenho apropriado.

## 12. Síntese da TED 02

A base foi preparada sem imputar valores nem excluir registros; as colunas foram padronizadas e os identificadores foram excluídos de `X`. As diferenças observadas por histórico acadêmico, frequência e projetos fundamentaram o exame de classificação supervisionada, com cautela devido ao tamanho e composição da amostra.

## 13. Definição do problema de Machine Learning

A TED 03 investigou **classificação supervisionada multiclasse retrospectiva**, com `grade` como alvo e oito categorias preservadas. A finalidade foi verificar, por experimentos reproduzíveis, o comportamento de modelos supervisionados utilizando as variáveis da base tratada. O estudo **não** equivale a prever notas antes de todos os atributos estarem disponíveis.

## 14. Conjunto de dados, alvo e seleção de variáveis

O arquivo `data/processed/dataset_modelagem.csv` contém 145 linhas e 32 colunas: 31 preditoras e `grade`. O identificador `student_id` foi excluído. O trabalho preservou todas as 31 preditoras conforme decisão metodológica anterior, tratando seus diferentes tipos conforme a natureza codificada.

## 15. Preparação para modelagem e prevenção de vazamento

O protocolo adotado foi:

- **16 atributos nominais:** `OneHotEncoder(handle_unknown='ignore')`.
- **15 atributos ordinais:** códigos preservados como valores ordenados.
- **Regressão Logística:** `StandardScaler` sobre os ordinais.
- **Árvore de Decisão e Random Forest:** ordinais sem padronização.
- **Pipelines:** transformadores ajustados em cada partição de treinamento, sem utilizar indevidamente as observações do teste.

Essa separação permite tratamento adequado aos diferentes algoritmos e reduz riscos de vazamento do conjunto de teste durante validação.

## 16. Algoritmos, divisão e avaliação

Foram comparados `LogisticRegression(max_iter=3000)`, `DecisionTreeClassifier` e `RandomForestClassifier`, com `random_state=42` quando aplicável. A divisão estratificada 80/20 gerou **116 registros de treino** e **29 de teste reservado**. A comparação ocorreu apenas no conjunto de treino, usando `StratifiedKFold(n_splits=5, shuffle=True, random_state=42)`.

**Métrica principal:** F1-macro médio da validação cruzada. **Métrica complementar:** acurácia. O classificador com maior F1-macro médio foi selecionado por regra computacional preestabelecida antes da avaliação do teste. Essa seleção técnica não equivale a uma deliberação formal de equipe.

## 17. Resultados experimentais

### 17.1 Comparação na validação cruzada

| Classificador | F1-macro médio | Desvio-padrão F1 | Acurácia média | DP acurácia | F1 treino |
|---|---:|---:|---:|---:|---:|
| Random Forest | 0,227408 | 0,057315 | 0,311232 | 0,074522 | 1,000000 |
| Árvore de Decisão | 0,208232 | 0,071473 | 0,242391 | 0,074874 | 1,000000 |
| Regressão Logística | 0,207314 | 0,054845 | 0,276812 | 0,081405 | 0,985632 |

O **Random Forest** obteve o maior F1-macro médio nessa comparação. A diferença pequena entre os valores e a variabilidade entre as cinco partes não comprovam superioridade geral.

### 17.2 Teste final reservado

Após a seleção técnica por validação cruzada, o Random Forest foi ajustado aos 116 registros de treinamento e avaliado nos 29 reservados. Resultados da reprodução **local** já publicada:

| Métrica | Resultado |
|---|---:|
| F1-macro no teste | **0,288095** |
| Acurácia no teste | **0,379310 (37,93%)** |
| Acertos | **11 de 29** |
| Classes do alvo | 8 |

### 17.3 Matriz de confusão do teste

*Linhas = classes reais; colunas = classes previstas.*

| Real / Prevista | Fail | DD | DC | CC | CB | BB | BA | AA |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Fail | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 |
| DD | 0 | 5 | 1 | 0 | 0 | 0 | 0 | 1 |
| DC | 0 | 5 | 0 | 0 | 0 | 0 | 0 | 0 |
| CC | 0 | 2 | 0 | 2 | 0 | 0 | 0 | 0 |
| CB | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 |
| BB | 0 | 3 | 0 | 0 | 0 | 0 | 0 | 0 |
| BA | 0 | 1 | 0 | 0 | 0 | 0 | 2 | 0 |
| AA | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 2 |

### 17.4 Relatório por classe

| Classe | Precisão | Recall | F1-score | Suporte |
|---|---:|---:|---:|---:|
| Fail | 0,000 | 0,000 | 0,000 | 2 |
| DD | 0,278 | 0,714 | 0,400 | 7 |
| DC | 0,000 | 0,000 | 0,000 | 5 |
| CC | 0,667 | 0,500 | 0,571 | 4 |
| CB | 0,000 | 0,000 | 0,000 | 2 |
| BB | 0,000 | 0,000 | 0,000 | 3 |
| BA | 0,667 | 0,667 | 0,667 | 3 |
| AA | 0,667 | 0,667 | 0,667 | 3 |

**Visualizações executadas:** os gráficos de distribuição de classes, comparação de F1-macro e matriz de confusão estão nas saídas do notebook [TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb](../notebooks/TED03/TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb).

## 18. Interpretação dos resultados, erros e limitações

O teste apresentou acurácia de 37,93% e F1-macro de 0,288095. Nenhuma observação das classes **Fail, DC, CB e BB** foi corretamente classificada no teste reservado. Houve concentração de previsões em **DD**. O F1-macro próximo de 1,0 no treinamento dos modelos contrasta com resultados muito menores em validação cruzada, situação compatível com **risco de sobreajuste**.

A reduzida amostra e o número pequeno de observações por classe tornam os indicadores instáveis. Não houve validação externa ou avaliação da estabilidade em outras instituições e turmas. Esses resultados não sustentam uso para decisões individuais sobre estudantes.

## 19. Privacidade, reprodutibilidade e contribuição ao MVP

O experimento utilizou base pública. A exclusão de `student_id` entre os preditores não garante anonimização completa. Em aplicações com dados pessoais, seriam necessárias medidas compatíveis com a LGPD, com atenção a finalidade, necessidade, base legal, proteção e transparência. Informações demográficas e familiares podem refletir desigualdades; não foi executada auditoria de equidade por subgrupos.

O trabalho documenta uma **demonstração técnica de classificação retrospectiva**; não valida previsão antecipada de desempenho nem o algoritmo de priorização do StudyTrack IA. Os experimentos ajudam a identificar requisitos de dados, limites de aplicação e cuidados para uma futura avaliação do MVP.

**Rastreabilidade:** `notebooks/TED03/TED03_modelagem.ipynb` (original preservado), `notebooks/TED03/TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb` (12 células de código executadas, 17 saídas), `docs/TED03_RESULTADOS_TECNICOS_2026-11-02.md` (métricas e matriz). A execução registrada é **local**; não há comprovação de execução no Colab oficial. O Pull Request nº 1 está em rascunho, sem merge para `main`.

## 20. Conclusão da TED 03

A TED 03 deu continuidade à seleção, à preparação e à análise exploratória dos dados por meio da comparação de três classificadores multiclasse. O Random Forest liderou a validação cruzada pelo critério técnico anteriormente registrado (F1-macro médio de 0,227408). No teste reservado, obteve F1-macro de 0,288095 e acurácia de 37,93%, com 11 acertos em 29 observações. O desempenho limitado, o risco de sobreajuste, o desequilíbrio e o tamanho das classes impedem considerar o modelo pronto para aplicação operacional.

A investigação contribui para a formação metodológica e para a identificação de requisitos de dados e limitações, mas não demonstra melhoria na priorização de tarefas do MVP. Esta versão consolida evidências técnicas e deverá ter suas interpretações e sua autoria conferidas pelos integrantes antes da submissão.

## Referências e materiais de rastreabilidade

- YILMAZ, Nevriye; ŞEKEROĞLU, Boran. **Higher Education Students Performance Evaluation**. UCI Machine Learning Repository. DOI: [10.24432/C51G82](https://doi.org/10.24432/C51G82). Dados coletados em 2019, disponibilizados na UCI em 2023.
- SCIKIT-LEARN DEVELOPERS. [Cross-validation: evaluating estimator performance](https://scikit-learn.org/stable/modules/cross_validation.html). Documentação.
- STUDYTRACK IA. [Repositório e TEDs anteriores](https://github.com/Francisco-alt-coder/StudyTrack_IA). PDFs `TED_01_Big_Data_StudyTrack_IA.pdf` e `TED02_StudyTrack_.pdf`.
- STUDYTRACK IA. [Pull Request nº 1 — TED 03](https://github.com/Francisco-alt-coder/StudyTrack_IA/pull/1): notebook de reprodução local e resultados técnicos de 02/11/2026.

## Registro de uso da Inteligência Artificial

**Ferramenta:** ChatGPT (OpenAI). **Finalidade:** conferência dos arquivos públicos e dos resultados, reprodução técnica local, revisão de consistência e organização editorial do Documento Técnico v3.0. **Apoio prestado:** revisão documental, explicações de código, comparação de métricas e preparação de materiais derivados de evidências já existentes. A IA não executou o Google Colab oficial, não aprovou o trabalho pelos integrantes e não validou o desempenho do modelo em produção.

**Validação:** confronto entre matriz, acurácia e contagens, registro de execução local no notebook e conferência de arquivos e fontes. A equipe permanece responsável por revisar as interpretações, a autoria e o histórico de consultas efetivamente utilizadas.

**Privacidade:** esta consolidação usou dados públicos, sem inserção de dados pessoais sigilosos ou credenciais.
