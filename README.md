# Desafio Final: Infraestrutura Wiki.js (Docker)

Projeto desenvolvido para a disciplina de **Tópicos Avançados em TI (2026/1)**. O objetivo é a implantação de uma infraestrutura de produção resiliente, segura e otimizada para o Wiki.js utilizando Docker Compose.

---

## 🏗️ Arquitetura da Solução
O ambiente utiliza uma arquitetura **Two-Tier**, garantindo a separação entre a camada de aplicação e a camada de dados:
*   **Aplicação:** `Wiki.js` (container `wiki_app`) - Interface web para documentação.
*   **Banco de Dados:** `PostgreSQL 15-alpine` (container `wiki_db`) - Armazenamento persistente.

---

## 🚀 Requisitos Atendidos
*   **Isolamento de Rede:** Comunicação interna via rede `wiki-network` sem exposição da porta do banco de dados (5432) para o host.
*   **Persistência de Dados:** Uso de *Named Volumes* para garantir que dados do Postgres e uploads do Wiki.js não sejam perdidos em caso de reinicialização.
*   **Gerenciamento de Segredos:** Variáveis de ambiente protegidas em arquivo `.env` (ignorado pelo Git).
*   **Resiliência:** Implementação de `healthcheck` oficial com `pg_isready` para garantir a ordem correta de inicialização dos containers.

---

## 🛠️ Como Executar

### Pré-requisitos
*   Docker instalado
*   Docker Compose instalado

### Passos de Instalação
1. Clone este repositório:
   `git clone https://github.com/vitto2099/TrabalhoDockerFinal.git`
2. Copie o arquivo de modelo para o arquivo real:
   `cp .env.example .env`
3. Edite o arquivo `.env` com suas credenciais.
4. Inicie o ambiente:
   `docker compose up -d`

---

## ⚙️ Comandos de Gestão

| Comando | Descrição |
| :--- | :--- |
| `docker compose up -d` | Sobe a infraestrutura |
| `docker compose ps` | Verifica o status dos containers |
| `docker compose down` | Remove os containers (dados persistem) |
| `docker volume ls` | Lista os volumes criados |

---

## 👨‍💻 Autor
**Vitor** - Aluno de Engenharia de Software (UNC).
