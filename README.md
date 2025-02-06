# Tokenizer

Tokenizer is a simple GUI application for converting text into a delimited list with optional quoting, spacing, block characters, and SQL formatting.

## Features
- Convert text into a delimited list with configurable delimiters (comma, tab, newline, etc.).
- Optionally wrap items in quotes (`'`, `"`, `` ` ``).
- Add enclosing blocks (`()`, `[]`, `{}`).
- Optionally add spaces after commas for readability.
- **SQL Mode**:
  - Automatically formats input into a SQL `SELECT ... WHERE IN (...)` query.
  - Allows specifying **SELECT columns**, **FROM expressions (tables, joins, etc.)**, and **WHERE condition columns**.
- Copy results to the clipboard.

## Requirements
- Python 3.9+
- PyQt5 (`pip install PyQt5`)

## Installation
Clone the repository and install dependencies:
```sh
git clone https://github.com/your-repo/tokenizer.git
cd tokenizer
pip install -r requirements.txt
```

## Running the Application
```sh
python tokenizer.py
```

## SQL Mode
When "SQL" is selected in the **Mode** dropdown:
- **Add Block** is automatically set to `()` and hidden.
- Additional input fields appear:
  - **Select Columns** (default: `*`)
  - **From Expression** (default: `"table"`, supports joins)
  - **Condition Column** (default: `"col"`)

### **Example Output**
If the input list is:
```
apple
banana
cherry
```
And the SQL settings are:
- **Select Columns:** `name`
- **From Expression:** `fruits_table INNER JOIN categories ON fruits_table.category_id = categories.id`
- **Condition Column:** `fruit_name`

Then the output will be:
```sql
SELECT name
FROM fruits_table INNER JOIN categories ON fruits_table.category_id = categories.id
WHERE fruit_name IN ('apple', 'banana', 'cherry');
```

## License
MIT License