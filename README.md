# Como criar um ambiente no AWS Elastic Beanstalk via API

**Requesitos:**

- *AWS CLI* 
- *EB CLI*  
- *Access key e Security Key*
- *boto 3*

**Passos:**

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
