# Big Data with AWS
Explorando Dados Demográficos na AWS utilizando os serviços de Big data: Athena, QuickSight, Glue e S3.

### Sumario
1. [Introdução a AWS](https://github.com/WANGOMES/big-data-with-aws#introdu%C3%A7%C3%A3o-a-aws);
2. [Criação de Conta na Amazon](https://github.com/WANGOMES/big-data-with-aws#cria%C3%A7%C3%A3o-de-conta-na-amazon);
2. [Entendendo sobre os serviços da AWS: S3, Glue, Athena e QuickSight](https://github.com/WANGOMES/big-data-with-aws#entendendo-sobre-os-servi%C3%A7os-da-aws-s3-glue-athena-e-quicksight);
3. [Explorando dados demográficos do Brasil - passo a passo](https://github.com/WANGOMES/big-data-with-aws#explorando-dados-demogr%C3%A1ficos-do-brasil).

### Introdução a AWS
**AWS - Amazon Web Services** - Provedor de soluções computacionais em núvem e sob demanda. Na AWS    encontramos serviços de Computação em núvem (EC2, AWS Lambda), de Banco de Dados (RDS, DynamoDB, Redshift), para Plataforma Móvel (Amazon API Gateway), para IoT, Machine Learning (Amazon SageMaker), Armazenamento( amazon S3), de Análise de Dados (Athena, Kinesis), Ferramentas de Desenvolvedor, Conteineres, Games, Robótica e muito mais.

![Data Analytics Services AWS](https://repository-images.githubusercontent.com/119132172/34a4c900-9677-11e9-8684-70f8049d35ea "Data Analytics Services AWS")

### Criação de Conta na Amazon


![Criando uma Conta Gratuita na AWS - imagem](http://dfcumz7fkmzfb.cloudfront.net/wp-content/uploads/2018/11/01100444/AWS_Console_-_Signup.png "Criando uma Conta Gratuita na AWS")

### Entendendo sobre os serviços da AWS: S3, Glue, Athena e QuickSight
- Amazon S3
- Amazon Glue
- Amazon Athena
- Amazon QuickSight

### Explorando Dados Demográficos do Brasil

### Criar bucket no Amazon S3

- Amazon S3 Console -> Buckets -> Create bucket -> Bucket name [nome_do bucket] - Create bucket
- Create folder (Criar uma pasta chamada ```/output``` e outra com o nome do seu conjunto de dados. Este nome irá definir o nome da tabela criada no Glue)
- Upload dos arquivos de dados localizados na pasta ```/data```

#### Criar Glue Crawler

- Amazon Glue Console -> Crawlers -> Add Crawler
- Source type [Data Stores] -> Crawl all folders
- Data store [S3] -> Include path [caminho do diretório dos dados de entrada]
- Create IAM Role
- Frequency [Run on demand]
- Database name [seu_nome_de_db]
- Group behavior [Create a single schema for each S3 path]
- Finish
- Databases -> Tables -> Visualizar dados das tabelas criadas

### Criar aplicação no Amazon Athena

- Query editor -> Settings -> Manage settings -> Query result location and encryption -> Browse S3 -> selecionar o bucket criado
- Selecionar Database -> criar queries (exemplos na pasta ```/src```)
- Verificar queries não salvas no bucket criado no S3
- Salavar queries -> Executar novamente -> Verificar no bucket criado no S3

#### Criando nova tabela

- Generate table DDL
- Copiar a query gerada
- Selecionar o DB e criar a nova tabela em uma nova query

### Visualizar dados no Amazon QuickSight

- Signup (caso não tenha conta) -> Escolher [Standard]
- Datasets -> Create new dataset -> Athena -> Name [NomeDoDataSet] -> Create
- Select database -> select table -> Edit or preview -> Save & visualize
- Criar visualizações selecionando colunas, criando filtros e parâmetros e selecionando Visual types para gráficos.

### Eliminar recursos
 - Exluir os elementos criados
### Créditos
Material do Prof. [Cassiano Peres (Analista e Desenvolvedor de Sistemas e Instrutor na DIO)](https://github.com/cassianobrexbit)
