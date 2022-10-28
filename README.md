[![Join the chat at https://gitter.im/linkedin-Burrow/Lobby](https://badges.gitter.im/linkedin-Burrow/Lobby.svg)](https://gitter.im/linkedin-Burrow/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Build Status](https://travis-ci.org/linkedin/Burrow.svg)](https://travis-ci.org/linkedin/Burrow)
[![go report card](https://goreportcard.com/badge/github.com/linkedin/Burrow)](https://goreportcard.com/report/github.com/linkedin/Burrow)
[![Coverage Status](https://coveralls.io/repos/github/linkedin/Burrow/badge.svg?branch=master)](https://coveralls.io/github/linkedin/Burrow?branch=master)
[![GoDoc](https://godoc.org/github.com/linkedin/Burrow?status.svg)](https://godoc.org/github.com/linkedin/Burrow)

# Burrow - Verificação de atraso do consumidor Kafka

Burrow é um companheiro de monitoramento do [Apache Kafka](http://kafka.apache.org) que fornece verificação de atraso do consumidor como um serviço sem a necessidade de especificar limites. Ele monitora as compensações comprometidas para todos os consumidores e calcula o status desses consumidores sob demanda. Um endpoint HTTP é fornecido para solicitar o status sob demanda, bem como fornecer outras informações do cluster Kafka. Há também notificadores configuráveis que podem enviar status via e-mail ou chamadas HTTP para outro serviço.

## recursos
* SEM LIMITES! Os grupos são avaliados em uma janela deslizante;
* Suporte a vários clusters Kafka;
* Monitora automaticamente todos os consumidores usando compensações comprometidas com Kafka;
* Suporte configurável para deslocamentos confirmados pelo Zookeeper;
* Configurable support for Storm-committed offsets
* HTTP endpoint for consumer group status, as well as broker and consumer information
* Configurable emailer for sending alerts for specific groups
* Configurable HTTP client for sending alerts to another system for all groups

## Getting Started
### Prerequisites
Burrow is written in Go, so before you get started, you should [install and set up Go](https://golang.org/doc/install). As the dependencies
are managed using Go module, the lowest version of Go supported is 1.11, though we recommend using version 1.12 for development.

### Build and Install
```
$ Clone github.com/linkedin/Burrow to a directory outside of $GOPATH. Alternatively, you can export GO111MODULE=on to enable Go module.
$ cd to the source directory.
$ go mod tidy
$ go install
```

### Running Burrow
```
$ $GOPATH/bin/Burrow --config-dir /path/containing/config
```

### Using Docker
A Docker file is available which builds this project on top of an Alpine Linux image.
To use it, build your docker container, mount your Burrow configuration into `/etc/burrow` and run docker.

A [Docker Compose](docker-compose.yml) is also available for quick and easy development.

Install [Docker Compose](https://docs.docker.com/compose/) and then:

1. Build the docker container:
   ```
   docker-compose build
   ```

2. Run the docker compose stack which includes kafka and zookeeper:
   ```
   docker-compose down; docker-compose up
   ```

3. Some test topics have already been created by default and Burrow can be accessed on `http://localhost:8000/v3/kafka`.


### Configuration
For information on how to write your configuration file, check out the [detailed wiki](https://github.com/linkedin/Burrow/wiki)

## License
Copyright 2017 LinkedIn Corp. Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License.
You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR
CONDITIONS OF ANY KIND, either express or implied.
