# Processo Passo a Passo

## Instalando o Terraform CLI

##### 1. Abra o powershell como admin

##### 2. Navegue até uma pasta de sua escolha

##### 3. Rode o comando para baixar o zip do terraform

```
Invoke-WebRequest -Uri https://releases.hashicorp.com/terraform/1.0.11/terraform_1.0.11_windows_amd64.zip -OutFile terraform.zip
```

##### 4. Rode o comando para descompactar o arquivo zip

```
Expand-Archive -Path terraform.zip -DestinationPath C:\terraform
```

##### 5. Rode o comando para salvar o terraform no path do sistema

```
[System.Environment]::SetEnvironmentVariable('PATH', $env:PATH + ';C:\terraform', [System.EnvironmentVariableTarget]::Machine)
```

##### 6. Rode o comando em um novo terminal para verificar se o terraform CLI foi instalado corretamente

```
terraform -v
```

##### 7. Remova o arquivo .zip baixado na etapa 3 (Opcional)

## Instalando AWS CLI

##### 1. Abra o powershell como admin

##### 2. Rode o comando para baixar o instalador do AWS CLI

```
Invoke-WebRequest -Uri https://awscli.amazonaws.com/AWSCLIV2.msi -OutFile AWSCLIV2.msi
```

##### 3. Rode o comando para instalar o AWS CLI

```
Start-Process msiexec.exe -Wait -ArgumentList '/I AWSCLIV2.msi /quiet'
```

##### 4. Rode o comando em um novo terminal para verificar se a AWS CLI foi instalada corretamente

```
aws --version
```

## Configurando a AWS

##### 1. Abra a AWS Academy no navegador

```
https://awsacademy.instructure.com/
```

##### 2. Abra o learn lab, em:

```
Curso > Módulos > Iniciar os laboratórios de aprendizagem da AWS Academy
```

##### 3. Clique em start lab no canto superior

##### 4. Abra o AWS Details e marque para mostrar o AWS CLI

##### 5. Rode o comando para configurar as credenciais da aws

```
aws configure
```

##### 6. Preencha cada uma das infos solicitadas pela etapa anterior com as credenciais do AWS Academy que são obtidas na AWS CLI details

```
AWS Access Key ID [None]: 'aws_access_key_id'
AWS Secret Access Key [None]: 'aws_secret_access_key'
Default region name [None]: 'Region'
Default output format [None]: 'json'
```

##### 7. Rode os seguintes comandos para abrir as credenciais recem armazenadas

```
cd ~\.aws\
notepad credentials
```

##### 8. Adicione uma nova linha com o token de sessão da AWS CLI details

```
aws_session_token = 'aws_session_token'
```

PS: A região é mostrada no final da página de detalhes da AWS, normalmente é us-east-1

## Criando a EC2 com Terraform

##### 1. Na pasta desejada do projeto, crie um arquivo main.tf e insira nele o seguinte código

```
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c02fb55956c7d316"  # Amazon Linux 2 AMI (HVM), SSD Volume Type
  instance_type = "t2.micro"

  tags = {
    Name = "TerraformExample"
  }
}
```

PS: se sua região for diferente da apresentada, altere-a no código acima

##### 2. Rode o comando para preparar o Terraform

```
terraform init
```

##### 3. Rode o comando para definir o que será executado pelo Terraform, será necessário confirmar com "yes"

```
terraform plan
```

##### 4. Rode o comando para aplicar a execução que foi planejada, será necessário confirmar com "yes"

```
terraform apply
```

## Removendo as infras criadas (Extra)

##### 1. Rode o comando para destruir o que foi criado, será necessário confirmar com "yes"

```
terraform destroy
```

Veja a página <a href="/screenshots">Screenshots</a> para acompanhar as imagens das execuções
