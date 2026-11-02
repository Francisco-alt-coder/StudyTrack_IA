# Declaração de uso de Inteligência Artificial — TED 03

**Projeto:** StudyTrack IA  
**Disciplina:** Big Data e Ciências de Dados, ADS/UNIBALSAS, 2026.2  
**Professor:** Alex Rogaleski Marques  
**Equipe:** Caio Vinícius Lima Soares; David Rodrigues Costa; Francisco Wesley de Souza Dias; Pedro Henrique Guedes.

## Ferramenta e finalidade

**ChatGPT (OpenAI).** Apoio à conferência do repositório público e da base UCI; consulta e revisão de sintaxe de código Python e bibliotecas; reprodução computacional local de métricas; verificação de consistência entre matriz de confusão, resultados e texto; organização e revisão documental.

A equipe deverá conferir o conteúdo desta declaração e identificar outras ferramentas efetivamente usadas, se houver. Este registro não afirma que a IA tenha sido utilizada somente nessas etapas nem substitui o formulário específico do professor.

## Etapas com apoio técnico registrado

1. Conferência de estrutura do CSV e identidade do arquivo por hash Git.
2. Revisão de pipelines, pré-processamento e validação cruzada estratificada de cinco partes com os três classificadores.
3. Aplicação computacional do critério pré-especificado de maior F1-macro médio, seguida da execução técnica local do Random Forest nos 29 registros reservados.
4. Conferência das métricas (F1-macro 0,288095; acurácia 0,379310), da matriz e do relatório por classe.
5. Organização editorial e revisão do Documento Técnico v3.0, preservando a descrição das TEDs 01 e 02.
6. Revisão de consistência do README, do histórico de publicação e desta declaração.

## Autoria e decisões metodológicas

As decisões metodológicas registradas anteriormente pela equipe foram mantidas: 31 preditoras, 16 nominais, 15 ordinais, divisão 80/20 estratificada, cinco partes de validação, semente 42, F1-macro principal e comparação dos três classificadores. A seleção computacional do maior F1-macro **não é apresentada como deliberação formal dos integrantes**. A interpretação acadêmica e a aprovação da entrega permanecem sob responsabilidade dos estudantes.

## Evidência de execução e validação

O arquivo publicado `notebooks/TED03/TED03_REPRODUCAO_LOCAL_EXECUTADA.ipynb` contém **12 células de código executadas e 17 saídas**. Os registros confirmam a base de 145 registros e 31 preditoras, a divisão 116/29, 11 acertos em 29 observações e os indicadores calculados. O CSV preparado corresponde ao blob Git `7859d534e981355b852a520b5e745aac121f9489`.

A execução registrada foi **local**, não no Google Colab oficial. Não foram realizados validação externa, testes de equidade por subgrupo, implantação em produção nem avaliação operacional do MVP.

## Histórico de consultas

O histórico efetivamente utilizado deverá ser apresentado em link ou PDF, se exigido no termo do professor. Link de uma das conversas relacionadas informado pelo estudante: https://chatgpt.com/share/6ae8bfb4-ea70-83e9-a002-4ed4cc926903

Outras conversas de conferência técnica e de revisão documental devem constar do histórico entregue **se efetivamente utilizadas**, evitando omissões ou criação de evidências fictícias.

## Privacidade e responsabilidade

Foi utilizada uma base pública e não foram inseridas credenciais ou dados pessoais sigilosos nesta revisão. A exclusão do identificador de modelagem não garante anonimização completa. Os estudantes devem conferir as fontes, resultados, redação, riscos e conformidade com as regras de uso restrito de IA da disciplina.

*Registro organizado para conferência da equipe em 02/11/2026. Não presume assinatura ou aprovação individual dos integrantes.*
