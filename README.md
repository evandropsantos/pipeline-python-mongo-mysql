# Pipeline de dados: integrando Python com MongoDB e MySQL

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

[mongo db](https://cloud.mongodb.com/v2/59f05e733b34b96d93ee5d20#/clusters)

```python
    # elimina completamente o banco de dados
    client.drop_database("nome_do_banco_de_dados")
```