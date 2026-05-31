<div align="center">

# Academic Schedule Bot

[![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)](https://kotlinlang.org/)
[![Gradle](https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white)](https://gradle.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Telegram](https://img.shields.io/badge/Telegram_Bot-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)](https://core.telegram.org/bots)

[![GitHub last commit](https://img.shields.io/github/last-commit/i-JSS/Academic-Schedule-Bot?style=flat-square)](https://github.com/i-JSS/Academic-Schedule-Bot/commits/main)
[![GitHub repo size](https://img.shields.io/github/repo-size/i-JSS/Academic-Schedule-Bot?style=flat-square)](https://github.com/i-JSS/Academic-Schedule-Bot)

Um **bot para o Telegram** que gera automaticamente todas as grades horárias válidas, resolvendo conflitos de agendamento de intervalos com uma abordagem de **Algoritmo Guloso**.

[Ver Apresentação](https://youtu.be/dBowU2K6534) - [Reportar Bug](https://github.com/i-JSS/Academic-Schedule-Bot/issues)

</div>


<div align="center">


## Screenshots

| Iniciando o bot                                                                                                                               | Escolhendo matérias                                                                                                                            |
|-----------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| <img src="https://raw.githubusercontent.com/projeto-de-algoritmos-2024/Greed_BotGradeHoraria/refs/heads/main/images/inicia.png" width="220"/> | <img src="https://raw.githubusercontent.com/projeto-de-algoritmos-2024/Greed_BotGradeHoraria/refs/heads/main/images/escolhe.png" width="220"/> |


<img src="https://raw.githubusercontent.com/projeto-de-algoritmos-2024/Greed_BotGradeHoraria/refs/heads/main/images/grade.png" width="220"/>

</div>

---

## Sobre o Projeto

O **Academic Schedule Bot** é um chatbot para a plataforma Telegram que resolve o clássico problema de **Maximização de Agendamento de Intervalos** no contexto acadêmico. A partir de um conjunto de matérias e seus respectivos horários, o bot aplica uma estratégia gulosa para gerar todas as combinações de grade sem conflitos — ajudando estudantes a planejar o semestre de forma prática e eficiente.

Este projeto foi desenvolvido como parte da disciplina de **Projeto de Algoritmos** na Universidade de Brasília (UnB), com foco em algoritmos gulosos e escalonamento com restrições.

---

## Funcionalidades

- Geração de todas as grades horárias válidas e sem conflitos
- Algoritmo guloso para escalonamento eficiente de intervalos
- Interface interativa via Telegram
- Armazenamento de matérias e horários em PostgreSQL
- Validação e detecção de conflitos em tempo real

---

## Tecnologias Utilizadas

| Camada            | Tecnologia                   |
|-------------------|------------------------------|
| Linguagem         | Kotlin                       |
| Build             | Gradle (Kotlin DSL)          |
| Banco de Dados    | PostgreSQL                   |
| Plataforma do Bot | Telegram Bot API             |
| Algoritmo         | Greedy / Interval Scheduling |

---

## Como Executar

### Pré-requisitos

- JDK 17+
- Gradle
- PostgreSQL
- Token de Bot do Telegram (via [@BotFather](https://t.me/botfather))

### Passo a passo

**1. Clone o repositório**

```bash
git clone https://github.com/i-JSS/Academic-Schedule-Bot.git
cd Academic-Schedule-Bot
```

**2. Restaure o banco de dados**

Faça o download do [dump SQL](https://github.com/i-JSS/Academic-Schedule-Bot/blob/main/postgres_localhost-2025_01_18_12_54_32-dump.sql) e restaure-o em um banco PostgreSQL chamado `greed`:

```bash
psql -U postgres -c "CREATE DATABASE greed;"
psql -U postgres -d greed -f postgres_localhost-2025_01_18_12_54_32-dump.sql
```

**3. Crie o usuário do banco**

```sql
CREATE ROLE kd_user LOGIN PASSWORD 'pa';
GRANT ALL PRIVILEGES ON DATABASE greed TO kd_user;
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO kd_user;
```

**4. Compile o projeto**

```bash
./gradlew build
```

**5. Configure o token do bot**

```bash
# Linux / macOS
export BOT_TOKEN=seu_token_aqui

# Windows (PowerShell)
$env:BOT_TOKEN = "seu_token_aqui"
```

**6. Execute**

Rode a função `main` e acesse o bot em [@UnBHorarios_bot](https://web.telegram.org/k/#@UnBHorarios_bot).

---

## Algoritmo

A lógica de escalonamento é baseada no problema de **Maximização de Agendamento de Intervalos** — um algoritmo guloso clássico que seleciona o maior número de intervalos não sobrepostos. Neste contexto:

- Cada **matéria** é mapeada para um ou mais **intervalos de tempo**
- A estratégia gulosa percorre os intervalos ordenados e elimina conflitos
- Todas as combinações válidas e sem conflito são retornadas ao usuário

> Complexidade: **O(n log n)** para ordenação + **O(n)** para seleção por combinação.

---

## Autores

| Matrícula | Aluno |
|---|---|
| 22/1007814 | André Emanuel Bispo da Silva |
| 22/1008150 | João Antonio Ginuino Carvalho |

---

<div align="center">
Feito com <3 na <strong>Universidade de Brasília</strong>
</div>