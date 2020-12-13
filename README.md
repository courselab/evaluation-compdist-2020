# Computação Distribuida - Problema do Consenso

Abaixo está um simples tutorial de como deve ser executado o projeto

## Como rodar o projeto

Primeiramente, tenha o python instalado em sua máquina.

Instale as dependecias com o seguinte comando abaixo:

```sh
$ cd python_blockchain_app
$ pip install -r requirements.txt
```

Inicie o blockchain server :

```sh
$ export FLASK_APP=node_server.py
$ flask run --port 8000
```

Rode a aplicaçao em um terminal diferente : 

```sh
$ python run_app.py
```

A aplicaçao estará rodando no endereço : [http://localhost:5000](http://localhost:5000).

Para rodar com multiplos nodes, execute os comandos abaixo, como exemplo :

```sh
# Make sure you set the FLASK_APP environment variable to node_server.py before running these nodes
# already running
$ flask run --port 8000 &
# spinning up new nodes
$ flask run --port 8001 &
$ flask run --port 8002 &
```

Registre os nodes da seguinte forma : 

```sh
curl -X POST \
  http://127.0.0.1:8001/register_with \
  -H 'Content-Type: application/json' \
  -d '{"node_address": "http://127.0.0.1:8000"}'
```

```sh
curl -X POST \
  http://127.0.0.1:8002/register_with \
  -H 'Content-Type: application/json' \
  -d '{"node_address": "http://127.0.0.1:8000"}'
```

