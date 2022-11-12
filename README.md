# Big Data with AWS
Explorando Dados Demográficos na AWS utilizando os serviços de Big data: Athena, QuickSight, Glue e S3.

### Sumario
1. [Introdução a AWS](https://github.com/WANGOMES/big-data-with-aws#introdu%C3%A7%C3%A3o-a-aws);
2. [Criação de Conta na Amazon](https://github.com/WANGOMES/big-data-with-aws#cria%C3%A7%C3%A3o-de-conta-na-amazon);
2. [Entendendo sobre os serviços da AWS: S3, Glue, Athena e QuickSight](https://github.com/WANGOMES/big-data-with-aws#entendendo-sobre-os-servi%C3%A7os-da-aws-s3-glue-athena-e-quicksight);
3. [Explorando dados demográficos do Brasil - passo a passo](https://github.com/WANGOMES/big-data-with-aws#explorando-dados-demogr%C3%A1ficos-do-brasil).

### Introdução a AWS
**AWS - Amazon Web Services** - Provedor de soluções computacionais em núvem e sob demanda. Na AWS    encontramos serviços de Computação em núvem (EC2, AWS Lambda), de Banco de Dados (RDS, DynamoDB, Redshift), para Plataforma Móvel (Amazon API Gateway), para IoT, Machine Learning (Amazon SageMaker), Armazenamento( amazon S3), de Análise de Dados (Athena, Kinesis), Ferramentas de Desenvolvedor, Conteineres, Games, Robótica e muito mais.

![Data Analytics Services AWS](https://user-images.githubusercontent.com/40408615/201495310-eacda71f-8997-44cf-94d3-f3e4fcc1d57b.jpeg "Data Analytics Services AWS")

### Criação de Conta na Amazon Web Services - AWS

![Criando uma Conta Gratuita na AWS - imagem](https://user-images.githubusercontent.com/40408615/201495370-a020780a-c64e-4c2a-94ca-6a812d522d4c.jpeg "Criando uma Conta Gratuita na AWS")

Para criar uma conta na AWS basta ter um email válido e um cartão de crédito. A conta de nível gratuito possui os seguintes serviços:
 - Amazon EC2 - 750hs/mês de computação em núvem;
 - Amazon S3 - 5GB de armazenamento de documentos (20.000 GETs e 2.000 PUTs de solicitações);
 - Amazon DynamoDB - 25GB de armazenamento;
 - Amazon SageMaker - 2 meses de Machine Learning;
 - Amazon redshift - 2 meses de Data Warehousing;
 - AWS Lambda - 1 Milhão/mẽs de solicitações, entre outros.

[Clique para criar sua conta na AWS](https://portal.aws.amazon.com/billing/signup?refid=c623d581-46f6-43a2-b227-cabbee9cd673&redirect_url=https%3A%2F%2Faws.amazon.com%2Fregistration-confirmation&language=pt_br#/start/email).

### Entendendo sobre os serviços da AWS: S3, Glue, Athena e QuickSight

**Amazon S3**

O Amazon Simple Storage Service (Amazon S3) é um serviço de armazenamento de objetos que oferece escalabilidade, disponibilidade de dados, segurança e performance. 

Pode ser utilizado para armazenar e proteger qualquer volume de dados para uma variedade de casos de uso, como data lakes, sites, aplicações móveis, backup e restauração, arquivamento, aplicações corporativas, dispositivos IoT e análises de big data. 

**Amazon Glue**
 
O AWS Glue é um serviço de integração de dados com tecnologia sem servidor que facilita aos usuários de análise a descoberta, preparação, transferência e integração de dados de várias fontes. Pode ser usado para análise, machine learning e desenvolvimento de aplicações. 

Possui ferramentas de produtividade e operações de dados para criação, execução de trabalhos e implementação de fluxos de trabalho de negócios.

**Amazon Athena**

O Amazon Athena é um serviço de consultas interativas que facilita a análise de dados diretamente no Amazon S3 usando SQL padrão. Com algumas ações no AWS Management Console, você pode direcionar o Athena para os dados armazenados no Amazon S3 e começar a usar o SQL padrão para executar consultas.

Como o Athena não utiliza servidor, não há infraestrutura para configurar ou gerenciar, e você paga apenas pelas consultas executadas. 

É escalado automaticamente, executando consultas em paralelo, o que acelera os resultados mesmo em conjuntos de dados grandes e consultas complexas.

**Amazon QuickSight**

Amazon QuickSight é um serviço de business intelligence (BI) em escala de nuvem e se conecta aos seus dados na nuvem e combina dados de muitas fontes diferentes. Em um único painel de dados é possível incluir dados da AWS, dados de terceiros, big data, dados de planilhas, dados SaaS, dados B2B e outros.

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
