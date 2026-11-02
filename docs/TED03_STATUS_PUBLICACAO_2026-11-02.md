# TED 03 — estado técnico após a publicação do notebook executado (02/11/2026)

**Projeto:** StudyTrack IA | **Disciplina:** Big Data e Ciências de Dados (UNIBALSAS).

## Evidências verificadas
- Base preparada: `data/processed/dataset_modelagem.csv` (145 registros, 32 colunas; 31 preditoras e alvo `grade`, oito classes; Git blob `7859d534e981355b852a520b5e745aac121f9489`).
- Divisão treino/teste: 116/29, estratificada, `random_state=42`.
- Validação: cinco partes com `StratifiedKFold`, transformações dentro de pipelines (One-Hot para 16 nominais; 15 ordinais preservadas; padronização na Regressão Logística).
- Critério técnico pré-especificado: maior F1-macro médio de validação cruzada.
- Melhor pontuação por esse critério: Random Forest, F1-macro CV **0,227408**.
- Teste final reservado: F1-macro **0,288095**, acurácia **0,379310** (**11/29**); matriz de confusão e relatório por classe na documentação técnica.
- Reprodução **local**: notebook auxiliar com 12 células executadas e saídas/gráficos salvos, incluído na branch em `notebooks/TED03/TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb`. O notebook original `TED03_modelagem.ipynb` foi preservado.

## Aprovação e limitações
Em 02/11/2026 o estudante comunicou que a equipe considera sua avaliação aprovada **desde que** as regras do professor e a autoria dos integrantes tenham sido respeitadas. Essa manifestação foi registrada como condicionada, sem inferir ata formal, aprovação individual documentada ou validação do professor.

**Não foi comprovada execução do notebook no Google Colab oficial.** A execução local não deve ser identificada como execução Colab.

O **Documento Técnico v3.0 acumulativo definitivo** ainda exige integrar os resultados às seções correspondentes, preservando o histórico e as evidências das TEDs 01 e 02; versões antigas ainda descrevem equivocadamente o teste como não realizado. Adendo complementar foi preparado fora do repositório. A declaração de uso de IA deve explicitar o suporte efetivamente prestado, incluindo reprodução técnica e elaboração de apoio documental.

Este resultado é **classificação retrospectiva**: desempenho baixo no teste, risco de sobreajuste e ausência de validação externa. Não comprova previsão antecipada nem utilidade operacional no MVP.

**GitHub:** PR #1 permanece em rascunho e sem merge na `main`.
