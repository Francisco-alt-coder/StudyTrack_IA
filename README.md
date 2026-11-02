# StudyTrack IA

O **StudyTrack IA** é um projeto acadêmico desenvolvido com o objetivo de ajudar estudantes universitários a organizar melhor sua rotina de estudos e acompanhar suas atividades de forma mais clara.

A proposta surgiu a partir de um problema comum no ambiente acadêmico: lidar ao mesmo tempo com diferentes disciplinas, trabalhos, avaliações, prazos e prioridades. O sistema busca reunir essas informações em um único ambiente e, futuramente, utilizar recursos de Inteligência Artificial para apoiar o estudante na tomada de decisões sobre o que precisa de mais atenção em cada momento.

## Objetivo do projeto

O principal objetivo do StudyTrack IA é apoiar o planejamento acadêmico por meio do registro e acompanhamento de disciplinas, atividades, prazos e informações relacionadas ao desempenho do estudante.

Entre as funcionalidades previstas para o MVP estão:

- cadastro de disciplinas;
- cadastro e acompanhamento de atividades;
- organização por prazos;
- definição de prioridades;
- calendário acadêmico;
- painel de acompanhamento;
- uso de Inteligência Artificial como apoio ao planejamento e à análise da rotina de estudos.

## Big Data e Ciência de Dados

Este repositório também reúne as etapas desenvolvidas na disciplina de **Big Data e Ciências de Dados**.

Na **TED 01**, foi selecionado o conjunto de dados **Higher Education Students Performance Evaluation**, disponibilizado pelo UCI Machine Learning Repository. A base contém informações relacionadas a hábitos de estudo, frequência às aulas, preparação para avaliações, desempenho anterior e nota final de estudantes do ensino superior.

Na **TED 02**, a mesma base foi utilizada para o processo de inspeção, preparação e análise exploratória dos dados. Foram verificadas questões como valores ausentes, registros duplicados, inconsistências e possíveis problemas de qualidade.

A análise confirmou que a base possui boa integridade, sem valores ausentes, registros duplicados ou códigos fora das faixas documentadas. Por isso, o principal tratamento realizado foi a organização e padronização dos nomes das variáveis para facilitar a leitura e as análises posteriores.

Também foram realizadas análises sobre:

- distribuição das notas finais;
- horas semanais de estudo;
- frequência às aulas;
- impacto de projetos e atividades;
- desempenho no semestre anterior;
- relações entre algumas variáveis e o desempenho acadêmico.

Os resultados mostraram que o desempenho acadêmico não pode ser explicado por um único fator. O histórico acadêmico, a frequência e outros aspectos da rotina apresentaram relações relevantes, enquanto o número de horas de estudo, analisado isoladamente, não apresentou uma relação linear simples com a nota final.

Essas análises ajudam a compreender melhor o comportamento acadêmico dos estudantes, mas a base utilizada não possui informações como prazo das atividades, peso das avaliações ou prioridade das tarefas. Por isso, ela não é suficiente, sozinha, para representar o mecanismo de priorização do StudyTrack IA.

## TED 03 — Modelagem preditiva e Machine Learning

A TED 03 mantém a classificação retrospectiva de `grade` em oito classes, a partir das 31 variáveis preditoras da base preparada na TED 02. Foram comparados Regressão Logística, Árvore de Decisão e Random Forest com divisão estratificada 80/20, validação cruzada de cinco partes e semente 42. As variáveis nominais foram codificadas com One-Hot Encoding, e as ordinais foram padronizadas apenas na Regressão Logística.

**Arquivos centrais para a entrega:**

- **[Documento Técnico v3.0 acumulativo (PDF)](docs/TED03_Documento_Tecnico_v3_Consolidado.pdf)** ([texto acessível](docs/TED03_Documento_Tecnico_v3_Consolidado.md)): preserva as informações das TEDs 01 e 02 e incorpora protocolo, resultados, interpretação e limitações da TED 03.
- **[Notebook executado](notebooks/TED03/TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb)**: 12 células de código executadas, 17 saídas, avaliação e matriz de confusão. **Execução local, não comprovada no Google Colab.**
- **[Notebook original](notebooks/TED03/TED03_modelagem.ipynb)**: versão original mantida para rastreabilidade.
- **[Resultados técnicos](docs/TED03_RESULTADOS_TECNICOS_2026-11-02.md)**: métricas, tabela de validação cruzada e relatório por classe.
- **[Declaração de uso de IA (PDF)](docs/TED03_Declaracao_Uso_IA.pdf)** ([texto acessível](docs/TED03_Declaracao_Uso_IA.md)): registro das ferramentas e etapas de apoio, com responsabilidade de conferência pela equipe.
- **[Situação da publicação](docs/TED03_STATUS_PUBLICACAO_2026-11-02.md)**: distingue evidência técnica de conferência acadêmica.

**Resultados registrados:** Random Forest com maior F1-macro médio de validação cruzada (0,227408); teste reservado de 29 registros com F1-macro 0,288095, acurácia de 37,93% e 11 acertos. O desempenho é limitado e não valida previsão antecipada nem priorização automática no MVP.

**Nota metodológica:** a escolha do Random Forest seguiu uma regra computacional previamente definida; a revisão das interpretações, a autoria e a confirmação da equipe permanecem sob responsabilidade dos integrantes. O Pull Request nº 1 está em rascunho, sem merge para `main`.

### Como executar a TED 03

1. Acesse o notebook executado a partir do link acima, usando Jupyter ou Google Colab.
2. Instale, quando necessário, `pandas`, `numpy`, `matplotlib` e `scikit-learn`. O ambiente que gerou as saídas locais utilizou Python 3.13.5 e scikit-learn 1.8.0; versões diferentes podem exigir compatibilidade do parâmetro `sparse_output`.
3. Execute as células sequencialmente. O notebook lê `data/processed/dataset_modelagem.csv` quando presente; caso contrário, utiliza URL pública do CSV previamente versionado.
4. Confirme a dimensão `145 × 32`, a divisão `116/29` e as saídas da validação cruzada e do teste.
5. Diferencie os resultados já registrados da sua própria execução. Reexecutar localmente ou no Colab não significa que isso já tenha sido comprovado para a submissão.

## Estrutura do repositório

```text
StudyTrack_IA/
│
├── data/
│   ├── raw/
│   │   └── DATA.csv
│   │
│   └── processed/
│       ├── dataset_tratado.csv
│       └── dataset_modelagem.csv
│
├── notebooks/
│   ├── TED02/
│   │   └── TED02_limpeza_EDA.ipynb
│   └── TED03/
│       └── TED03_modelagem.ipynb
│
└── README.md
```

### data/raw

Contém o conjunto de dados original, preservado sem alterações.

- `DATA.csv`: base original utilizada no projeto.

### data/processed

Contém as versões preparadas durante a TED 02.

- `dataset_tratado.csv`: mantém os registros da base original, mas utiliza nomes de colunas mais descritivos.
- `dataset_modelagem.csv`: versão preparada para futuras etapas de modelagem, sem o identificador do estudante.

### notebooks/TED02

Contém o notebook utilizado para reproduzir o processo de inspeção, preparação e análise exploratória.

O arquivo `TED02_limpeza_EDA.ipynb` reúne os códigos utilizados para:

- carregar o conjunto de dados;
- verificar valores ausentes;
- identificar registros duplicados;
- validar os códigos das variáveis;
- renomear e organizar as colunas;
- calcular estatísticas descritivas;
- gerar gráficos;
- analisar relações entre variáveis;
- exportar as bases preparadas.

### notebooks/TED03

Contém `TED03_modelagem.ipynb` e `TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb`. A reprodução local publicada compara os três classificadores, aplica o critério de F1-macro, calcula o teste final e apresenta matriz de confusão e relatórios por classe. A documentação acumulativa e os resultados estão em `docs/`.

## Tecnologias utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook
- Git e GitHub

## Continuidade do projeto

As próximas etapas devem continuar utilizando o mesmo histórico de desenvolvimento, mantendo a separação entre dados originais, dados processados, códigos e documentos.

No contexto do StudyTrack IA, análises futuras poderão utilizar dados próprios do sistema, como:

- prazo da atividade;
- peso ou valor da atividade;
- disciplina;
- status;
- nível de prioridade;
- esforço estimado;
- histórico de conclusão.

Essas informações estarão mais diretamente relacionadas ao objetivo central do projeto, que é auxiliar o estudante na organização e priorização de suas atividades acadêmicas.

## Projeto acadêmico

Projeto desenvolvido no curso de **Análise e Desenvolvimento de Sistemas**, no **Centro Universitário de Balsas (UNIBALSAS)**.

Integrantes:

- Caio Vinícius Lima Soares
- David Rodrigues Costa
- Francisco Wesley de Souza Dias
- Pedro Henrique Guedes
