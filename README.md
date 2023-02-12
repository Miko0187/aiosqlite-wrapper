# aiosqlite-wrapper

## 🏗 An async wrapper for aiosqlite

## ❔ Requirements

- [Python](https://www.python.org/) - `3.7+`
- [aiosqlite](https://pypi.org/project/aiosqlite/) - `pip install aiosqlite`

## 📄 Example

```py
import asyncio
from wrapper import execute, Fetch


@execute
async def create_table():
    return """CREATE TABLE IF NOT EXISTS users (
        name TEXT PRIMARY KEY,
        age INTEGER
    )"""

@execute
async def insert_user(name, age):
    return "INSERT INTO users VALUES (?, ?)"

@fetch(Fetch.ALL)
async def get_users():
    return "SELECT * FROM users"

async def main():
    await create_table()

    await insert_user("John", 20)
    await insert_user("Marie", 21)

    users = await get_users()

    for user in users:
        print(f"Name: {user[0]}")
        print(f"Age: {user[1]}")

asyncio.run(main())
```
