# TED 03 — Situação técnica e documental em 02/11/2026

**Projeto:** StudyTrack IA  
**Disciplina:** Big Data e Ciência de Dados, UNIBALSAS.

## Arquivos publicados na branch principal (`main`)

- **TED 01:** `docs/TED01.pdf`, preservada.
- **TED 02:** `docs/TED02.pdf`, preservada.
- **TED 03:** `docs/TED03.pdf`, Documento Técnico final de 21 páginas.
- **Documento Técnico v3.0 acumulativo em versão complementar:** `docs/TED03_Documento_Tecnico_v3_Consolidado.pdf` e arquivo `.md` correspondente.
- **Declaração de Uso de IA:** `docs/Declaracao_Uso_IA_TED03.md` (transcrição do documento fornecido pelos autores) e `docs/Declaracao_Uso_IA_TED03.pdf` (PDF de cinco páginas gerado da transcrição). **O PDF original de seis páginas anexado à conversa não foi substituído nem enviado em seus bytes originais; a versão publicada é uma reprodução textual sem as imagens do modelo institucional.**
- **Base de dados:** `data/processed/dataset_modelagem.csv`, 145 registros e 32 colunas (31 preditoras e alvo `grade`).
- **Notebook de modelagem:** `notebooks/TED03/TED03_modelagem.ipynb`.
- **Reprodução executada:** `notebooks/TED03/TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb`, com saídas da execução local.
- **Métricas e matriz de confusão:** `docs/TED03_RESULTADOS_TECNICOS_2026-11-02.md`.
- **README:** orientações para localizar e executar os materiais.

## Síntese da avaliação de Machine Learning

- **Divisão:** 116 registros para treino e 29 para teste, estratificada; semente 42.
- **Pré-processamento:** 16 atributos nominais com One-Hot Encoding, 15 ordinais preservados e padronização na Regressão Logística.
- **Modelos comparados:** Regressão Logística, Árvore de Decisão e Random Forest.
- **Validação cruzada:** cinco partes, com F1-macro como métrica principal.
- **Maior F1-macro médio na validação cruzada:** Random Forest, 0,227408.
- **Teste reservado:** F1-macro 0,288095, acurácia 0,379310 (11 acertos em 29 casos).
- **Análises publicadas:** matriz de confusão, relatório por classe, limitações e riscos de generalização.

## Estado de publicação

O [Pull Request nº 1](https://github.com/Francisco-alt-coder/StudyTrack_IA/pull/1) foi **incorporado à `main` em 02/11/2026**. A declaração textual e a reprodução em PDF foram acrescentadas diretamente à `main` em commits posteriores. A versão principal do repositório contém a sequência das TEDs 01, 02 e 03.

**Situação:** materiais técnicos e documentais da TED 03 organizados e disponíveis no repositório público. A submissão do endereço do repositório no Portal do Aluno é uma ação externa e não foi efetuada por este registro.

## Limites e transparência

A execução documentada é **local**, não havendo comprovação de execução do mesmo notebook no Google Colab. O conjunto de dados sustenta uma análise retrospectiva de desempenho acadêmico; os resultados não validam previsão antecipada nem priorização automática de tarefas no MVP.

A declaração descreve dez evidências de uso de IA, mas o texto apresentado não contém capturas de tela nem links individuais para cada consulta. Caso sejam exigidos registros comprobatórios, estes devem corresponder às interações reais. Não foram criados históricos artificiais.
