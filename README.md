# DSAlib
A curated common or not so common collection of Data Structures and Algorithms (DSA) practice problems and solutions, featuring personal explanations, multiple approaches,and personal insights gained during problem-solving. This repository serves as both a learning journal and a reference for coding interview preparation and competitive programming.
<div align="center">

```
 ██████╗ ███████╗ █████╗     ██╗     ██╗██████╗ 
 ██╔══██╗██╔════╝██╔══██╗    ██║     ██║██╔══██╗
 ██║  ██║███████╗███████║    ██║     ██║██████╔╝
 ██║  ██║╚════██║██╔══██║    ██║     ██║██╔══██╗
 ██████╔╝███████║██║  ██║    ███████╗██║██████╔╝
 ╚═════╝ ╚══════╝╚═╝  ╚═╝    ╚══════╝╚═╝╚═════╝ 
```

**A production-ready C++ library for Data Structures & Algorithms**

![C++](https://img.shields.io/badge/C%2B%2B-17%2F20-blue?style=flat-square&logo=cplusplus)
![Build](https://img.shields.io/badge/build-passing-brightgreen?style=flat-square)
![Coverage](https://img.shields.io/badge/coverage-96%25-blueviolet?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-orange?style=flat-square)
![Algorithms](https://img.shields.io/badge/algorithms-40%2B-teal?style=flat-square)
![Version](https://img.shields.io/badge/version-v2.4.0-red?style=flat-square)

</div>

---

## What's Inside

| Category | Algorithms |
|---|---|
| **Sorting** | Quick Sort, Merge Sort, Heap Sort, Radix Sort, Tim Sort, Counting Sort |
| **Graphs** | BFS, DFS, Dijkstra, Bellman-Ford, Floyd-Warshall, Kruskal, Prim |
| **Trees** | AVL Tree, Red-Black Tree, Segment Tree, Fenwick Tree, Trie |
| **Dynamic Programming** | 0/1 Knapsack, LCS, LIS, Matrix Chain, Coin Change, Edit Distance |
| **Searching** | Binary Search, Ternary Search, Interpolation, Exponential, Jump Search |
| **Strings** | KMP, Rabin-Karp, Z-Algorithm, Aho-Corasick, Suffix Array |

---

## Complexity Reference

### Sorting Algorithms

| Algorithm | Best | Average | Worst | Space | Stable |
|---|---|---|---|---|---|
| Quick Sort | Ω(n log n) | Θ(n log n) | O(n²) | O(log n) | ✗ |
| Merge Sort | Ω(n log n) | Θ(n log n) | O(n log n) | O(n) | ✓ |
| Heap Sort | Ω(n log n) | Θ(n log n) | O(n log n) | O(1) | ✗ |
| Tim Sort | Ω(n) | Θ(n log n) | O(n log n) | O(n) | ✓ |
| Radix Sort | Ω(nk) | Θ(nk) | O(nk) | O(n+k) | ✓ |
| Counting Sort | Ω(n+k) | Θ(n+k) | O(n+k) | O(k) | ✓ |

### Searching Algorithms

| Algorithm | Best | Average | Worst | Space |
|---|---|---|---|---|
| Binary Search | Ω(1) | Θ(log n) | O(log n) | O(1) |
| Linear Search | Ω(1) | Θ(n) | O(n) | O(1) |
| Jump Search | Ω(1) | Θ(√n) | O(√n) | O(1) |
| Interpolation | Ω(1) | Θ(log log n) | O(n) | O(1) |

### Tree Operations

| Structure | Search | Insert | Delete | Space |
|---|---|---|---|---|
| AVL Tree | O(log n) | O(log n) | O(log n) | O(n) |
| Red-Black Tree | O(log n) | O(log n) | O(log n) | O(n) |
| Segment Tree | O(log n) | O(log n) | O(log n) | O(n) |
| Fenwick Tree | O(log n) | O(log n) | O(log n) | O(n) |
| Trie | O(m) | O(m) | O(m) | O(n·m) |

> `m` = length of key, `k` = range of input

---

## Installation

### CMake (recommended)

```cmake
# Add to your CMakeLists.txt
include(FetchContent)

FetchContent_Declare(dsalib
  GIT_REPOSITORY https://github.com/your-username/dsalib.git
  GIT_TAG        v2.4.0
)
FetchContent_MakeAvailable(dsalib)

target_link_libraries(your_target PRIVATE dsalib)
```

### Git Clone

```bash
git clone --depth=1 https://github.com/your-username/dsalib.git
cd dsalib
cmake -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build
sudo cmake --install build
```

### vcpkg

```bash
vcpkg install dsalib
```

```cmake
# Then in CMakeLists.txt:
find_package(dsalib CONFIG REQUIRED)
target_link_libraries(your_target PRIVATE dsalib::dsalib)
```

---

## Quick Start

```cpp
#include <dsalib/sort.hpp>
#include <dsalib/graph.hpp>
#include <dsalib/tree/avl.hpp>

int main() {
    // --- Sorting
    std::vector<int> v = {5, 2, 8, 1, 9};
    dsa::merge_sort(v.begin(), v.end());       // [1, 2, 5, 8, 9]

    // --- Graph (Dijkstra's shortest path)
    dsa::Graph<int> g(6);
    g.add_edge(0, 1, 4);
    g.add_edge(0, 2, 2);
    auto dist = dsa::dijkstra(g, 0);           // shortest distances from node 0

    // --- AVL Tree
    dsa::AVLTree<int> tree;
    tree.insert(10);
    tree.insert(20);
    tree.insert(5);
    tree.inorder();                            // 5 → 10 → 20

    return 0;
}
```

---

## Data Structures

All structures are **header-only** and **template-based** — no runtime overhead, no dependencies.

```
dsalib/
├── include/
│   ├── dsalib/
│   │   ├── sort.hpp          # Sorting algorithms
│   │   ├── search.hpp        # Searching algorithms
│   │   ├── graph.hpp         # Graph representations + traversals
│   │   ├── dp.hpp            # Dynamic programming
│   │   ├── string.hpp        # String algorithms
│   │   └── tree/
│   │       ├── avl.hpp       # AVL Tree
│   │       ├── rbt.hpp       # Red-Black Tree
│   │       ├── segment.hpp   # Segment Tree
│   │       ├── fenwick.hpp   # Fenwick (BIT)
│   │       └── trie.hpp      # Trie
│   └── ds/
│       ├── stack.hpp         # Stack
│       ├── queue.hpp         # Queue / Deque
│       ├── linked_list.hpp   # Singly & Doubly Linked List
│       ├── heap.hpp          # Min / Max Heap
│       ├── hash_map.hpp      # Hash Map (open addressing)
│       ├── disjoint_set.hpp  # Union-Find (DSU)
│       ├── bloom_filter.hpp  # Bloom Filter
│       ├── lru_cache.hpp     # LRU Cache
│       └── skip_list.hpp     # Skip List
```

### Available Data Structures

- Stack
- Queue / Deque
- Singly & Doubly Linked List
- Min / Max Heap
- Hash Map (open addressing)
- Disjoint Set (Union-Find)
- Segment Tree
- Fenwick Tree (Binary Indexed Tree)
- Trie
- Bloom Filter
- LRU Cache
- Skip List

---

## Usage Examples

### Sorting with Custom Comparator

```cpp
#include <dsalib/sort.hpp>

struct Student {
    std::string name;
    int grade;
};

std::vector<Student> students = {{"Alice", 85}, {"Bob", 92}, {"Carol", 78}};

// Sort by grade descending
dsa::quick_sort(students.begin(), students.end(),
    [](const Student& a, const Student& b) {
        return a.grade > b.grade;
    });
// Result: Bob(92), Alice(85), Carol(78)
```

### Graph Traversal

```cpp
#include <dsalib/graph.hpp>

dsa::Graph<int> g(5);
g.add_edge(0, 1);
g.add_edge(0, 2);
g.add_edge(1, 3);
g.add_edge(2, 4);

// BFS from source 0
auto bfs_order = dsa::bfs(g, 0);      // [0, 1, 2, 3, 4]

// DFS from source 0
auto dfs_order = dsa::dfs(g, 0);      // [0, 1, 3, 2, 4]

// Check for cycle
bool has_cycle = dsa::detect_cycle(g); // false
```

### Dynamic Programming

```cpp
#include <dsalib/dp.hpp>

// 0/1 Knapsack
std::vector<int> weights = {2, 3, 4, 5};
std::vector<int> values  = {3, 4, 5, 6};
int capacity = 8;

int max_val = dsa::knapsack(weights, values, capacity); // 10

// Longest Common Subsequence
std::string s1 = "ABCBDAB";
std::string s2 = "BDCABA";
int lcs_len = dsa::lcs(s1, s2); // 4
```

---

## Running Tests

```bash
# Build with tests enabled
cmake -B build -DDSALIB_BUILD_TESTS=ON
cmake --build build

# Run all tests
cd build && ctest --output-on-failure

# Run specific test suite
./build/tests/test_sorting
./build/tests/test_graphs
./build/tests/test_trees
```

---

## Benchmarks

Benchmarked on `Apple M2, 8GB RAM, clang 15 -O2`, input size `n = 1,000,000`.

| Algorithm | Time (ms) | Comparisons |
|---|---|---|
| `dsa::merge_sort` | 142 ms | ~19.9M |
| `dsa::quick_sort` | 118 ms | ~13.8M |
| `dsa::heap_sort` | 198 ms | ~27.2M |
| `dsa::tim_sort` | 109 ms | ~11.4M |
| `std::sort` | 112 ms | ~13.5M |

> Run benchmarks locally: `cmake -DDSALIB_BUILD_BENCHMARKS=ON` then `./build/bench/bench_all`

---

## Requirements

- C++17 or later (`-std=c++17`)
- CMake 3.14+
- A modern compiler: GCC 9+, Clang 10+, MSVC 2019+

No external dependencies. Header-only.

---

## Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch: `git checkout -b feat/my-algorithm`
3. Add your implementation under `include/dsalib/`
4. Write tests in `tests/`
5. Ensure all tests pass: `ctest --output-on-failure`
6. Open a Pull Request

Please follow the [code style guide](CONTRIBUTING.md) and keep complexity analysis in the header comments.

---

## Project Structure

```
dsalib/
├── include/           # Header-only implementations
├── tests/             # Unit tests (Catch2)
├── bench/             # Benchmarks (Google Benchmark)
├── examples/          # Usage examples
├── docs/              # Documentation
├── CMakeLists.txt
├── CONTRIBUTING.md
└── README.md
```

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

<div align="center">

Made with ♥ for GATE CS & competitive programming

⭐ Star this repo if it helped you!

</div>
