# Criação EC2 com Terraform

## Instalando o terraform

1. Abra o powershell como admin

2. Navegue até uma pasta de sua escolha

3. Rode o comando `Invoke-WebRequest -Uri https://releases.hashicorp.com/terraform/1.0.11/terraform_1.0.11_windows_amd64.zip -OutFile terraform.zip` para baixar o zip do terraform

4. Rode o comando `Expand-Archive -Path terraform.zip -DestinationPath C:\terraform` para descompactar o arquivo zip

5. Rode o comando `[System.Environment]::SetEnvironmentVariable('PATH', $env:PATH + ';C:\terraform', [System.EnvironmentVariableTarget]::Machine)` para salvar o terraform no path do sistema

6. Remova o arquivo .zip baixado na etapa 3 (Opcional)
