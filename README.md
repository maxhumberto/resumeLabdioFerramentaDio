# 🧪 Laboratório Completo – Ferramentas de Gerenciamento, Infraestrutura e Serviços no Azure

Este guia simula um **laboratório prático no portal do Azure**, cobrindo:

- [Ferramentas de Gerenciamento](#parte-1--ferramentas-de-gerenciamento)
- [Infraestrutura (Infrastructure)](#parte-2--infraestrutura-infrastructure)
- [Serviços (Services)](#parte-3--serviços-services)
- [Pré-requisitos](#pré-requisitos)
- [Comandos Azure CLI](#comandos-azure-cli)
- [Políticas (Azure Policy)](#azure-policy)
- [Automação (Azure Automation)](#azure-automation)
- [Template ARM](#deploy-via-arm-template)
- [Checklist Final](#checklist-final)

---

## PARTE 1 – Ferramentas de Gerenciamento

### 1. Configurando o Azure Dashboard
1. Acesse o [Portal do Azure](https://portal.azure.com) e faça login.  
2. No menu lateral → **Dashboard** → **+ Novo dashboard** → nome: `Lab-Gerenciamento` → **Salvar**.  
3. Clique **Editar** → arraste blocos como:
   - Métricas de VM  
   - Uso de CPU  
   - Status do armazenamento  
4. Ajuste tamanho/posição → **Concluir personalização**.  

### 2. Monitorando com Azure Monitor
- No menu lateral → **Monitor** →  
  - **Métricas** → adicionar gráfico de uso de CPU.  
  - **Logs** → rodar:

```kql
AzureActivity
| sort by TimeGenerated desc
Criar alerta: CPU > 80%, ação: enviar e-mail.

3. Organizando com Resource Manager (ARM)
Grupos de recursos → + Criar

Nome: Lab-Recursos

Região: Brazil South

💡 Criar via template: Implantações personalizadas → Criar modelo no editor → inserir JSON → Salvar.

4. Aplicando regras com Azure Policy
Vá em Policy → Definições → + Atribuir política

Escolher: Exigir tags em recursos

Escopo: Lab-Recursos.

5. Controlando gastos com Cost Management + Billing
Cost Management + Billing → Orçamentos → + Adicionar

Nome: Orçamento-Lab

Valor: 100

Alerta em 80%.

6. Recebendo recomendações com Azure Advisor
Advisor → ver recomendações de Custo, Segurança, Desempenho.

7. Acompanhando status com Service Health
Service Health → ver problemas e manutenções → criar alerta.

8. Automatizando com Azure Automation
Automation Accounts → + Criar → nome: Automation-Lab

Criar runbook PowerShell:

powershell
Copiar
Editar
Stop-AzVM -Name "MinhaVM" -ResourceGroupName "Lab-Recursos" -Force
Agendar para 23h.

PARTE 2 – Infraestrutura (Infrastructure)
2.1 Criar Rede Virtual
Redes virtuais → + Criar

Nome: VNet-Lab

Endereço CIDR: 10.0.0.0/16

Sub-rede: 10.0.1.0/24.

2.2 Criar Conta de Armazenamento
Contas de Armazenamento → + Criar

Nome: storagecontolab

Tipo: Standard LRS

Criar container imagens e enviar arquivo.

2.3 Criar Máquina Virtual
Máquinas Virtuais → + Criar

Nome: VM-Lab

Sistema: Windows Server ou Ubuntu

Tamanho: B2s

Rede: VNet-Lab.

PARTE 3 – Serviços (Services)
3.1 Criar Banco de Dados SQL
SQL Databases → + Criar

Nome: db-lab

Servidor: sqlserverlab

Local: Brazil South.

3.2 Criar App Service
App Services → + Criar

Nome: webapp-lab

Runtime: .NET ou Node.js.

3.3 Criar Azure Function
Function Apps → + Criar

Nome: func-lab

Runtime: Python

Plano: Consumption.

Pré-requisitos
Conta no Azure com permissões para criar recursos.

Azure CLI instalada.

Login:

bash
Copiar
Editar
az login
az account set --subscription "<SUBSCRIPTION_ID>"
Comandos Azure CLI
Inclui criação de Resource Group, VNet, Storage, VM, SQL Database, Web App e Function App.
📄 Ver comandos completos

Azure Policy
Exigir tags obrigatórias em recursos.
📄 Ver exemplo JSON

Azure Automation
Criar runbook PowerShell para desligar VM automaticamente.
📄 Ver script

Deploy via ARM Template
Exemplo mínimo criando Storage e VNet via template JSON.
📄 Ver template e comando CLI



5. Observações
Os recursos criados geram custos. 


