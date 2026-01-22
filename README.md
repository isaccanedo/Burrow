[![Join the chat at https://gitter.im/linkedin-Burrow/Lobby](https://badges.gitter.im/linkedin-Burrow/Lobby.svg)](https://gitter.im/linkedin-Burrow/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Build Status](https://travis-ci.org/linkedin/Burrow.svg)](https://travis-ci.org/linkedin/Burrow)
[![go report card](https://goreportcard.com/badge/github.com/linkedin/Burrow)](https://goreportcard.com/report/github.com/linkedin/Burrow)
[![Coverage Status](https://coveralls.io/repos/github/linkedin/Burrow/badge.svg?branch=master)](https://coveralls.io/github/linkedin/Burrow?branch=master)
[![GoDoc](https://godoc.org/github.com/linkedin/Burrow?status.svg)](https://godoc.org/github.com/linkedin/Burrow)

# Burrow - Verificação de atraso do consumidor Kafka

Burrow é um companheiro de monitoramento do [Apache Kafka](http://kafka.apache.org) que fornece verificação de atraso do consumidor como um serviço sem a necessidade de especificar limites. Ele monitora as compensações comprometidas para todos os consumidores e calcula o status desses consumidores sob demanda. Um endpoint HTTP é fornecido para solicitar o status sob demanda, bem como fornecer outras informações do cluster Kafka. Há também notificadores configuráveis que podem enviar status via e-mail ou chamadas HTTP para outro serviço.

# recursos
* SEM LIMITES! Os grupos são avaliados em uma janela deslizante;
* Suporte a vários clusters Kafka;
* Monitora automaticamente todos os consumidores usando compensações comprometidas com Kafka;
* Suporte configurável para deslocamentos confirmados pelo Zookeeper;
* Suporte configurável para deslocamentos confirmados pelo Storm;
* Endpoint HTTP para status do grupo de consumidores, bem como informações do corretor e do consumidor;
* Email configurável para envio de alertas para grupos específicos;
* Cliente HTTP configurável para envio de alertas para outro sistema para todos os grupos.

## Começando
### Pré-requisitos
Burrow foi escrito em Go, portanto, antes de começar, você deve [instalar e configurar o Go](https://golang.org/doc/install). Como as dependências são gerenciadas usando o módulo Go, a versão mais baixa do Go suportada é a 1.11, embora seja recomendável usar a versão 1.12 para desenvolvimento.

### Construir e instalar
```
$ Clone github.com/linkedin/Burrow to a directory outside of $GOPATH. Alternativamente, você pode exportar GO111MODULE=on para habilitar o módulo Go.
$ cd para o diretório de origem.
$ vá mod arrumado
$ vá instalar
```

### Executando o Burrow
```
$ $GOPATH/bin/Burrow --config-dir /path/containing/config
```

### Usando o Docker
Está disponível um arquivo Docker que constrói este projeto em cima de uma imagem Alpine Linux.
Para usá-lo, construa seu contêiner docker, monte sua configuração do Burrow em `/etc/burrow` e execute o docker.

Um [Docker Compose](docker-compose.yml) também está disponível para desenvolvimento rápido e fácil.

Instale o [Docker Compose](https://docs.docker.com/compose/) e depois:

1. Construir o contêiner docker:
   ```
   docker-compose build
   ```

2. Execute a pilha de composição do docker que inclui kafka e zookeeper:
   ```
   docker-compose down; docker-compose up
   ```

3. Alguns tópicos de teste já foram criados por padrão e Burrow pode ser acessado em `http://localhost:8000/v3/kafka`.


### Configuração
Para obter informações sobre como escrever seu arquivo de configuração, confira o [wiki detalhado](https://github.com/linkedin/Burrow/wiki)

## Licença
Copyright 2017 LinkedIn Corp. Licenciado sob a Licença Apache, Versão 2.0 (a "Licença"); você não pode usar este arquivo exceto em conformidade com a Licença.
Você pode obter uma cópia da Licença em http://www.apache.org/licenses/LICENSE-2.0

A menos que exigido pela lei aplicável ou acordado por escrito, o software distribuído sob a Licença é distribuído "COMO ESTÁ", SEM GARANTIAS OU CONDIÇÕES DE QUALQUER TIPO, expressas ou implícitas.
