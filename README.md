# configEc2
 volume ebs

# Exercício de Configuração e Gerenciamento de Instância EC2

## Objetivo

Este exercício tem como objetivo configurar uma instância EC2 na AWS, conectar-se a ela via SSH, gerenciar o armazenamento EBS, formatar e montar o volume, e verificar os recursos.

## Passos Executados

### 1. Configuração da Instância EC2

1. **Acesso ao Console da AWS:**
   - Acesse o [Console de Gerenciamento da AWS](https://aws.amazon.com/console/).

2. **Navegar até o Serviço EC2:**
   - No painel de serviços, clique em "EC2".

3. **Criar uma Nova Instância EC2:**
   - Clique em "Launch Instance" para iniciar a criação de uma nova instância.
   - Selecione a AMI "Amazon Linux 2".

4. **Escolher o Tipo de Instância:**
   - Escolha o tipo de instância de acordo com as necessidades (por exemplo, `t2.micro`).

5. **Configurar as Opções da Instância:**
   - Defina a rede, o grupo de segurança e o armazenamento conforme necessário.

6. **Configurar um Par de Chaves:**
   - Selecione ou crie um par de chaves para acesso SSH.

7. **Lançar a Instância:**
   - Revise e lance a instância.

### 2. Conexão via SSH

1. **Obter o Endereço IP Público:**
   - No Console EC2, localize o endereço IP público ou DNS público da instância.

2. **Conectar via SSH:**
   - Use o comando:
     ```bash
     ssh -i /caminho/para/sua-chave.pem ec2-user@IP-OU-DNS-PUBLICO
     ```
   - Substitua `/caminho/para/sua-chave.pem` e `IP-OU-DNS-PUBLICO` pelos valores corretos.

### 3. Gerenciamento do Armazenamento

1. **Explorar Opções de Armazenamento:**
   - No Console da AWS, vá para "Volumes" em EC2.

2. **Criar um Novo Volume EBS:**
   - Clique em "Create Volume", selecione o tipo e tamanho do volume.

3. **Anexar o Volume à Instância:**
   - Clique no volume, selecione "Actions" > "Attach Volume", escolha a instância e defina o dispositivo.

### 4. Formatando e Montando o Volume

1. **Criar um Ponto de Montagem:**
   - Na instância EC2, execute:
     ```bash
     sudo mkdir /mnt/novovolume
     ```

2. **Formatar o Volume:**
   - Execute:
     ```bash
     sudo mkfs -t ext4 /dev/xvdf
     ```

3. **Montar o Volume:**
   - Execute:
     ```bash
     sudo mount /dev/xvdf /mnt/novovolume
     ```

### 5. Criação de Arquivos

1. **Criar um Arquivo de Texto no Volume Montado:**
   - Execute:
     ```bash
     echo "Este é um arquivo de teste." | sudo tee /mnt/novovolume/arquivo_teste.txt
     ```

2. **Verificar o Conteúdo do Arquivo:**
   - Execute:
     ```bash
     cat /mnt/novovolume/arquivo_teste.txt
     ```

### 6. Explorando Recursos

1. **Verificar o Volume Montado:**
   - Execute:
     ```bash
     ls /mnt/novovolume
     df -h
     mount | grep /mnt/novovolume
     ```

2. **Captura de Tela:**
   - Tire um print dos comandos e resultados do terminal para avaliação.

### 7. Encerramento da Instância

1. **Encerrar ou Parar a Instância:**
   - No Console da AWS, vá para "Instances", selecione a instância e escolha "Instance State" > "Stop" ou "Terminate".

## Observações

- Certifique-se de que o volume EBS e a instância EC2 estejam na mesma Zona de Disponibilidade.
- Verifique as permissões e o estado da instância se encontrar problemas ao anexar o volume.



