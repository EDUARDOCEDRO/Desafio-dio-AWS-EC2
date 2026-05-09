# Desafio-dio-AWS-EC2

# ☁️ Gerenciamento de Instâncias EC2 na AWS

Repositório criado como entregável do desafio prático da [DIO](https://www.dio.me/).

---

## O que é o Amazon EC2?

O **EC2 (Elastic Compute Cloud)** é o serviço da AWS que permite criar servidores virtuais na nuvem. Em vez de comprar um computador físico, você aluga um servidor e paga apenas pelo tempo que usar.

---

## Conceitos que aprendi

**AMI** — É o "modelo" do servidor. Define o sistema operacional (ex: Ubuntu, Amazon Linux). É como escolher qual sistema operacional instalar.

**Tipo de instância** — Define o tamanho do servidor: quantidade de CPUs e memória RAM. Ex: `t2.micro` é o menor, ideal para estudos e elegível no Free Tier.

**Key Pair** — Par de chaves para acessar o servidor via SSH. A chave privada (arquivo `.pem`) é gerada uma única vez — é importante guardar esse arquivo!

**Security Group** — Funciona como um firewall. Define quais portas e IPs podem acessar a instância. Ex: liberar a porta 22 para SSH e a porta 80 para HTTP.

**Elastic IP** — Um IP público fixo. Sem ele, o IP da instância muda toda vez que ela é reiniciada.

---

## Como criar uma instância EC2 (passo a passo)

1. Acesse o Console AWS → EC2 → **Launch Instance**
2. Dê um nome para a instância
3. Escolha a AMI (ex: Amazon Linux 2023)
4. Escolha o tipo (ex: `t2.micro` — Free Tier)
5. Crie ou selecione um **Key Pair** e baixe o arquivo `.pem`
6. Configure o **Security Group** (libere as portas necessárias)
7. Clique em **Launch Instance** e aguarde o status `Running`

---

## Como conectar via SSH

```bash
# Ajustar permissão do arquivo de chave
chmod 400 minha-chave.pem

# Conectar à instância
ssh -i "minha-chave.pem" ec2-user@<ip-da-instancia>
```

> No Ubuntu, o usuário é `ubuntu` em vez de `ec2-user`.

---

## Dicas importantes

- **Parar ≠ Terminar** — Parar preserva a instância. Terminar a apaga para sempre.
- **Free Tier** — O `t2.micro` tem 750 horas/mês gratuitas no primeiro ano.
- **Sempre pare as instâncias** quando não estiver usando, para evitar cobranças.
- **Nunca compartilhe** o arquivo `.pem` nem suas credenciais AWS.

---

## O que aprendi com esse desafio

- Como navegar no Console da AWS e criar recursos
- A diferença entre parar e terminar uma instância
- A importância dos Security Groups para segurança
- Como o modelo de cobrança por demanda funciona na prática

---

## Recursos úteis

- [Documentação do EC2](https://docs.aws.amazon.com/pt_br/ec2/index.html)
- [AWS Free Tier](https://aws.amazon.com/pt/free/)

)
