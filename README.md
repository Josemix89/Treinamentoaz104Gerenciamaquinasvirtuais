# Treinamentoaz104Gerenciamaquinasvirtuais
Gerenciamento e Criação de Máquinas Virtuais no Microsoft Azure
Guia Técnico Passo a Passo 
1 INTRODUÇÃO
A computação em nuvem revolucionou a forma como empresas disponibilizam infraestrutura de TI. O Microsoft Azure, plataforma de nuvem da Microsoft Azure, oferece recursos para criação, gerenciamento e monitoramento de máquinas virtuais (VMs), permitindo escalabilidade, alta disponibilidade e redução de custos operacionais.
Este documento apresenta um guia técnico detalhado para criação e gerenciamento de máquinas virtuais no Azure, incluindo boas práticas, documentação técnica, dicas profissionais e estrutura de projeto para publicação no GitHub.
________________________________________
2 OBJETIVO
Demonstrar:
•	Criação de máquinas virtuais no Azure; 
•	Configuração de rede; 
•	Controle de acesso; 
•	Gerenciamento de discos; 
•	Monitoramento; 
•	Boas práticas de segurança; 
________________________________________
3 PRÉ-REQUISITOS
3.1 Conta Microsoft Azure
Criar uma conta gratuita em:
Portal Microsoft Azure
________________________________________
3.2 Conhecimentos Necessários
•	Redes TCP/IP; 
•	Windows Server ou Linux; 
•	Conceitos de virtualização; 
•	Segurança da informação; 
•	SSH e RDP. 
________________________________________
4 CONCEITOS IMPORTANTES
4.1 Máquina Virtual (VM)
Uma VM é um computador virtualizado executado dentro da infraestrutura da nuvem Azure.
4.2 Resource Group
Grupo lógico utilizado para organizar recursos relacionados.
4.3 Virtual Network (VNET)
Rede virtual responsável pela comunicação entre recursos.
4.4 NSG (Network Security Group)
Firewall utilizado para controlar tráfego de entrada e saída.
________________________________________
5 CRIAÇÃO DE MÁQUINA VIRTUAL WINDOWS SERVER
5.1 Acessar o Portal Azure
1.	Abrir o portal:
Portal Azure
2.	Efetuar login. 
________________________________________
5.2 Criar Resource Group
Passos
1.	Pesquisar:
"Resource Groups" 
2.	Clicar:
"Create" 
3.	Informar: 
o	Subscription 
o	Nome do grupo 
o	Região 
Exemplo
RG-LAB-INFRAESTRUTURA
Brazil South
________________________________________
5.3 Criar Máquina Virtual
Passos
1.	Pesquisar:
"Virtual Machines" 
2.	Clicar:
"Create" 
3.	Selecionar:
"Azure Virtual Machine" 
________________________________________
5.4 Configurações Básicas
Informações principais
Subscription: Azure Subscription
Resource Group: RG-LAB-INFRAESTRUTURA
Virtual Machine Name: VM-WINDOWS-01
Region: Brazil South
Availability Options: No Infrastructure Redundancy
Security Type: Standard
Image: Windows Server 2022
Size: Standard B2s
Username: administrador
Password: ********
________________________________________
5.5 Liberar Acesso RDP
Marcar:
Allow selected ports
RDP (3389)
________________________________________
5.6 Configurar Disco
Recomendado
Premium SSD
Para ambientes de produção.
________________________________________
5.7 Configurar Rede
Configurações
Virtual Network: VNET-INFRA
Subnet: SUBNET-SERVERS
Public IP: ENABLED
NIC NSG: BASIC
________________________________________
5.8 Revisar e Criar
1.	Validar configurações; 
2.	Clicar:
"Create"; 
3.	Aguardar deployment. 
________________________________________
6 ACESSO À MÁQUINA VIRTUAL
6.1 Conexão RDP
1.	Abrir VM; 
2.	Clicar:
"Connect"; 
3.	Selecionar:
"RDP"; 
4.	Baixar arquivo RDP; 
5.	Conectar utilizando usuário e senha. 
________________________________________
7 CRIAÇÃO DE VM LINUX
7.1 Selecionar Imagem
Ubuntu Server 22.04 LTS
________________________________________
7.2 Autenticação SSH
Gerar chave SSH
No PowerShell:
ssh-keygen
________________________________________
7.3 Liberar Porta SSH
TCP 22
________________________________________
7.4 Conectar via SSH
ssh azureuser@IPPUBLICO
________________________________________
8 GERENCIAMENTO DE MÁQUINAS VIRTUAIS
8.1 Start e Stop
Opções disponíveis
•	Start 
•	Restart 
•	Stop 
•	Deallocate 
________________________________________
8.2 Redimensionamento de VM
Passos
1.	Abrir VM; 
2.	Selecionar:
"Size"; 
3.	Escolher novo tamanho; 
4.	Aplicar. 
________________________________________
8.3 Snapshot
Criar Snapshot
1.	Disks; 
2.	Selecionar disco; 
3.	Create Snapshot. 
________________________________________
8.4 Backup
Utilizar:
Azure Backup
Recovery Services Vault
________________________________________
9 MONITORAMENTO
9.1 Azure Monitor
Ferramenta para:
•	CPU; 
•	Memória; 
•	Disco; 
•	Rede; 
•	Alertas. 
________________________________________
9.2 Log Analytics
Centraliza logs da infraestrutura.
________________________________________
10 SEGURANÇA
10.1 Boas Práticas
Recomendações
•	Não liberar RDP para internet; 
•	Utilizar VPN; 
•	Implementar MFA; 
•	Utilizar Bastion; 
•	Aplicar patches; 
•	Utilizar Defender for Cloud. 
________________________________________
10.2 Azure Bastion
Permite acesso seguro sem IP público.
________________________________________
11 DICAS E MACETES PROFISSIONAIS
11.1 Economia de Custos
Desligar VMs
Stop + Deallocate
Evita cobrança de processamento.
________________________________________
11.2 Tags
Utilizar tags para organização:
Environment=Production
Owner=Infraestrutura
CostCenter=TI
________________________________________
11.3 Naming Convention
Padronizar nomes:
VM-PRD-AD01
VM-HML-WEB01
VM-DEV-LINUX01
________________________________________
11.4 Template ARM
Automatizar criação utilizando:
•	ARM Template; 
•	Bicep; 
•	Terraform. 
