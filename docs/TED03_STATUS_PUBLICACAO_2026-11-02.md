# TED 03 — situação técnica e documental em 02/11/2026

**Projeto:** StudyTrack IA | **Disciplina:** Big Data e Ciências de Dados, UNIBALSAS.

## Materiais existentes e verificados

- **Base preparada:** `data/processed/dataset_modelagem.csv`, 145 registros, 32 colunas; 31 preditoras, alvo `grade`, oito classes. Git blob `7859d534e981355b852a520b5e745aac121f9489`.
- **Protocolo:** divisão estratificada 116/29, semente 42, One-Hot para 16 nominais e 15 ordinais preservadas (com padronização na Regressão Logística); `StratifiedKFold` de cinco partes; F1-macro principal, acurácia complementar; pipelines para prevenir vazamento.
- **Comparação técnica:** Regressão Logística, Árvore de Decisão e Random Forest. Maior F1-macro médio na validação cruzada: Random Forest, **0,227408**.
- **Teste final reservado:** F1-macro **0,288095**, acurácia **0,379310**, **11/29**. Matriz de confusão e relatório por classe publicados.
- **Notebook de reprodução local:** `notebooks/TED03/TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb`, com **12 células de código executadas** e **17 saídas**, incluindo gráficos e matriz.
- **Documento Técnico v3.0 acumulativo:** publicado em `docs/TED03_Documento_Tecnico_v3_Consolidado.pdf` e `docs/TED03_Documento_Tecnico_v3_Consolidado.md`, abrangendo as etapas anteriores, protocolo, métricas, limitações e relação com o MVP.
- **Declaração de IA atualizada:** `docs/TED03_Declaracao_Uso_IA.pdf` e `docs/TED03_Declaracao_Uso_IA.md`, coerente com as 12 células do notebook publicado.
- **TEDs anteriores:** PDFs originais permanecem na raiz do repositório, sem substituição.

## Limites e condições acadêmicas

A execução disponível é **local**. Não há comprovação de execução do mesmo notebook no Google Colab oficial; o enunciado apresentado não determina o Colab como ambiente obrigatório. A documentação e o notebook foram organizados para facilitar reprodução e inspeção.

A escolha do Random Forest foi feita por regra técnica pré-definida e **não** representa, por si só, ata ou deliberação formal dos integrantes. A equipe deve validar as interpretações, a autoria, o histórico efetivo de IA e o documento a ser submetido.

O modelo apresentou desempenho limitado, especialmente nas classes Fail, DC, CB e BB. Não houve validação externa, auditoria de equidade ou aplicação no MVP. **Não é prova de previsão antecipada nem do algoritmo de priorização.**

## Publicação Git

O Pull Request [nº 1](https://github.com/Francisco-alt-coder/StudyTrack_IA/pull/1) permanece aberto em **rascunho**, sem merge na `main`. Para submissão antes de eventual merge, use diretamente [a branch da TED 03](https://github.com/Francisco-alt-coder/StudyTrack_IA/tree/ted03/revisao-final-verificavel-2026-11-02), verificando a acessibilidade e a presença da documentação consolidada.

Atualização documental realizada para corrigir referências antigas que ainda tratavam o teste e a consolidação como pendentes.
