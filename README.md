# Como criar um modelo de previsão com seus devidos pontos de extremidades configurados

Nos passos abaixo descrevo como podemos criar um ambiente de trabalho no Microsoft Azure Machine Learning.
Você usará o recurso de aprendizado de máquina automatizado no Azure Machine Learning para treinar e avaliar um modelo de aprendizado de máquina, você implantará e testará o modelo treinado.

**Objetivo:** Aprendizado de máquina automático para previsão de aluguel de bicicletas.

1 - Crie a conta Azure através do link abaixo: https://azure.microsoft.com
  (Faça um pequeno cadastro com seus dados pessoais e cartao de crédito, a utilização do cartão de crédito é apenas para garantir que a sua conta é real, ao realizar o cadastro você terá U$200 disponível durante 30 dias, é interessante excluir tudo que foi criado após criar seus testes).
  * Existem serviços que são gratuitos por 12 meses
  * Mais de 55 serviços gratuitos

2 - Após criar sua conta, clique em "Create a resource"
(Interessante colocar no idioma em inglês atráves do ícone de engrenagem no canto superior direito).

3 - Busque pelo serviço "Azure Machine Learning"
  Organize as informações dentro do Azure.
  - Coloque o nome em "Resource group", sugestão: "LABAI-900".
  - Em "Name" coloque como sugestão "laboratorioai900".
  - Em "Region: East US".
  - Mantenhos os outros campos como estão preenchidos.

4 - Clique em "Create"
  * Sempre que estiver criando algo mantenha-se na página para verificar se tudo ocorreu corretamente.

5 - Após criado, clique em "Go to resource".
  
6 - Na parte inferior da página clique em "Launch studio" para a criação de modelos.
  (Quando clicar no botão, você será redirecionado ao endereço https://ml.azure.com)

7 - Clique no menu do lado esquerdo na opção "ML automatizado".

8 - Clique em "Novo trabalho de ML automatizado".
    Vamos utilizar uma base de dados públicos em nosso exemplo
    - Nome do trabalho: mslearn-bike-automl
    - Novo nome do experimento: mslearn-bike-rental
    - Descrição: Aprendizado de máquina automático para previsão de aluguel de bicicletas.
    Clique em "Avançar".

9 - Em tipo de tarefa e dados coloque "Regressão".
    - Em "Selecionar os dados", clique em "Criar".
    - Em "Nome" colocar "alugueldebicicletas" (sem espaços).
    - Em "Descrição" colocar "Dados históricos de aluguel de bicicletas".
    - Tipo: Tabular
    Clique em "Avançar".

10 - Em "Escolha uma fonte para o ativo de dados" escolha "De arquivo da Web".
    - Em URL da Web: https://aka.ml/bike-rentals
    - Configurações: Somente altere a informação "Cabeçalho de coluna: Somente o primeiro arquivo tem cabeçalhos".
    Clique em "Avançar".

11 - Não precisa alterar nada na tela de "Esquema".
    Clique em "Avançar".

12 - Aparecerá uma tela de resumo de tudo que foi preenchido.
    Clique em "Criar".  

13 - Aguarde alguns minutos para a criação da tarefa e dados.
    Após finalizado clique no nome dos dados "alugueldebicicletas"
    Clique em "Avançar".

14 - A próxima tela é "Configuração de tarefas".
  - Coluna de destino: rentals (Integer)
  - Clique no link "Exibir definições de configuração adicionais".
  - Métrica primária: NormalizeRootMeanSquaredError
  - Desmarque a opção "Explicar o melhor modelo".
  - Desmarque a opção "Usar todos os modelos suportados".
  - Em "Modelos permitidos", colocar "RandomForest" e "LightGBM".
  Clique em "Salvar".

 15 - Expanda "Limites"
   - Máximo de avaliações: 3
   - Máximo de avaliações simultâneas: 3
   - Máximo de nós: 3
   - Limite de pontuação da métrica: 0,085
   - Tempo limite do experimento (minutos): 15
   - Tempo limite de iteração (minutos): 15
   - Marque a opção "Habilitar encerramento antecipado".
   - Tipo de validação: Divisão de validação de treinamento.
   - Validação de percentual de dados: 10
   Clique em "Avançar".

16 - Na tela "Computação", não precisa alterar nada.
   Clique em "Avançar".

17 - Na tela "Examinar", clicar em "Enviar trabalho de treinamento".

18 - Analise as métricas do "algoritmo".

19 - Selecione a guia Métricas e selecione os gráficos residuais e predito_true se eles ainda não estiverem selecionados.

Revise os gráficos que mostram o desempenho do modelo. 
O gráfico de resíduos mostra os resíduos (as diferenças entre os valores previstos e reais) como um histograma. 
O gráfico predito_true compara os valores previstos com os valores verdadeiros.

Os 2 passos abaixo são importantes:
1 - Implantar e testar o modelo
2 - Testar o serviço implantado

Consultar documentação de referência:
Referência: https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html
