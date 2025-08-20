# 🚀 Desafio IaC com Terraform + LocalStack

Este projeto provisiona uma infraestrutura **simulada da AWS** usando o [LocalStack](https://localstack.cloud/) e o [Terraform](https://www.terraform.io/).  

A stack contém:

- **VPC** com bloco CIDR `10.0.0.0/16`
- **Internet Gateway** para acesso à internet
- **Subnet Pública** (`10.0.1.0/24`)
- **Route Table** pública com rota `0.0.0.0/0`
- **Security Group** com ingress dinâmico liberando portas `22`, `80`, `443`
- **Instância EC2** (simulada) tipo `t3.medium`, com tag `ec2-iac-site`
- **Outputs**: ARN da instância, IP público, DNS público

> ⚠️ Importante: No LocalStack, instâncias EC2, IP público e DNS são **simulados**, servindo apenas para validar sua IaC sem custo na AWS real.

---

## 📦 Pré-requisitos

- [Docker](https://docs.docker.com/get-docker/)
- [Terraform](https://developer.hashicorp.com/terraform/downloads) (>= 1.4)
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
- Python + Pip (para instalar LocalStack/awslocal)

```bash
pip install localstack awscli-local[ver1]
