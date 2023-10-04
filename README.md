# Pipeline de dados: integrando Python com MongoDB e MySQL

![diagram](https://caelum-online-public.s3.amazonaws.com/3063-pipeline-dados/imagens/Aula1-img1.png "diagrama do projeto")

## Servidor venv

```bash
    python3 -m venv venv
    source venv/bin/activate
```

## Criar requirements (dependencias)

```bash
    pip freeze > requirements.txt
```

## Mongo DB

- [mongo db](https://cloud.mongodb.com/v2/59f05e733b34b96d93ee5d20#/clusters)

```python
    # elimina completamente o banco de dados
    client.drop_database("nome_do_banco_de_dados")
```

## Operadores

- [documentação](https://www.mongodb.com/docs/manual/reference/operator/query/)

O pymongo, assim como o MongoDB, suporta uma variedade de operadores de consulta para lidar com diferentes situações. Aqui estão alguns dos mais comumente usados:

- `$gt:` captura documentos no qual o valor de um campo é superior ao especificado.
- `$gte:` utilizado quando o valor de um campo precisa ser maior ou igual ao valor especificado.
- `$lt:` encontra documentos em que o valor de um campo é menor que o especificado.
- `$lte:` utilizado para valores de campos menores ou iguais ao valor especificado.
- `$ne:` filtra documentos nos quais o valor de um campo é diferente do valor especificado.
- `$in:` útil quando o valor de um campo está dentro de um conjunto especificado de valores.
- `$nin:` encontra documentos em que o valor de um campo não está em um conjunto especificado de valores.
- `$regex:` permite a utilização de uma expressão regular para correspondências mais complexas.

Alguns exemplos de como podemos usar estes operadores:

```python
    # $gt: encontra documentos onde o "Preço" é superior a 500.
    query = {"Preço": {"$gt": 500}}

    #$gte: localiza documentos onde a "Avaliação da compra" seja maior ou igual a 4.
    query = {"Avaliação da compra": {"$gte": 4}}

    #$lt: busca documentos onde a "Quantidade de parcelas" é menor que 3.
    query = {"Quantidade de parcelas": {"$lt": 3}}

    #$lte: seleciona documentos em que o "Frete" seja menor ou igual a 50.
    query = {"Frete": {"$lte": 50}}

    # $ne: localiza documentos em que o "Tipo de pagamento" não seja "cartao_credito".
    query = {"Tipo de pagamento": {"$ne": "cartao_credito"}}

    #$in: filtra documentos nos quais a "Categoria do Produto" seja "esporte e lazer" ou "eletrônicos".
    query = {"Categoria do Produto": {"$in": ["esporte e lazer", "eletronicos"]}}

    # $nin: busca documentos nos quais a "Categoria do Produto" não seja nem "esporte e lazer" nem "eletrônicos".
    query = {"Categoria do Produto": {"$nin": ["esporte e lazer", "eletronicos"]}}

    # $regex: encontra todos os vendedores cujos nomes começam com "Ma".
    query = {"Vendedor": {"$regex": "^Ma"}}

    for doc in collection.find(query):
    print(doc)

```

## MySQL

### Criando um usuário

```bash
    # Iniciando
    sudo mysql
```

```sql
    --  Criando um usuário
    CREATE USER 'evpersa'@'localhost' IDENTIFIED BY '12345';

    -- Dando privilegios
    GRANT ALL PRIVILEGES ON *.* TO 'evpersa'@'localhost';

    -- Finalizando
    exit
```

## mysql.connector

O `mysql.connector` é uma biblioteca Python que permite a conexão com um banco de dados MySQL a partir de um script Python. Isso é feito através do MySQL Connector/Python, um driver de banco de dados que permite que as aplicações Python se comuniquem com os servidores MySQL.

Essa biblioteca apresenta diversas funcionalidades essenciais na manipulação de bancos de dados. Entre as principais, podemos destacar:

connect(): é o método que estabelece a conexão entre a aplicação Python e o servidor de banco de dados. Ele é essencial para iniciar qualquer operação no banco de dados. O método connect() requer parâmetros como host, usuário, senha e nome do banco de dados para estabelecer a conexão.

cursor(): uma vez estabelecida a conexão, a função cursor() é utilizada para criar um objeto cursor. Esse objeto é uma interface que permite a execução de comandos SQL e a manipulação dos registros do banco de dados. O cursor permite navegar, buscar, inserir e excluir registros na base de dados.

execute(): método que efetivamente executa os comandos SQL. Ele é aplicado através do objeto cursor e recebe como parâmetro a string do comando SQL a ser executado.

Utilizando o `mysql.connector`, é possível executar todas as operações padrão de um banco de dados, como: inserir, selecionar, atualizar e excluir dados em um banco de dados MySQL. Além disso, você pode usar esse módulo para realizar operações mais avançadas, como transações, procedimentos armazenados e muito mais. Assim, o mysql.connector torna-se uma ferramenta poderosa e flexível para a manipulação de bancos de dados MySQL a partir de aplicações Python.

[documentação](https://dev.mysql.com/doc/connector-python/en/)