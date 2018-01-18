# Como criar um simples ambiente no AWS Elastic Beanstalk via API

## **Requesitos:**

- *AWS CLI* 
- *EB CLI*  
- *Access key e Security Key*
- *boto 3*

### **Passos:**

*Passo 1*

1 - Instalacao do AWS CLI [Clique Aqui](https://docs.aws.amazon.com/pt_br/cli/latest/userguide/installing.html)

2 - Instalacao do EB CLI [Clique Aqui](https://docs.aws.amazon.com/pt_br/elasticbeanstalk/latest/dg/eb-cli3-install.html)

3 - Acesso ao Access Key e Security Key [Clique Aqui](https://docs.aws.amazon.com/pt_br/elasticbeanstalk/latest/dg/eb-cli3-install.html)

4 - Instalacao e configuracao do boto3 [Clique Aqui](https://github.com/boto/boto3)


*Passo 2*

Verificando integracao com API via AWS CLI. 

```bash
aws ec2 describe-instances
```

A saida do comando acima deve ser um JSON semelhante ao conteudo abaixo, exemplo:

```json
"Instances": [
                {
                    "AmiLaunchIndex": 0,
                    "ImageId": "ami-ce792ab4",
                    "InstanceId": "i-0878c2890ebe57bbc",
                    "InstanceType": "t2.medium",
                    "KeyName": "pedro-devops",
                    "LaunchTime": "2018-01-17T12:49:48.000Z",
                    "Monitoring": {
                        "State": "disabled"
                    },
                    "Placement": {
                        "AvailabilityZone": "us-east-1a",
                        "GroupName": "",
                        "Tenancy": "default"},
                }
```

Passo 3 

_Neste passo vamos criar o nosso ambiente, para isso precisamos informar alguns parâmetros inicias como, região, nome da  aplicacao, plataforma e etc..._

```bash
eb init 
```
> Por padrão,  ao executar o comando sem nenhum parâmetro o  EB CLI solicita que você insira um valor para cada configuração, mas voce pode passar os parametros manualmente, conforme abaixo:

```bash
eb init nome_da_aplicacao --region us-east-1 -p "IIS 7.5"
```
> No exemplo acima, estamos passando o nome da aplicado, região e plataforma.

_apos as conficuracoes acima um arquivo **.elasticbeanstalk/config.yml** sera criado em seu diretorio local,onde constam tais configuracoes._ 

Passo 4

Criando ambiente e implantando o aplicativo.

```bash
eb create meu-aplicativo
```

> Da mesma forma do comando **eb init**, podemos passar os parametros nescessarios para criar a aplicacao.

```bash
eb create meu-aplicativo  --branch_default meu-aplicativo --cname meu-aplicativo-dev --elb-type network --region us-east-1 -p "IIS 7.5" --vpc.id vpc-1a670662 --vpc.ec2subnets subnet-44954c6b
```

> No exemplo acima, estou definindo o tipo de load balancer **_--elb-type network_**, região, plataforma vpc e subnet.











