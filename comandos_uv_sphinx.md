# 📚 Guia Prático: Automação e Documentação com UV e Sphinx

Este guia detalha os comandos para a criação, gerenciamento de dependências e construção de páginas de documentação Python utilizando **`uv`** (gerenciador de projetos ultra-rápido) e **`Sphinx`**.

---

## ⚙️ Pré-requisito Principal: O que instalar primeiro?

Antes de usar os comandos `uv`, você precisa ter a ferramenta **`uv`** instalada no seu sistema operacional.

* **Instalar o `uv` no Windows (PowerShell):**
  ```powershell
  powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
  ```
* **Instalar o `uv` no Linux/Mac (Bash):**
  ```bash
  curl -LsSf https://astral.sh/uv/install.sh | sh
  ```

---

## 🛠️ Tabela de Comandos do Workflow

| Nº | Comando | Para que serve | Exemplo de Aplicação | Requer Instalação Prévia? |
| :-: | ----- | ----- | ----- | :-: |
| **1** | `uv init` | **Inicializa um novo projeto Python** criando a estrutura básica e o arquivo `pyproject.toml`. | `uv init` | Sim (`uv` no sistema) |
| **2** | `uv add sphinx myst-parser sphinx-autobuild` | **Instala as dependências de documentação** no projeto:<br>• `sphinx`: Gerador da doc.<br>• `myst-parser`: Suporte a Markdown (`.md`).<br>• `sphinx-autobuild`: Servidor com auto-reload. | `uv add sphinx myst-parser sphinx-autobuild` | Não (O `uv` baixa e instala tudo automaticamente) |
| **3** | `uv run sphinx-quickstart` | **Inicia o assistente interativo** de configuração do Sphinx para responder perguntas sobre nome, autor e idioma do projeto. | `uv run sphinx-quickstart` | Não (Executado via `uv`) |
| **4** | `mv source docs` | **Renomeia a pasta `source`** gerada pelo Sphinx para `docs` (padrão mais utilizado). | `mv source docs` | Não (Comando nativo do Bash/Linux) |
| **5** | `sed -i s/source/docs/ Makefile` | **Atualiza o arquivo `Makefile`** substituindo as referências da antiga pasta `source` para `docs`. | `sed -i s/source/docs/ Makefile` | Não (Comando nativo do Bash/Linux) |
| **6** | `uv run make` | **Executa o utilitário Make** pelo ambiente virtual do `uv` para verificar alvos de compilação. | `uv run make` | Não (Executado via `uv`) |
| **7** | `uv run make html` | **Compila a documentação** e gera as páginas HTML estáticas dentro da pasta `build/html`. | `uv run make html` | Não (Executado via `uv`) |
| **8** | `uv run sphinx-autobuild docs build/html` | **Sobe um servidor local** em `http://localhost:8000` que atualiza a página no navegador em tempo real ao salvar arquivos. | `uv run sphinx-autobuild docs build/html` | Não (Executado via `uv`) |
| **9** | `uv add furo` | **Instala o tema "Furo"**, um tema moderno e leve para o Sphinx. | `uv add furo` | Não (O `uv` instala o pacote) |
| **10**| `uv add sphinx-book-theme` | **Instala o tema "Book Theme"**, estilo livro interativo (usado em documentações como Jupyter/Python). | `uv add sphinx-book-theme` | Não (O `uv` instala o pacote) |

---

## 📝 Resumo Passo a Passo: Configuração do Projeto

### Passo 1: Interatividade no `sphinx-quickstart` (Item 3)
Quando você rodar `uv run sphinx-quickstart`, o terminal fará algumas perguntas. Responda assim:
* Separate source and build directories (y/n): **`yes`**
* Project name: **`doce-asa`** *(ou o nome do seu projeto)*
* Author name(s): **`Seu Nome Seu Sobrenome`**
* Project release []: **`2026`**
* Project language [en]: **`pt_BR`**

---

### Passo 2: Ajustes Manuais no arquivo `docs/conf.py` (Itens 12 a 17)

Abra o arquivo **`docs/conf.py`** no VS Code e faça as alterações abaixo para aplicar o tema e o suporte ao Markdown:

#### 1. Alterar o Tema Visual
Procure a variável `html_theme` e altere para o tema desejado:

```python
# Para usar o tema Furo:
html_theme = 'furo'

# OU para usar o tema Book Theme:
# html_theme = 'sphinx_book_theme'
```

#### 2. Ativar Suporte a Arquivos Markdown (`.md`)
Procure a lista `extensions` e adicione a extensão `'myst_parser'`:

```python
extensions = [
    'myst_parser',
]
```

---

## 🔄 Fluxo de Trabalho Diário

```text
1. Altere ou crie arquivos .md dentro da pasta docs/
2. Execute o servidor de visualização:
   uv run sphinx-autobuild docs build/html
3. Abra no navegador: http://localhost:8000
4. As alterações aparecerão automaticamente na tela ao salvar!
```