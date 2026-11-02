# StudyTrack IA

Projeto acadêmico do curso de **Análise e Desenvolvimento de Sistemas (ADS)** do Centro Universitário de Balsas (**UNIBALSAS**). O StudyTrack IA propõe apoiar estudantes no cadastro de disciplinas e atividades, acompanhamento de prazos, calendário e visualização de prioridades.

Este repositório reúne a continuidade da disciplina **Big Data e Ciências de Dados**, preservando as etapas de seleção da base (TED 01), preparação e análise exploratória (TED 02) e modelagem com Machine Learning (TED 03).

## Integrantes

- Caio Vinícius Lima Soares
- David Rodrigues Costa
- Francisco Wesley de Souza Dias
- Pedro Henrique Guedes

**Professor:** Alex Rogaleski Marques  
**Período:** 2026.2

## Etapas do projeto de dados

| Etapa | Conteúdo | Documentação |
| --- | --- | --- |
| TED 01 | Definição do problema, necessidades de dados e seleção de base pública. | [PDF da TED 01](docs/TED01.pdf) |
| TED 02 | Inspeção, tratamento, análise exploratória, estatísticas e visualizações. | [PDF da TED 02](docs/TED02.pdf) |
| TED 03 | Classificação multiclasse de desempenho, comparação de classificadores e avaliação final. | [Documento Técnico v3.0](docs/TED03_Documento_Tecnico_v3_Consolidado.pdf) |

**Base utilizada:** [Higher Education Students Performance Evaluation — UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/856/higher+education+students+performance+evaluation). O conjunto contém 145 observações e, na versão de modelagem, 31 preditoras e a variável-alvo `grade` com oito classes. A fonte original possui licença CC BY 4.0.

O estudo é **retrospectivo**, não uma validação de previsão antecipada de notas nem do sistema de priorização de tarefas do MVP.

## Organização dos arquivos

```text
StudyTrack_IA/
├── README.md
├── docs/
│   ├── TED01.pdf
│   ├── TED02.pdf
│   ├── TED03_Documento_Tecnico_v3_Consolidado.pdf
│   ├── TED03_Documento_Tecnico_v3_Consolidado.md
│   ├── TED03_RESULTADOS_TECNICOS_2026-11-02.md
│   └── TED03_STATUS_PUBLICACAO_2026-11-02.md
├── data/
│   ├── raw/
│   │   └── DATA.csv
│   └── processed/
│       ├── dataset_tratado.csv
│       └── dataset_modelagem.csv
└── notebooks/
    ├── TED02/
    │   └── TED02_limpeza_EDA.ipynb
    └── TED03/
        ├── TED03_modelagem.ipynb
        └── TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb
```

A TED 01 é documental e, por isso, não exige um notebook próprio. As versões antigas dos arquivos permanecem no histórico de commits do Git.

### Dados

- `data/raw/DATA.csv`: conjunto original, preservado.
- `data/processed/dataset_tratado.csv`: colunas renomeadas para leitura e análise.
- `data/processed/dataset_modelagem.csv`: 145 registros e 32 colunas, sem o identificador de estudante.

### Notebooks

- [TED 02 — limpeza e análise exploratória](notebooks/TED02/TED02_limpeza_EDA.ipynb)
- [TED 03 — notebook de modelagem](notebooks/TED03/TED03_modelagem.ipynb)
- [TED 03 — reprodução local com saídas](notebooks/TED03/TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb)

A reprodução publicada é **local**; ela não deve ser apresentada como execução comprovada no Google Colab.

## Tecnologias

Python, Pandas, NumPy, Matplotlib, Scikit-learn, Jupyter Notebook, Git e GitHub.

## Como executar os códigos

1. Clone o repositório e abra a pasta `StudyTrack_IA`.
2. Crie um ambiente Python, de preferência com `venv`.
3. Instale as bibliotecas necessárias:

   ```bash
   pip install pandas numpy matplotlib scikit-learn jupyter
   ```

4. Inicie o Jupyter:

   ```bash
   jupyter notebook
   ```

5. Abra o notebook da TED desejada e execute as células na ordem. A base preparada da TED 03 está em `data/processed/dataset_modelagem.csv`.

**Verificações esperadas na TED 03:** base de 145 × 32; divisão estratificada em 116 registros de treinamento e 29 de teste; resultados de validação cruzada e teste reservado documentados no notebook. Versões diferentes das bibliotecas podem demandar ajustes de compatibilidade.

## Resultados da TED 03

Foram comparados Regressão Logística, Árvore de Decisão e Random Forest com validação cruzada estratificada de cinco partes e **F1-macro** como métrica principal. Na reprodução técnica registrada, o Random Forest apresentou F1-macro médio de **0,227408** na validação cruzada. No teste reservado, obteve **0,288095** de F1-macro, **37,93%** de acurácia e **11 acertos em 29 registros**.

Esses resultados são limitados pelo tamanho da amostra e pelo desequilíbrio entre classes. Eles não demonstram desempenho suficiente para uso prático nem a priorização automática de atividades do StudyTrack IA.

## Continuidade e histórico

Este mesmo repositório reúne as TEDs anteriores e a TED 03. Os dados originais, as versões processadas, os notebooks e os documentos permanecem separados para facilitar reprodução e conferência. Antes de apresentar resultados, confira a versão do notebook, as saídas e o documento técnico correspondente.
