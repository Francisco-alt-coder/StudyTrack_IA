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
│   └── TED02/
│       └── TED02_limpeza_EDA.ipynb
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

## Tecnologias utilizadas

- Python
- Pandas
- Matplotlib
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
