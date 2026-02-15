# 🚀 Automação de Onboarding: Criação de Usuários em Massa (Microsoft 365)

Este repositório contém um script em **PowerShell** desenvolvido para otimizar as rotinas da equipe de Suporte N1 e N2, automatizando a criação de novas contas corporativas no Microsoft 365 (Entra ID).

## 🎯 O Problema
Durante o processo de integração (Onboarding) de novos colaboradores, a criação manual de usuários no Centro de Administração do M365 consome muito tempo do analista de suporte e abre margem para falhas humanas (erros de digitação no e-mail, esquecimento de políticas de senha, etc).

## 💡 A Solução
Um script que consome uma planilha `.csv` padrão exportada pelo RH e provisiona dezenas de contas em poucos segundos, utilizando as melhores práticas e a API mais moderna da Microsoft.

## ⚙️ Funcionalidades Principais
* **Integração Moderna:** Utiliza o módulo oficial `Microsoft.Graph` (substituindo os antigos módulos AzureAD e MSOnline).
* **Validação de Dados:** Verifica automaticamente se a planilha possui as colunas necessárias antes de iniciar a execução.
* **Segurança de Credenciais:** Força a troca de senha no primeiro login (`ForceChangePasswordNextSignIn = $true`).
* **Tratamento Inteligente de Senhas:** Caso o RH deixe a senha em branco na planilha, o script gera automaticamente uma senha temporária forte que atende às políticas de complexidade do Entra ID.
* **Tratamento de Exceções (Try/Catch):** Se a criação de um usuário falhar, o script isola o erro, avisa no console e continua processando os demais funcionários da lista sem "quebrar".

## 📂 Estrutura dos Arquivos
* `criador de usários.ps1`: O script principal em PowerShell.
* `Exemplo-NovosUsuarios.csv`: Arquivo de exemplo demonstrando a formatação exigida pela automação.

## 🛠️ Como Utilizar
1. Clone este repositório.
2. Preencha o arquivo `Exemplo-NovosUsuarios.csv` com os dados dos novos colaboradores.
3. Abra o PowerShell como Administrador.
4. Execute o script. Será solicitada a autenticação com uma conta que possua privilégios de Administrador Global ou Administrador de Usuários no Microsoft 365.
