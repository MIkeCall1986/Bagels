# 🥯 Bagels - TUI Expense Tracker

Powerful expense tracker that lives in your terminal.

![PyPI - Version](https://img.shields.io/pypi/v/bagels?style=for-the-badge)
![GitHub License](https://img.shields.io/github/license/EnhancedJax/Bagels?style=for-the-badge)
![PyPI - Downloads](https://img.shields.io/pypi/dm/Bagels?style=for-the-badge)

<!-- <a title="This tool is Tool of The Week on Terminal Trove, The $HOME of all things in the terminal" href="https://terminaltrove.com/bagels"><img src="https://cdn.terminaltrove.com/media/badges/tool_of_the_week/svg/terminal_trove_tool_of_the_week_black_on_white_bg.svg" alt="Terminal Trove Tool of The Week" height="28" /></a> -->

![Bagels](./public/screenshots/thumb1.png)
![Bagels](./public/screenshots/thumb2.png)

Bagels expense tracker is a TUI application where you can track and analyse your money flow, with convenience oriented features and a complete interface.

> **Why an expense tracker in the terminal?**
> I found it easier to build a habit and keep an accurate track of my expenses if I do it at the end of the day, instead of on the go. So why not in the terminal where it's fast, and I can keep all my data locally?

## ✨ Features

Some notable features include:

- Accounts, (Sub)Categories, Splits, Transfers, Records
- Templates for Recurring Transactions
- Add Templated Record with Number Keys
- Clear Table Layout with Togglable Splits
- Transfer to and from Outside Tracked Accounts
- "Jump Mode" Navigation
- Less and Less Fields to Enter per Transaction, Powered by Transactions and Input Modes
- Insights
- Customizable Keybindings and Defaults, such as First Day of Week
- Label, amount and category filtering
- Spending plottings / graphs with estimated spendings
- Budgetting tool for saving money and limiting unnecessary spendings

## 📦 Installation

<details open>
    <summary><b>Recommended: By UV</b></summary>

Bagels can be installed via uv on MacOS, Linux, and Windows.

`uv` is a single Rust binary that you can use to install Python apps. It's significantly faster than alternative tools, and will get you up and running with Bagels in seconds.

You don't even need to worry about installing Python yourself - uv will manage everything for you.

#### Unix / MacOS:

```bash
# install uv (package manager):
curl -LsSf https://astral.sh/uv/install.sh | sh

# restart your terminal, or run the following command:
source $HOME/.local/bin/env # or follow instructions

# install bagels through uv
uv tool install --python 3.13 bagels
```

`uv` can also be installed via Homebrew, Cargo, Winget, pipx, and more. See the [installation guide](https://docs.astral.sh/uv/getting-started/installation/) for more information.

#### Windows:

```bash
# install uv:
winget install --id=astral-sh.uv  -e
# then follow instructions to add uv to path
uv tool install --python 3.13 bagels
```

</details>

<details>
    <summary>By Brew</summary>

    brew install bagels

</details>

<details>
    <summary>By Pipx</summary>

    pipx install bagels

</details>

<details>
    <summary>By Conda</summary>

    conda install -c conda-forge bagels

</details>

<details>
    <summary>By X-CMD</summary>

    x install bagels

</details>

## 🥯 Usage:

```bash
bagels # start bagels
bagels --at "./" # start bagels with data stored at cd
bagels locate database # find database file path
bagels locate config # find config file path
```

> It is recommended, but not required, to use "modern" terminals to run the app. MacOS users are recommended to use Ghostty, and Windows users are recommended to use Windows Terminal.

To upgrade with uv:

```bash
uv tool upgrade bagels
```

## ↔️ Migration

Please read the [migration guide](MIGRATION.md) for migration from other services.

## 🛠️ Development setup

```sh
git clone https://github.com/EnhancedJax/Bagels.git
cd Bagels
uv run pre-commit install
mkdir instance
uv run bagels --at "./instance/" # runs app with storage in ./instance/
# alternatively, use textual dev mode to catch prints
uv run textual run --dev "./src/bagels/textualrun.py"
uv run textual console -x SYSTEM -x EVENT -x DEBUG -x INFO # for logging
```

Please use the black formatter to format the code.

## 🗺️ Roadmap

- [x] Budgets (Major!)
- [x] More insight displays and analysis (by nature etc.)
- [ ] Daily check-ins
- [ ] Pagination for records on monthly and yearly views.
- [ ] Importing from various formats

Backlog:

- [ ] "Processing" bool on records for transactions in process
- [ ] Record flags for future insights implementation
- [ ] Code review
- [ ] Repayment reminders
- [ ] Add tests
- [ ] Bank sync

## Attributions

- Heavily inspired by [posting](https://posting.sh/)
- Bagels is built with [textual](https://textual.textualize.io/)
- It's called bagels because I like bagels

24.02.26 sync fork
Ось результати аналізу та стратегія трансформації для проекту **Bagels**, підготовлені у форматі для копіювання в Notion.

---

# 📑 Звіт AI-консультанта: Проект "Bagels"

**Bagels** — це потужний термінальний трекер витрат (TUI), написаний на Python з використанням бібліотеки Textual, який дозволяє зручно аналізувати фінансові потоки безпосередньо в консолі.

---

## 🧬 Частина 1: "ДНК" Проекту

Логіку коду Bagels можна розбити на такі **атомарні функції**:

*   **Керування транзакціями (Records Management):** Обробка складних фінансових операцій, включаючи рахунки, категорії, перекази та розподіл (splits) платежів.
*   **Оркестрація TUI (Textual Rendering):** Побудова інтерактивного інтерфейсу в терміналі з підтримкою табличних макетів та "Jump Mode" навігації.
*   **Система шаблонів (Templating):** Логіка для швидкого введення повторюваних транзакцій за допомогою гарячих клавіш.
*   **Аналітичний двигун (Insights Engine):** Фільтрація даних за мітками, сумами та категоріями, а також побудова графіків витрат.
*   **Локальне керування даними:** Функції для роботи з локальною базою даних та файлами конфігурації без необхідності хмарної синхронізації.
*   **Автоматизація середовища (UV Integration):** Використання Rust-бінарника `uv` для надшвидкого встановлення, керування залежностями та версіями Python.

### 💎 Головна технічна цінність
Головна цінність проекту полягає у **високій продуктивності та конфіденційності (Local-First)**. Bagels перетворює термінал на повноцінну фінансову робочу станцію, де швидкість взаємодії (через клавіатуру) та локальне зберігання даних мають пріоритет над громіздкими веб-інтерфейсами.

---

## 🚀 Частина 2: "Трансформація" (Інтеграція з Gemini LLM)

Інтеграція з **Gemini** (зокрема через GitHub Models або Spark) перетворює Bagels зі статичного інструменту на **автономного фінансового асистента**.

### Як зміниться функціонал?
1.  **Введення природною мовою (Natural Language Input):** Замість заповнення полів форми, користувач зможе просто написати в терміналі: *"Сьогодні витратив 15 баксів на обід в кафе через картку Mono"*. Gemini автоматично розпарсить це в категорію, рахунок та суму.
2.  **Прогностична аналітика:** ШІ зможе аналізувати графіки витрат і давати поради: *"З твоїм темпом витрат на каву ти перевищиш бюджет на 20% до кінця місяця"*.
3.  **Автоматична категоризація:** Використання Gemini для інтелектуального тегування транзакцій на основі історії користувача, що мінімізує ручну роботу.

### Сценарій сервісу "Smart Expense API" (Bagels + Gemini + ID_{$})

Сценарій створення інтелектуального сервісу на вашому сайті:
1.  **Збір (ID_{$1}):** Ваш базовий Python-скрипт **ID_{$1}** моніторить ваші вхідні листи з чеками або SMS від банку.
2.  **Обробка (Gemini):** Текст чека передається в Gemini, яка витягує суму, дату та перелік товарів.
3.  **Запис (Bagels):** Через CLI-інтерфейс Bagels дані автоматично заносяться в локальну базу даних як нова транзакція або "Record".
4.  **Звіт (ID_{$2}):** Другий скрипт **ID_{$2}** забирає дані з `bagels insights` і генерує JSON для вашого сайту.
5.  **Деплой (GitHub Spark):** За допомогою **GitHub Spark** ви розгортаєте веб-дашборд на сайті, який відображає локальну статистику з вашого терміналу у візуально привабливому вигляді для особистого користування.

---

## 📋 План дій для Notion
| Крок | Дія | Результат |
| :--- | :--- | :--- |
| **1** | Встановлення через UV: `uv tool install bagels` | Робоче середовище в терміналі |
| **2** | Налаштування шаблонів через `config.toml` | Швидке ручне введення |
| **3** | Підключення Gemini для парсингу вільних запитів | Інтелектуальне введення даних |
| **4** | Використання **GitHub Spark** для веб-візуалізації | Готовий сервіс на сайті |

---

### 💡 Резюме

**Суть:** **Термінальний трекер витрат на Python**.

**AI-Роль:** **Створення інтелектуальних застосунків через Spark**.
