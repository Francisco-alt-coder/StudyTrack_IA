# StudyTrack IA — TED 03 | Resultado técnico de conferência

**Execução:** 02/11/2026. **Base:** `data/processed/dataset_modelagem.csv` (145 × 32, 31 preditoras, alvo `grade`, 8 classes). **Hash Git verificado:** `7859d534e981355b852a520b5e745aac121f9489`.

## Protocolo
Divisão treino/teste estratificada de 116/29, `random_state=42`. One-Hot Encoding em 16 variáveis nominais; 15 ordinais preservadas (padronizadas somente para Regressão Logística). Regressão Logística, Árvore de Decisão e Random Forest foram comparados com StratifiedKFold de cinco partes, F1-macro principal e acurácia complementar. Transformadores ajustados nos pipelines sem consultar teste.

## Resultados da validação cruzada (somente treinamento)
| Classificador | F1-macro médio | DP do F1 | Acurácia média | DP da acurácia | F1 no treino |
|---|---:|---:|---:|---:|---:|
| Random Forest | 0,227408 | 0,057315 | 0,311232 | 0,074522 | 1,000000 |
| Árvore de Decisão | 0,208232 | 0,071473 | 0,242391 | 0,074874 | 1,000000 |
| Regressão Logística | 0,207314 | 0,054845 | 0,276812 | 0,081405 | 0,985632 |

## Critério técnico aplicado antes do teste
O maior F1-macro médio foi o do **Random Forest**, selecionado por regra computacional previamente definida. Isso **não registra deliberação formal da equipe**. Após essa seleção, somente o Random Forest foi ajustado aos 116 registros e testado nos 29 reservados.

**Teste final:** F1-macro **0,288095**, acurácia **0,379310 (11/29)**.

## Matriz de confusão
Linhas = classe real; colunas = classe prevista.

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

## Leitura crítica
O modelo acertou 11 de 29 amostras e não acertou casos das classes Fail, DC, CB e BB. Há concentração de previsões em DD e indícios de sobreajuste (treino com F1 alto, validação baixa). A base é pequena, as classes são pouco representadas e não há demonstração de eficácia para previsão antecipada ou priorização do StudyTrack IA. Não houve validação externa ou auditoria de equidade.

## Proveniência e uso de IA
Resultados de reprodução técnica local com Python 3.13.5 / pandas 2.2.3 / NumPy 2.3.5 / scikit-learn 1.8.0. Notebook reconstruído e executado localmente sem erros; a execução no Colab oficial não foi atestada. ChatGPT apoiou a verificação, execução computacional e organização de evidências. Os estudantes devem conferir e assumir suas interpretações antes da entrega. Nenhum dado pessoal privado foi inserido.
