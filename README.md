# n8n Self-Hosted Lab

Este projeto é um laboratório self-hosted de automação com `n8n` e `Docker Compose`.
A ideia é ter um ambiente simples, reproduzível e seguro para estudar:

- Docker
- n8n
- AWS no futuro
- GitHub Actions no futuro
- automações e agentes de IA

## Objetivo do projeto

O objetivo deste repositório é servir como base para um ambiente online/local de automação,
permitindo estudar operação de containers, persistência de dados, CI/CD e futuros deploys em AWS.

Este é um laboratório prático, não uma aplicação de produção pronta.

## Arquitetura inicial

A arquitetura inicial foi mantida propositalmente simples:

- `Docker Compose` para orquestração local
- imagem oficial `n8nio/n8n`
- persistência via volume montado em `./data`
- SQLite local como banco padrão do n8n

Isso facilita subir o ambiente rapidamente e entender a relação entre container, volume e dados persistidos.

## Estrutura do projeto

```text
.
├── docker-compose.yml
├── README.md
├── .gitignore
├── data/
└── data_backup/
```

- `docker-compose.yml`: define o serviço do n8n
- `data/`: diretório de runtime e persistência do n8n
- `data_backup/`: cópia/backup local para estudo ou recuperação

## Como executar localmente

### Pré-requisitos

- Docker instalado
- Docker Compose disponível no sistema

### Subir o ambiente

```bash
docker compose up -d
```

### Parar o ambiente

```bash
docker compose down
```

### Ver logs

```bash
docker compose logs -f
```

## Como acessar

Depois de subir o container, acesse:

```text
http://localhost:5678
```

## Segurança

Este projeto foi pensado para evitar exposição de dados sensíveis no GitHub.

- `database.sqlite` não deve ser versionado
- tokens, credenciais e senhas não devem ir para o GitHub
- a pasta `data/` é runtime e persistência local, não código-fonte

Se houver necessidade de variáveis sensíveis no futuro, elas devem ficar em arquivos `.env`
fora do controle de versão ou em um mecanismo seguro de secrets.

## Roadmap futuro

Evoluções planejadas para este laboratório:

- AWS EC2
- HTTPS
- GitHub Actions
- deploy automatizado
- agentes de IA
- integrações com GitHub, Azure DevOps e Bitbucket

## Observações

O foco desta base é manter o ambiente simples, reproduzível e fácil de entender.
A persistência foi preservada e o `docker-compose.yml` atual não foi alterado além do necessário.
