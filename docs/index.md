📚 BitBully Databases

<h1 align="center">
<img src="https://github.com/MarkusThill/bitbully-databases/blob/master/bitbully-databases-logo.png" alt="bitbully-logo-full" width="400" >
</h1><br>

BitBully Databases provide precomputed **Connect-4 opening books** containing millions of evaluated positions and scores.
Each database stores Huffman-encoded board states with their corresponding **evaluation values** (win/loss or distance to win/loss).
They are packaged as binary assets and can be accessed directly through the `bitbully_databases` module.

This package includes a **pure-Python implementation** (no NumPy dependency) that demonstrates how to read, search, and interpret these databases.
For performance-critical applications, prefer the optimized [BitBully C++/pybind11 API](https://github.com/MarkusThill/BitBully).

---

## 🗂️ Available Databases

| Name | File | Ply Depth | Entries | Contains Win Distances | Disk Size | In-Memory Size (Python) | Description |
|------|------|------------|----------|-------------------------|------------|--------------------------|--------------|
| **8-ply** | `book_8ply.dat` | 8 | 34 515 | ✗ | 102 KB | 277 336 B (~271 KB) | Smallest opening book, containing all unique positions up to 8 moves. Stores only win/loss outcomes without distances. |
| **12-ply** | `book_12ply.dat` | 12 | 1 735 945 | ✗ | 6.7 MB | 15 225 112 B (~14.9 MB) | Covers all positions up to 12 plies (≈ 1.7 M). Stores only win/loss outcomes (−1 = loss, 0 = draw, 1 = win). |
| **12-ply-dist** *(default)* | `book_12ply_distances.dat` | 12 | 4 200 899 | ✓ | 21 MB | 34 724 184 B (~33.1 MB) | The most detailed book. Extends 12-ply by including signed distance values indicating how many moves remain until a win or loss. Recommended for research and analysis. |

All databases are **sorted by Huffman-encoded position keys** for efficient binary-search lookup.



---

## Pure-Python Implementation — Educational and Non-Performance Critical

The pure-Python interface provided in this package emphasizes clarity over speed and demonstrates the logic behind BitBully’s databases:

- Huffman encoding of Connect-4 positions
- Binary search over sorted position–score pairs
- Horizontal mirroring for symmetry
- Some other simple utility functions

For solvers, reinforcement-learning agents, or large-scale simulations, use the  [BitBully C++/pybind11 implementation](https://github.com/MarkusThill/BitBully) provided by the main BitBully package.
