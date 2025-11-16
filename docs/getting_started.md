
# Getting Started

## Installing BitBully Databases

Install `bitbully-databases` via pip:


=== "Latest"
    ```bash
    pip install bitbully-databases
    ```

=== "Version x.y.z"
    ```bash
    pip install bitbully-databases==x.y.z
    ```

## Usage

```python
import bitbully_databases as bbd

# Load the 12-ply book with distances (default)
db = bbd.BitBullyDatabases("12-ply-dist")

# Get the absolute file path of the packaged database
path = bbd.BitBullyDatabases.get_database_path("12-ply-dist")
print("Database path:", path)

# Check database metadata
print("Book size:", db.get_book_size())
print("Memory size (bytes):", db.get_book_memory_size())
print("Contains win distances:", db.has_win_distances())

# Example Connect-4 board (bottom → top)
# Player 1 (yellow, X) will eventually win
board = [
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 1, 0, 0, 0],
    [0, 1, 0, 2, 0, 0, 0],
    [0, 2, 0, 1, 0, 2, 0],
    [0, 1, 0, 2, 0, 1, 0],
    [0, 2, 0, 1, 0, 2, 0],
]

# Retrieve the evaluation score for the board
value = db.get_book_value(board)
print("Book value:", value)
if value is not None and db.has_win_distances():
    print(f"→ Player 1 wins in {100 - abs(value)} moves.")

# Display whether the database uses distances and the type of book
print("Has win distances:", db.has_win_distances())
```

---

### 8-Ply Database — Basic Win/Loss Information
```python
board = [
    [0,0,0,0,0,0,0],
    [0,0,0,1,0,0,0],
    [0,0,0,2,0,0,0],
    [0,2,0,1,0,0,0],
    [0,1,0,2,0,0,0],
    [0,2,0,1,0,0,0],
]

val = bbd.BitBullyDatabases("8-ply").get_book_value(board)
print(val)  # → 1 (Player 1 win)
```

---

### 12-Ply Database — Basic Win/Loss Information
```python
board = [
    [0,0,0,0,0,0,0],
    [0,0,0,0,0,0,0],
    [0,0,1,1,0,0,0],
    [0,0,2,2,0,0,0],
    [0,0,2,1,2,0,0],
    [0,1,1,2,1,2,0],
]

val = bbd.BitBullyDatabases("12-ply").get_book_value(board)
print(val)  # → 0 (draw)
```

---

### 12-Ply-Dist Database — Win/Loss With Distance Values
```python
board = [
    [0,0,0,0,0,0,0],
    [0,0,0,1,0,0,0],
    [0,1,0,2,0,0,0],
    [0,2,0,1,0,2,0],
    [0,1,0,2,0,1,0],
    [0,2,0,1,0,2,0],
]

val = bbd.BitBullyDatabases("12-ply-dist").get_book_value(board)
print(val)  # → 71 (Player 1 wins in 100 − 71 = 29 moves)
```
