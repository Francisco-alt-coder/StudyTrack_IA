# TED 03 — situação técnica e documental em 02/11/2026

**Projeto:** StudyTrack IA | **Disciplina:** Big Data e Ciências de Dados, UNIBALSAS.

## Materiais documentados

- **TED 01:** `docs/TED01.pdf`, documento original preservado em versão organizada.
- **TED 02:** `docs/TED02.pdf`, documento original preservado em versão organizada.
- **Base preparada:** `data/processed/dataset_modelagem.csv`, 145 registros e 32 colunas, incluindo 31 preditoras e `grade`.
- **Protocolo TED 03:** divisão estratificada 116/29, semente 42; 16 nominais com One-Hot e 15 ordinais preservadas, com padronização na Regressão Logística; validação cruzada de cinco partes.
- **Classificadores:** Regressão Logística, Árvore de Decisão e Random Forest. Maior F1-macro médio na validação cruzada: Random Forest, **0,227408**.
- **Teste reservado:** F1-macro **0,288095**, acurácia **0,379310** (**11/29**); matriz de confusão e relatório por classe publicados.
- **Notebook de reprodução local:** `notebooks/TED03/TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb`, com saídas de execução local.
- **Documento Técnico v3.0 acumulativo:** `docs/TED03_Documento_Tecnico_v3_Consolidado.pdf` e versão textual em Markdown.

## Limites de verificação

A execução registrada foi **local**. Não há comprovação de execução do mesmo notebook no Google Colab. A seleção técnica do Random Forest seguiu a regra de F1-macro da validação cruzada; a interpretação e a conferência acadêmica cabem aos autores.

Os resultados não evidenciam validação externa nem comprovam previsão antecipada ou implementação de um algoritmo de priorização de tarefas para o MVP.

## Publicação Git

O [Pull Request nº 1](https://github.com/Francisco-alt-coder/StudyTrack_IA/pull/1) mantém a TED 03 em branch de revisão, sem merge para `main`. O histórico das TEDs anteriores foi preservado; os PDFs dessas etapas foram apenas reorganizados em `docs/`.
