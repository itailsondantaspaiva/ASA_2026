# 🚀 Guia Prático: Comandos Essenciais Git & Bash

Este documento serve como um guia de referência rápida para navegação no terminal (Bash) e gerenciamento de versão de código com o Git.

---

## 📂 1. Navegação e Arquivos (Terminal Bash)

Comandos básicos para navegar pelas pastas e visualizar arquivos no seu sistema operacional.

| Comando | O que faz | Exemplo de Aplicação |
| :--- | :--- | :--- |
| `pwd` | **Exibe o caminho atual**: Mostra em qual pasta você está no momento (*Print Working Directory*). | `pwd` |
| `ls` | **Lista conteúdo**: Lista arquivos e pastas do diretório atual. | `ls` |
| `ls -la` | **Lista detalhada e oculta**: Mostra arquivos ocultos e detalhes de permissões/tamanho. | `ls -la` |
| `cd <pasta>` | **Entra na pasta**: Navega para o diretório especificado. | `cd ProjetoAuditoria` |
| `cd ..` | **Volta uma pasta**: Retorna para a pasta pai (um nível acima). | `cd ..` |
| `mkdir <nome>` | **Cria pasta**: Cria um novo diretório na pasta atual. | `mkdir meu-novo-projeto` |
| `clear` | **Limpa a tela**: Apaga todo o histórico visível no terminal (ou use `Ctrl + L`). | `clear` |

---

## 🛠️ 2. Configuração e Inicialização (Git)

Comandos usados para preparar o ambiente Git no computador ou em um novo projeto.

> 💡 **Nota:** A configuração global precisa ser feita apenas uma vez por computador.

* **`git config --global user.name`**
  * **Para que serve:** Define o nome do autor das alterações no Git.
  * **Exemplo:** `git config --global user.name "Seu Nome"`

* **`git config --global user.email`**
  * **Para que serve:** Define o e-mail associado às suas contribuições e conta do GitHub.
  * **Exemplo:** `git config --global user.email "seu.email@exemplo.com"`

* **`git init`**
  * **Para que serve:** Inicializa um novo repositório Git no diretório atual (cria a pasta oculta `.git`).
  * **Exemplo:** `git init`

* **`git clone`**
  * **Para que serve:** Baixa um projeto existente no GitHub/GitLab para o seu computador.
  * **Exemplo:** `git clone https://github.com/usuario/nome-do-repositorio.git`

---

## 📝 3. Salvando Alterações Localmente (Git)

Fluxo diário de trabalho local: verificar status, preparar arquivos e registrar versões (*commits*).

* **`git status`**
  * **Para que serve:** Mostra o estado atual dos seus arquivos (modificados, novos ou prontos para commit).
  * **Exemplo:** `git status`

* **`git add .`**
  * **Para que serve:** Adiciona **todas** as alterações modificadas e novas à área de preparação (*Staging Area*).
  * **Exemplo:** `git add .` *(ou `git add nome-do-arquivo.py` para um arquivo específico)*

* **`git commit -m "mensagem"`**
  * **Para que serve:** Salva permanentemente a foto dos arquivos preparados no histórico com uma mensagem explicativa.
  * **Exemplo:** `git commit -m "feat: cria tela de login"`

* **`git log --oneline`**
  * **Para que serve:** Exibe um histórico simplificado de commits feitos no projeto.
  * **Exemplo:** `git log --oneline`

---

## ☁️ 4. Sincronização com Repositório Remoto (GitHub)

Conectando e trocando dados entre o seu computador local e a nuvem.

```bash
# Vincular projeto local a um repositório recém-criado no GitHub:
git branch -M main
git remote add origin https://github.com/usuario/nome-do-repositorio.git
git push -u origin main
```

### Detalhamento dos Comandos Remotos:

* **`git branch -M main`**
  * **Para que serve:** Renomeia o ramo principal atual para `main` (padrão atual do GitHub).

* **`git remote add origin <URL>`**
  * **Para que serve:** Associa o apelido `origin` ao link do seu repositório remoto.
  * **Exemplo:** `git remote add origin https://github.com/usuario/meu-projeto.git`

* **`git push`**
  * **Para que serve:** Envia seus commits locais para o servidor remoto.
  * **Exemplo:** `git push -u origin main` *(O parâmetro `-u` define o destino padrão para os próximos `git push`)*

* **`git pull`**
  * **Para que serve:** Baixa e aplica as alterações mais recentes do servidor remoto no seu projeto local.
  * **Exemplo:** `git pull`

---

## 🌿 5. Ramificações (Branches)

Utilizadas para criar recursos novos ou testar códigos sem afetar a versão principal (`main`).

* **`git branch`**
  * **Para que serve:** Lista todas as ramificações locais existentes.
  * **Exemplo:** `git branch`

* **`git switch -c <nome-da-branch>`**
  * **Para que serve:** Cria uma nova branch e alterna para ela imediatamente.
  * **Exemplo:** `git switch -c funcionalidade-filtro` *(Nota: em versões antigas do Git usava-se `git checkout -b`)*

* **`git switch <nome-da-branch>`**
  * **Para que serve:** Alterna para uma branch existente.
  * **Exemplo:** `git switch main`

---

## 🔄 Fluxo Básico de Trabalho Diário

```text
1. Editou o código no VS Code
2. git status          (Confere o que mudou)
3. git add .           (Prepara os arquivos)
4. git commit -m "..." (Salva a versão local)
5. git push            (Envia para o GitHub)
```