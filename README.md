# desafio dio - administração no microsoft azure

este repositório reúne tópicos sobre administração do ms azure, baseados nos conteúdos abordados durante os laboratório práticos do curso; sendo requisito para finalização do módulo 8.
o objetivo é servir como material de apoio para estudos e futuras implantações.


## ☁️ conteúdos abordados

### 1. administração de identidade
- uso do *azure active directory (azure ad)* para autenticação e autorização  
- criação e gerenciamento de usuários, grupos e funções (rbac)  
- identidade híbrida com ad local  
- autenticação multifator (mfa)  

exemplo de comando (cli):
```bash
az ad user create --display-name "usuario teste" --user-principal-name user@dominio.com --password SenhaSegura
```
<br>

### 2. administração de governança e conformidade
- uso de management groups, subscriptions e resource groups
- aplicação de políticas com azure policy
- controle de acesso baseado em função (rbac)
- monitoramento de conformidade com azure blueprints

exemplo de comando (powershell):
```powershell
New-AzPolicyAssignment -Name "BloquearLocalizacao" -Scope "/subscriptions/xxxx" -PolicyDefinition "BloquearLocalizacaoForaBR"
```
<br>

### 3. administração dos recursos do azure
- criação de recursos via portal, cli ou powershell
- uso de azure resource manager (arm) para automação
- organização por tags para custos e relatórios
- monitoramento com azure monitor

exemplo de comando (cli):
```bash
az group create --name grupo-teste --location brazilsouth
```
<br>

### 4. administração de rede virtual
- conceito de virtual network (vnet)
- sub-redes e grupos de segurança (nsg)
- integração de serviços dentro da rede
- emparelhamento de vnets (vnet peering)

exemplo de comando (cli):

```bash
az network vnet create --name vnet-teste --resource-group grupo-teste --address-prefix 10.0.0.0/16
```
<br>

### 5. administração de conectividade entre sites

- vpn gateway para conectar rede privada on-premises ao azure
- expressroute para conexões privadas, fazendo uma espécide de _bypass_ particular
- vpn site-to-site e point-to-site
- conceitos redundância e alta disponibilidade

exemplo de comando (cli):

```bash
az network vpn-gateway create --name vpn-teste --resource-group grupo-teste --vnet vnet-teste
```
<br>

### 6. administração do tráfego de rede

- balanceamento de carga com azure load balancer e application gateway
- distribuição global com azure front door
- resolução de nomes com azure dns
- proteção com azure ddos protection

exemplo de comando (cli):

```bash
az network lb create --resource-group grupo-teste --name lb-teste --sku Standard
```
<br>

### 7. administração do armazenamento do azure

- tipos de armazenamento: blob, file, table e queue
- replicação: lrs, zrs, grs, ra-grs (read only)
- controle de acesso com SAS tokens (melhor prática para acessos externos)
- políticas de ciclo de vida

exemplo de comando (cli):

```bash
az storage account create --name armazenamentoteste --resource-group grupo-teste --location brazilsouth --sku Standard_LRS
```
<br>

### 8. administração de máquinas virtuais do azure

- criação e configuração de vms
- imagens pré-configuradas ou personalizadas
- conjuntos de disponibilidade
- escalabilidade com vm scale sets, escaliabildade vertical x horizontal
- dominíos de falha e atualização
- backup e update management

exemplo de comando (cli):

```bash
az vm create --resource-group grupo-teste --name vm-teste --image UbuntuLTS --admin-username azureuser --generate-ssh-keys
```
<br>

### 9. administração do serviço de app services

- criação e configuração de aplicações em **paas** (platform as a service)  
- escolha de planos: **basic, standard, premium, isolated** conforme necessidade de escala e performance  
- relação: **app service plan** → agrupa os recursos de compute, onde os **app services** são executados  
- escalabilidade:  
  - **scale up**: upgrade de sku (mudança de plano)  
  - **scale out**: aumento de instâncias para atender maior demanda  
- integração com **azure container instances (aci)** e **azure kubernetes services (aks)** para orquestração de containers  
- uso de **deployment slots** (staging, production, etc.) com **swap** sem causar indisponibilidade  
- configuração de rotinas de **backup** dos apps  
- hospedagem de web apps com domínio padrão **azurewebsites.net**  
- suporte a **continuous deployment** via github, bitbucket, azure repos, git local e docker hub  

exemplo de comando (cli):
```bash
az webapp create --resource-group grupo-teste --plan appserviceplan-teste --name meuapp --runtime "DOTNET|6.0"
```
<br>

### 10. configuração de proteção de dados

- configuração de backup de arquivos e pastas no azure
- configuração de backup de máquinas virtuais
- uso do backup center para business continuity e validação do status de backup
- utilização de recovery services vault para workloads locais e em nuvem
- uso do mars agent (microsoft azure recovery services) para backup em ambientes on-premises
- suporte a replicação e restauração granular

exemplo de comando (cli):

```bash
az backup protection enable-for-vm --resource-group grupo-teste --vault-name vault-teste --vm vm-teste
```
<br>

### 11. administração de monitoramento

- utilização do azure monitor para métricas e logs em tempo real
- configuração de alertas baseados em métricas (cpu, memória, disponibilidade) e em logs (atividade, auditoria)
- criação de grupos de ação para enviar notificações via e-mail, sms, webhook, logic apps, automation runbooks etc.
- integração com application insights para monitorar aplicações em tempo real (requisições, falhas, dependências)
- uso de log analytics workspace para centralizar consultas e relatórios personalizados
- visualizações e dashboards no azure portal e integração com power bi
- diagnóstico de redes com network watcher (topologia, latência, conexões)
- acompanhamento de conformidade e segurança com microsoft defender for cloud

exemplo de comando (cli):

```bash
az monitor metrics list --resource vm-teste --metric "Percentage CPU"
```
