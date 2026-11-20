# Day 1 — Set Up Python and Start the Project

**Python, Flask & SQL — Inventory and Order Management System**

---

## Today you will

- Install Python and VS Code
- Run your first Python file
- Store a product name, SKU and stock quantity in variables
- Learn what an SKU is and why it must be unique
- Create a GitHub account and your project repository
- Make your first commit and push it online

By the end of this class your code is on the internet, on your own GitHub profile.

---

## What we are building

For the next 30 days we are not learning random Python. We are building **one real project**: a management system for a small store.

The system will:

- Keep a product list and track **stock** — the number of units available for sale
- Store supplier and customer details
- Record new stock arriving at the store
- Create customer orders containing one or more products
- Confirm an order only when enough stock is available
- Cancel an order and return its stock without counting it twice
- Show sales reports, low-stock reports and a history of every stock change
- Have a login and web pages for the store operator

### The 30 days in three parts

| Days | Part | What we do |
|---|---|---|
| 1–15 | **Python** | Learn programming and build the first version of the project |
| 16–22 | **SQL** | Store the project data in a database and write queries to use it |
| 23–30 | **Flask** | Turn the project into a web application and test it |

We save our work to GitHub **every single day**. Day 30 is not when the portfolio gets built. Day 1 is.

### The tools

| Tool | What it is for |
|---|---|
| Python | Writing the rules and calculations |
| SQLite | Storing products, customers, orders and stock |
| Flask | Building the web application |
| VS Code | Writing and running the code |
| Git and GitHub | Tracking changes and sharing the finished project |
| Postman and pytest | Checking the application works correctly |

---

## 1. Python and VS Code are two different things

- **Python** is the language — the words and grammar we write instructions in.
- **VS Code** is the editor — a smart notepad where we type those instructions and press Run.

Python is the language you speak. VS Code is the room you speak it in. They are separate free downloads and we need both.

A Python file ends with **`.py`**. When we run it, Python reads the file **top to bottom, one line at a time**, and does exactly what each line says. It never skips ahead and never guesses.

---

## 2. Installing Python

### Windows

1. Go to **python.org** → Downloads → Download Python 3.x
2. On the first install screen, tick **"Add python.exe to PATH"** — then click Install Now
3. Check it worked: open **Command Prompt** and type:

```bash
python --version
```

### macOS

1. Download from **python.org** and run the installer
2. Check it worked: open **Terminal** and type:

```bash
python3 --version
```

### Linux

Usually already installed. Check with:

```bash
python3 --version
```

### What you should see

```
Python 3.12.4
```

The exact numbers may differ. As long as it starts with **3**, you are ready.

> **The PATH tick box matters.** If you skipped it on Windows, the terminal will say `'python' is not recognized`. Run the installer again, choose **Modify**, and add Python to PATH.

> **Remember your command.** On Windows it is `python`. On macOS and Linux it is `python3`. Whichever works on your machine is the one you will type for the next 30 days.

---

## 3. Installing VS Code

1. Download from **code.visualstudio.com** and install it
2. Open VS Code and click the **Extensions** icon in the left bar (four squares)
3. Search for **"Python"** by Microsoft and click **Install**
4. Use `File → Open Folder…` to open your project folder

### The four parts of the VS Code window

| Part | Where | What it does |
|---|---|---|
| Explorer | left panel | shows the files in your folder |
| Editor | centre | where you type code |
| Terminal | bottom (`Ctrl` + `` ` ``) | where you type commands and see output |
| Run button | ▶ top right | runs the file you are looking at |

---

## 4. Your first instruction: `print()`

`print()` shows text on the screen. It is how the program talks to the person using it.

```python
print("Hello, store!")
```

Output:

```
Hello, store!
```

Three rules:

- The text goes **inside quotes**. `"double"` or `'single'` both work — just be consistent.
- The brackets `()` are not decoration. `print` is a **function**, and a function is always called with brackets.
- Python is **case-sensitive**. `print` works. `Print` is an error.

### Comments

A line starting with `#` is a note for humans. Python ignores it completely.

```python
# This line explains the code. Python skips it.
print("This line runs.")
```

Output:

```
This line runs.
```

---

## 5. Variables — labelled boxes

A variable is a **name that holds a value**, so we can reuse it instead of typing it again and again.

```python
product_name = "Blue Ball Pen"
product_sku = "PEN-BLU-001"
stock_qty = 25
```

Read the `=` sign as **"gets"**, not "equals":

> *product_name **gets** "Blue Ball Pen"*

Think of a variable as a labelled box. The label is the name. The value is what you put inside.

### Naming rules — these are enforced by Python

- Letters, numbers and underscores only — **no spaces**
- Cannot start with a number: `1name` is an error, `name1` is fine
- Case matters: `stock` and `Stock` are two completely different boxes

### Naming style — our rule for all 30 days

We use **snake_case**: all lowercase, words joined by underscores.

| Good | Bad | Why |
|---|---|---|
| `stock_qty` | `p` | says nothing |
| `product_name` | `productname` | hard to read |
| `product_sku` | `Product SKU` | spaces are not allowed |

A name must describe what is inside the box. Code is read far more often than it is written.

### Variables can change

```python
stock_qty = 25
stock_qty = 20   # a sale happened, so the box now holds 20
print(stock_qty)
```

Output:

```
20
```

The old value is gone. The box holds one thing at a time.

### Printing a variable — watch the quotes

```python
print(product_name)
print("product_name")
```

Output:

```
Blue Ball Pen
product_name
```

**No quotes** means *"look inside the box"*. **With quotes** means *"print these exact letters"*. This catches everybody once.

### Printing several things together

Separate them with commas. Python puts a space between each one.

```python
print("Product:", product_name)
print("Stock:", stock_qty)
```

Output:

```
Product: Blue Ball Pen
Stock: 25
```

---

## 6. SKU — the business term for today

**SKU** stands for **Stock Keeping Unit**. It is a short, unique code the store uses to identify one exact product.

### Why the product name is not enough

- Two suppliers both send something called "Blue Pen" — which is which?
- A customer orders "a pen" — which of the 14 pens that you sell?
- Two products have the same name but different sizes and prices

So every product gets a code that belongs to it and to nothing else:

| SKU | Product |
|---|---|
| `PEN-BLU-001` | Blue Ball Pen |
| `PEN-BLK-001` | Black Ball Pen |
| `NTB-A4-200` | A4 Notebook, 200 pages |

### Our SKU rules for this project

1. Uppercase letters, digits and hyphens only
2. **Unique** — no two products may share an SKU

Hold on to the word **unique**. On Day 5 we write code to spot duplicate SKUs. On Day 16 the database itself will refuse to save two products with the same SKU. Today it is a habit. Later it becomes a rule the computer enforces for us.

---

## 7. Git and GitHub

| Word | Meaning |
|---|---|
| **Git** | A tool on your computer that records snapshots of your code |
| **GitHub** | A website where those snapshots are stored online |
| **Repository** (repo) | One project folder that Git is watching |
| **Commit** | One saved snapshot, with a message describing what changed |
| **Push** | Sending your commits up to GitHub |

Git is like pressing **Save Game**. A commit is one save slot with a label on it. Pushing uploads your save file to the cloud so it is safe and other people can see it.

Why bother on Day 1? Because this repository is the thing you show an employer in a month. It will show 30 days of steady work, not one file uploaded at the end.

### Two files every project needs

- **`README.md`** — the front page of the project. What it is, and how to run it. GitHub displays it automatically.
- **`.gitignore`** — a list of files Git must **ignore**: temporary files, databases, and anything containing passwords.

---

## Hands-on: display one product and its stock

### Step 1 — Create the project folder

Create a folder named **`inventory-system`** somewhere easy to find, such as Desktop or Documents.

Use that exact name. Avoid spaces and special characters in folder names — `inventory-system` is good, `My Project (final)` causes problems later.

Open it in VS Code: `File → Open Folder…`

### Step 2 — Create the file

In the Explorer panel on the left, click **New File** and name it:

```
day01_product.py
```

The `.py` ending is what tells VS Code and Python that this is a Python file.

### Step 3 — Check that everything works

Type this one line:

```python
print("Inventory System is starting...")
```

Save with `Ctrl + S` (`Cmd + S` on Mac), then click the ▶ Run button.

Output:

```
Inventory System is starting...
```

Do not continue until you see that line in the terminal.

### Step 4 — Store the product details

Now replace it with three variables and show them:

```python
product_name = "Blue Ball Pen"
product_sku = "PEN-BLU-001"
stock_qty = 25

print("Product Name :", product_name)
print("SKU          :", product_sku)
print("Stock Qty    :", stock_qty)
```

Output:

```
Product Name : Blue Ball Pen
SKU          : PEN-BLU-001
Stock Qty    : 25
```

### Step 5 — Make it look like a real report

```python
print("==============================")
print("   INVENTORY SYSTEM - DAY 1")
print("==============================")

print("Product Name :", product_name)
print("SKU          :", product_sku)
print("Stock Qty    :", stock_qty)

print("==============================")
print("Report generated successfully.")
```

Output:

```
==============================
   INVENTORY SYSTEM - DAY 1
==============================
Product Name : Blue Ball Pen
SKU          : PEN-BLU-001
Stock Qty    : 25
==============================
Report generated successfully.
```

### Step 6 — Prove the variable is doing the work

Change this one line:

```python
stock_qty = 7
```

Save and run again. The report now shows `7`. You did not touch the `print` line — you changed what was inside the box, and the report followed. That is the whole point of a variable.

### Step 7 — Your turn

Add a **second product** of your own choice, using new variable names:

```python
product_name_2 = "..."
product_sku_2 = "..."
stock_qty_2 = ...
```

Print it below the first one.

---

## Git: save your work to GitHub

### Step 1 — Install Git

Download from **git-scm.com** and install with the default options. Then check:

```bash
git --version
```

### Step 2 — Create a GitHub account

Go to **github.com** and sign up. Choose a username you are happy to put on your CV — this link is going on it.

### Step 3 — Tell Git who you are

You do this once on your computer, not once per project:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Use the **same email address** as your GitHub account, otherwise your commits will not appear on your profile.

### Step 4 — Add the README and .gitignore
skip for now

### Step 5 — Create the repository on GitHub

1. On github.com click **New repository**
2. Name it `inventory-system`
3. Choose **Public**
4. Do **not** tick "Add a README file" — we already have one
5. Click **Create repository**

### Step 6 — First commit and push

In the VS Code terminal, inside your project folder:

```bash
git init
git add .
git commit -m "Day 1: project setup with first product display"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/inventory-system.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your real GitHub username.

### What each line does

| Command | What it does |
|---|---|
| `git init` | Start watching this folder |
| `git add .` | Select all changed files for the next snapshot |
| `git commit -m "..."` | Take the snapshot and label it |
| `git branch -M main` | Name the main line of work `main` |
| `git remote add origin <url>` | Point this folder at the GitHub repository |
| `git push -u origin main` | Upload it |

> The first push will ask you to sign in. Signing in through the browser is easiest. If the terminal asks for a password, it wants a **Personal Access Token** (GitHub → Settings → Developer settings → Personal access tokens), **not** your account password.

### Step 7 — Check it

Refresh your GitHub repository page in the browser. Your files should be there, with your README displayed underneath.

### From tomorrow, saving your work is three lines

```bash
git add .
git commit -m "Day N: what I did"
git push
```

---


