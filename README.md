# Sejam bem vindos Pessoal!😃

Projeto designado para a atividade: "Trabalhando com Machine Learning na Prática no Azure ML", onde irei desenvolver um modelo de previsão em machine learning e criar um passo a passo que será usado para realizar a atividade.

## Primeiros passos ⌨

#️⃣ Se você já tiver um espaço de trabalho do Azure Machine Learning, poderá usá-lo e pular para a próxima tarefa.


1️⃣ Crie um novo repositorio no GITHUB com um nome de sua escolha.

2️⃣ Entre no portal do Azure, selecione **+ Criar um recurso**, pesquise Machine Learning e crie um novo recurso do Azure Machine Learning com as seguintes configurações:

* **Assinatura** : sua assinatura do Azure .
* **Grupo de recursos** : Crie ou selecione um grupo de recursos .
* **Nome** : Insira um nome exclusivo para seu espaço de trabalho .
* **Região** : Selecione a região geográfica mais próxima .
* **Conta de armazenamento** : observe a nova conta de armazenamento padrão que será criada para seu espaço de trabalho .
* **Cofre de chaves** : Observe o novo cofre de chaves padrão que será criado para seu espaço de trabalho .
* **Insights de aplicativo** : observe o novo recurso padrão de insights de aplicativo que será criado para seu espaço de trabalho .
* **Registro de contêiner** : Nenhum ( um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner ).

3️⃣ Selecione **Revisar + criar** e selecione **Criar**. Aguarde a criação do seu espaço de trabalho (podde levar alguns minutos) e, em seguida, vá para o recurso **implantado**.

4️⃣Selecione **Launch Studio** (ou abra uma nova guia do navegador e navegue até https://ml.azure.com e entre no Azure Machine Learning Studio usando sua conta da Microsoft). Feche todas as mensagens exibidas.

5️⃣No estúdio Azure Machine Learning, você deverá ver seu espaço de trabalho recém-criado. Caso contrário, selecione **Todos os espaços de trabalho no menu à esquerda** e selecione o espaço de trabalho que você acabou de criar.

#### Tudo certo, seu espaço de trabalho foi criado✅


## Use aprendizado de máquina automatizado para treinar um modelo💻
No Azure Machine Learning Studio , veja a página Automated ML, crie um novo trabalho de **ML automatizado** com as seguintes configurações:
#### 🔹Configurações básicas :


▪ Nome do trabalho :  mslearn-bike-automl

▪ Novo nome do experimento : mslearn-bike-rental

▪ Descrição : Aprendizado de máquina automatizado para previsão de aluguel de bicicletas

▪ Marcadores : nenhum

### Tipo de tarefa e dados :

▪ Selecione o tipo de tarefa : Regressão

▪ Selecionar conjunto de dados : crie um novo conjunto de dados com as seguintes configurações:

####  🔹Tipo de dados :

▪ Nome : aluguel de bicicletas

▪ Descrição : dados históricos de aluguel de bicicletas

▪ Tipo : Tabular
#### 🔹Fonte de dados :
▪ Selecione **Dos arquivos da web**

#### 🔹URL da Web :

▪ URL da Web :https://aka.ms/bike-rentals

▪ Ignorar validação de dados : não selecionar


#### 🔹Configurações :

▪ Formato de arquivo : Delimitado

▪ Delimitador : Vírgula

▪ Codificação : UTF-8

▪ Cabeçalhos de coluna : apenas o primeiro arquivo possui cabeçalhos

▪ Pular linhas : Nenhum

▪ O conjunto de dados contém dados multilinhas : não selecione

#### 🔹Esquema :
▪ Incluir todas as colunas exceto Caminho

▪ Revise os tipos detectados automaticamente

Selecione **Criar** . Após a criação do conjunto de dados, selecione o conjunto de dados **de aluguel de bicicletas** para continuar a enviar o trabalho de ML automatizado.

 ### Configurações de tarefa :
▪ Tipo de tarefa : Regressão

▪ Conjunto de dados : aluguel de bicicletas

▪ Coluna de destino : Aluguéis (inteiro)

#### 🔹Clique em configurações adicionais :
▪ Métrica primária : Normalized root mean squared error

▪ Desmarque 🔲 explicar o melhor modelo

▪ Desmarque 🔲 Usar todos os modelos suportados. Você restringirá o trabalho para tentar apenas alguns algoritmos específicos para realizar testes.

▪ Modelos permitidos : Selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o máximo possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.

#### 🔹Limites : expanda esta seção
▪ Máximo de testes : 3

▪ Máximo de testes simultâneos : 3

▪ Máximo de nós : 3

▪ Limite de pontuação da métrica : 0,085 ( para que, se um modelo atingir uma pontuação da métrica de erro quadrático médio normalizado de 0,085 ou menos, o trabalho termina. )

▪ Tempo limite : 15

▪ Tempo limite de iteração : 15

☑️Habilitar encerramento antecipado

#### 🔹Validação e teste :
▪ Tipo de validação : divisão de validação de trem

▪ Porcentagem de dados de validação : 10

▪ Conjunto de dados de teste : Nenhum

### Calcular :

▪ Selecione o tipo de computação : sem servidor

▪ Tipo de máquina virtual : CPU

▪ Camada de máquina virtual : Dedicada

▪ Tamanho da máquina virtual : Standard_DS3_V2*

▪ Número de instâncias : 1

* Se a sua assinatura restringir os tamanhos de VM disponíveis para você, escolha qualquer tamanho disponível. Envie o trabalho de treinamento. Ele inicia automaticamente.Espere o trabalho terminar. Em alguns casos pode demorar até 15 minutos ou mais – agora pode ser um **bom momento para descansar**!

## Avalie o melhor modelo ✔

1️⃣ Na guia Visão geral do trabalho automatizado de aprendizado de máquina, observe o melhor resumo do modelo.

2️⃣ Selecione o texto em **Nome do algoritmo** do melhor modelo para visualizar seus detalhes.

3️⃣ Selecione a guia **Métricas** e selecione os **gráficos residuais** e **predito_true** se eles ainda não estiverem selecionados.

* Revise os gráficos que mostram o desempenho do modelo. O gráfico **de resíduos** mostra os resíduos (as diferenças entre os valores previstos e reais) como um histograma. O gráfico **predito_true** compara os valores previstos com os valores verdadeiros.

## Implantar e testar o modelo. 💾

1️⃣ Na guia Modelo selecione Implantar e marque Serviços Web Agora Preencha o campo a seguir com as seguintes configurações :

▪ Nome : prever-alugueis (Sem acentuação)

▪ Descrição : Prever aluguel de bicicletas

▪ Tipo de computação : Instância de Contêiner do Azure

▪ Habilitar autenticação✅ : selecionado

* Aguarde o início da implantação – isso pode levar alguns segundos. O **status de implantação** do endpoint **de previsão de aluguel** será indicado na parte principal da página como **Running**.

2️⃣  No painel Dados de entrada para testar o endpoint , substitua o modelo JSON pelos seguintes dados de entradaNo painel Dados de entrada para testar o endpoint , substitua o modelo JSON pelos seguintes dados de entrada:

        {
        "Inputs": { 
            "data": [
            {
            "day": 1,
            "mnth": 1,   
            "year": 2022,
            "season": 2,
            "holiday": 0,
            "weekday": 1,
            "workingday": 1,
            "weathersit": 2, 
            "temp": 0.3, 
            "atemp": 0.3,
            "hum": 0.3,
            "windspeed": 0.3 
            }
        ]    
    },   
     "GlobalParameters": 1.0
    }

Agora clique no botão **Testar**. Revise os resultados do teste, que incluem um **número previsto de aluguéis** com base nos recursos de entrada - 
semelhante a este:

`
 {
   "Results": [
     444.27799000000000
   ]
 }
`

* O painel de teste pegou os dados de entrada e usou o modelo treinado para retornar o número previsto de aluguéis.

## Limpar🗑
* O serviço web que você criou está hospedado em uma instância de contêiner do Azure . Se não pretender experimentá-lo ainda mais, deverá eliminar o ponto final para evitar acumular utilização desnecessária do Azure. Aqui esta o passo a passo para eliminar:

▪ No estúdio Azure Machine Learning , na guia **Endpoints** , selecione o ponto de **extremidade de previsão de aluguel**. Em seguida, selecione **Excluir** e confirme que deseja excluir o endpoint.

* Excluir sua computação garante que sua assinatura não será cobrada por recursos de computação.


Se o espaço de trabalho do Azure Machine Learning existir ainda em sua assinatura, será cobrada uma pequena quantia. 

🔹Para excluir seu espaço de trabalho:

▪ No portal Azure, entre na página **Grupos de recursos**, abra o grupo de recursos que especificou ao criar o seu espaço de trabalho Azure Machine Learning.

▪ Clique em **Excluir grupo de recursos**, digite o nome do grupo de recursos para confirmar que deseja excluí-lo e selecione Excluir.

### TENHA UM BOM LAB ☺
