# 🐳 Docker + Prometheus + Grafana Monitoring

[![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![Docker Compose](https://img.shields.io/badge/Docker%20Compose-2496ED?logo=docker&logoColor=white)](https://docs.docker.com/compose/)
[![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?logo=prometheus&logoColor=white)](https://prometheus.io/)
[![Grafana](https://img.shields.io/badge/Grafana-F46800?logo=grafana&logoColor=white)](https://grafana.com/)
[![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white)](https://nginx.org/)
[![Blackbox Exporter](https://img.shields.io/badge/Blackbox%20Exporter-000000?logo=prometheus&logoColor=white)](https://github.com/prometheus/blackbox_exporter)

Projeto de monitoramento de uma aplicação web executando em **container Docker**, utilizando **Prometheus** e **Grafana** para coleta, consulta e visualização de métricas.

---

## 🎯 Objetivo

Este laboratório foi desenvolvido com o objetivo de praticar conceitos de:

* Containers Docker
* Docker Compose
* Monitoramento de aplicações
* Prometheus
* Grafana
* Exporters
* Métricas HTTP
* Health check
* Persistência de dados
* Observabilidade básica

A ideia principal é construir um ambiente simples no qual uma aplicação Nginx seja monitorada e suas informações possam ser visualizadas através de um dashboard no Grafana.

---

## 🛠️ Tecnologias utilizadas

| Tecnologia                | Função                               |
| ------------------------- | ------------------------------------ |
| Docker                    | Containerização dos serviços         |
| Docker Compose            | Orquestração dos containers          |
| Nginx                     | Aplicação web monitorada             |
| Nginx Prometheus Exporter | Exportação das métricas do Nginx     |
| Blackbox Exporter         | Verificação da disponibilidade HTTP  |
| Prometheus                | Coleta e armazenamento das métricas  |
| Grafana                   | Visualização e criação de dashboards |

---

## 📁 Estrutura do projeto

```text
docker-grafana-monitoring/
│
├── compose.yml
│
├── nginx/
│   ├── index.html
│   └── nginx.conf
│
├── prometheus/
│   └── prometheus.yml
│
└── grafana/
```

---

## 📄 Arquivos principais

### `docker-compose.yml`

Define todos os serviços utilizados no laboratório:

* Nginx
* Nginx Exporter
* Blackbox Exporter
* Prometheus
* Grafana

Também define os volumes utilizados para persistência dos dados do Prometheus e Grafana.

---

### `nginx/nginx.conf`

Arquivo responsável pela configuração do Nginx.

Além da aplicação web, foi configurado o endpoint:

```text
/stub_status
```

Esse endpoint fornece informações básicas sobre as conexões do Nginx para que o Nginx Exporter possa coletá-las.

---

### `nginx/index.html`

Página HTML utilizada como aplicação web de teste.

Exibe uma página simples indicando que o Nginx está sendo executado em um container Docker.

---

### `prometheus/prometheus.yml`

Arquivo responsável pela configuração do Prometheus.

Nele são definidos os targets que serão monitorados:

```text
Prometheus
Nginx Exporter
Blackbox Exporter
```

Também foi configurado o intervalo global de coleta:

```yaml
scrape_interval: 5s
```

Isso faz com que o Prometheus consulte os targets a cada 5 segundos.

---

# 🚀 Como executar o projeto

## 1. Pré-requisitos

É necessário possuir:

* Docker
* Docker Compose
* Git

Verifique a instalação:

```powershell
docker --version
```

```powershell
docker compose version
```

---

## 2. Clonar o repositório

```powershell
git clone https://github.com/wendlersilva/docker-grafana-monitoring
```

Entre no diretório:

```powershell
cd docker-grafana-monitoring
```

---

## 3. Iniciar os containers

Execute:

```powershell
docker compose up -d
```

O Docker Compose irá criar e iniciar os serviços definidos no projeto.

Para verificar os containers:

```powershell
docker compose ps
```

Os principais serviços serão:

```text
nginx
nginx-exporter
blackbox-exporter
prometheus
grafana
```

---

# 🌐 Acessando os serviços

Após iniciar o ambiente, os serviços podem ser acessados localmente.

### Nginx

```text
http://localhost:8080
```

Página web da aplicação.

---

### Nginx Status

```text
http://localhost:8080/stub_status
```

Endpoint utilizado pelo Nginx Exporter.

---

### Nginx Exporter

```text
http://localhost:9113/metrics
```

Endpoint que disponibiliza as métricas do Nginx no formato Prometheus.

---

### Prometheus

```text
http://localhost:9090
```

Interface web para consultar as métricas coletadas.

---

### Grafana

```text
http://localhost:3000
```

Interface utilizada para criação e visualização dos dashboards.

---

## 🧰 Tecnologias

```text
Docker
Docker Compose
Nginx
Prometheus
Grafana
Nginx Prometheus Exporter
Blackbox Exporter
```

---

⭐ Projeto desenvolvido para fins de estudo e portfólio.
