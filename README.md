# Implantacao_inferencia_XGBOOST
Implantação e inferência com XGBOOST

OBJETIVO DA ATIVIDADE -

Executar o notebook em Google Colab para treinar e implantar um modelo XGBoost, interpretar resultados de predições em tempo real e de inferências em lote, e registrar as conclusões. 

 

Objetivos específicos: 

 

Preparar e carregar a base de atrasos de voo. 

 

Treinar e salvar o modelo XGBoost localmente. 

 

Simular chamadas de predições em tempo real (um registro por vez). 

 

Simular inferências em lote (conjunto de registros). 

 

Comparar resultados entre tempo real e batch. 

 

Registrar conclusões no notebook. 

- IMPLANTAÇÃO E INFERÊNCIA COM XGBOOST

Um grande site de reservas de viagens vem recebendo diversas reclamações de clientes por causa de atrasos inesperados em voos.
Para melhorar a experiência, a empresa quer criar um recurso que informe, no momento da reserva, a probabilidade de atraso do voo. A proposta é usar dados históricos para analisar fatores como condições climáticas, horário de partida, aeroporto de origem, destino e companhia aérea.
Você, como cientista de dados da equipe, recebeu a tarefa de implantar e testar o modelo de Machine Learning em Google Colab, simulando cenários de predições em tempo real e de inferências em lote (Batch Transform).

🎯 OBJETIVO DA ATIVIDADE
- Executar o notebook em Google Colab para treinar e implantar um modelo XGBoost, interpretar resultados de predições em tempo real e de inferências em lote, e registrar as conclusões.

Objetivos específicos:

- Preparar e carregar a base de atrasos de voo.

- Treinar e salvar o modelo XGBoost localmente.

- Simular chamadas de predições em tempo real (um registro por vez).

- Simular inferências em lote (conjunto de registros).

- Comparar resultados entre tempo real e batch.

- Registrar conclusões no notebook.


🧩 DESAFIO PRÁTICO
O seu notebook deve conter, no mínimo:

1.	Carregar e preparar os dados
- Baixar a base flights_delays_120.csv (ver instruções abaixo).
- Tratar variáveis categóricas (ex.: companhia aérea, origem, destino, clima).
- Dividir treino e teste.

2.	Treinar e salvar o modelo
- Ajustar o XGBClassifier.
- Salvar o modelo treinado em disco (joblib ou pickle).

3.	Predições em tempo real
-	Simular requisições unitárias (um passageiro/voo).
-	Obter a probabilidade de atraso e a classe prevista.

4.	Inferência em lote (Batch Transform)
-	Carregar múltiplos registros de teste.
-	Executar predições em lote e salvar resultados em CSV.


🛠️ ORIENTAÇÕES TÉCNICAS
Na construção do seu notebook, é obrigatório fazer, se aplicável:

| Etapa | Ações mínimas requeridas | Funções/Ferramentas-chave |
| --- | --- | --- |
| Importação dos dados biomédicos | •	Realizar os imports necessários | Import warnings |
|    | Baixar a base de dados através de uma requisição | requests, zipfile, io, pandas, scipy.io e boto3 |
|    | Carregar o arquivo baixado | resquest.get() |
|    |	Converter para dataframe | loadarff() |     
|    | Converter as classes categorias para núméricas | pd.Dataframe() |
| Explorando os dados |  Examinar o número de linhas e colunas | Df.shape |
|    | Obter uma lista das colunas | Df.columns |
| Preparação dos dados | Mover a posição da coluna target | cols = df.columns.tolist() |
|    | Divisão de dados | cols = cols[-1:] + cols[:-1] df = df[cols] |
|    | Upload para S3 | sklearn.model_selection.train_test_split() boto3.Session().resource('s3') |
| Configuração do XGBoost no SageMaker | Definir contêiner do XGBoost. | sagemaker.image_uris.retrieve, sagemaker.estimator.Estimator |
| Treinamento do modelo | •	Iniciar job de treino no SageMaker. | sagemaker.inputs.TrainingInput() |
|    | •	Acompanhar execução e logs. | .fit(), sagemaker.Session |

💡 DICAS

Para facilitar sua pesquisa e aprendizado durante o laboratório, fique de olho em algumas dicas:

1.	Entenda o formato dos dados: revise como pandas apresenta tipos como float64, int64 e object para identificar tipos numéricos e categóricos.
2.	Divisão de dados: pesquise sobre train_test_split com o parâmetro stratify para manter a proporção das classes ao separar treino e teste.
3.	Upload para S3: explore a biblioteca boto3 para enviar arquivos CSV diretamente sem salvar localmente, usando buffers de memória (io.StringIO).
4.	Configuração do SageMaker: revise como usar sagemaker.estimator.Estimator e sagemaker.inputs.TrainingInput para definir containers, instâncias e canais de dados.
5.	Hiperparâmetros XGBoost: entenda o significado de parâmetros como num_round, eval_metric e objective para ajustar o treinamento.
6.	Monitoramento do treinamento: familiarize-se com os logs do SageMaker para acompanhar o progresso do modelo e detectar problemas.




