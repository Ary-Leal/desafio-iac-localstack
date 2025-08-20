# 🚀 Desafio IaC com Terraform + LocalStack

[![Terraform](https://img.shields.io/badge/Terraform-v1.5+-purple?logo=terraform)](https://www.terraform.io/)
[![LocalStack](https://img.shields.io/badge/LocalStack-Latest-orange?logo=docker)](https://localstack.cloud/)
[![AWS](https://img.shields.io/badge/AWS-Simulado-232F3E?logo=amazonaws)](https://aws.amazon.com/)

Este projeto tem como objetivo **provisionar uma infraestrutura simulada da AWS** utilizando [Terraform](https://www.terraform.io/) e [LocalStack](https://localstack.cloud/).  

A proposta é oferecer um **laboratório local de Infraestrutura como Código (IaC)** para praticar a criação de recursos AWS sem custos em nuvem real, ideal para estudos, experimentação e testes de pipelines CI/CD.

---

## 📐 Arquitetura Provisionada

A stack criada pelo Terraform contém:

- **VPC** com bloco CIDR `10.0.0.0/16`
- **Internet Gateway** para acesso externo
- **Subnet Pública** (`10.0.1.0/24`)
- **Route Table** associada à subnet com rota padrão `0.0.0.0/0`
- **Security Group** com ingress dinâmico liberando portas:
  - `22` (SSH)
  - `80` (HTTP)
  - `443` (HTTPS)
- **Instância EC2 (simulada)** tipo `t3.medium`, com tag `ec2-iac-site`
- **Outputs** exportados:
  - ARN da instância
  - IP público
  - DNS público

> ⚠️ **Atenção**: No LocalStack, recursos como EC2, IP público e DNS são **apenas simulados**. Eles não permitem tráfego real, servindo apenas para validação da IaC.

---

## 🛠️ Tecnologias Utilizadas

- **Terraform** → Provisionamento da infraestrutura (IaC).
- **LocalStack** → Simulação dos serviços da AWS localmente.
- **Docker & Docker Compose** → Execução do LocalStack.
- **AWS CLI / awslocal** → Validação e consulta dos recursos provisionados.

---

## 📦 Pré-requisitos

- [Docker](https://docs.docker.com/get-docker/) + [Docker Compose](https://docs.docker.com/compose/)
- [Terraform](https://developer.hashicorp.com/terraform/downloads) >= 1.4
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
- Python + Pip (para instalar LocalStack e utilitário `awslocal`):
  ```bash
  pip install localstack awscli-local[ver1]
