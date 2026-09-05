## 🧬 Project Overview
This utility automates extracting, filtering, and cross-referencing genomic data from tab-separated datasets (`HUGO_genes.txt` and `chr21_genes.txt`). The pipeline isolates unique gene symbols, flags occurrences, maps descriptions via hash tables, and mathematically calculates set intersections to isolate overlapping genetic markers.

The final parsed results are automatically exported to a structured `/OUTPUT` directory for downstream data analysis.

## 🛠️ Technical Stack & Skills
* **Language:** Python 3 
* **Algorithmic Complexity:** High-efficiency data manipulation utilizing built-in Python `sets` for O(1) amortized lookups and mathematical intersections.
* **CLI & Automation:** Parametric command routing via `argparse` alongside an interactive runtime input loop.

## 💻 Code Architecture & Highlights
The codebase applies modular software design patterns to keep data processing, execution, and user interfaces entirely decoupled:

* **Mathematical Set Operations (`intersection.py`):** Leverages Python's native hashing structures to deduplicate arrays and compute structural intersections across multi-thousand-line database tables instantly:
```python
# Programmatically isolates overlapping targets across distinct genomic sets
intersection = set(unique_list1).intersection(set(unique_list2))
common_list = sorted(list(intersection))
```

* **Interactive Search Console (`chr21_gene_names.py`):** Implements a persistent lookup system, caching text datasets into an in-memory dictionary map to handle instantaneous user keyword queries:
```python
# Caches data matrices for high-speed key-value lookups
while True:
    gene = input("\nEnter gene name of interest... Type quit to exit: ").lower()
    if gene in desc:
        print(f"({gene}) Found! Here is the description:\n", desc[gene])
    elif gene == 'quit':
        break
```

* **Dynamic File Routing:** Integrates `argparse` to completely avoid hardcoded file names, letting you swap out input matrices or output pathways dynamically directly from a terminal environment.

## 🧪 Testing & Code Coverage
This repository prioritizes software stability and reliable data pipelines by integrating Python's native `unittest` framework.

* **Targeted Tests:** Configured inside `test_my_io.py` to assert correct behavior over data streams, text sanitization logic, and file boundaries.
* **Coverage Verification:** System behavior paths are verified via global `.coveragerc` and compiled `htmlcov` rules, ensuring execution paths across data modules are comprehensively validated against regression.

## 📊 Outputs Generated
The script processes raw genomic text entries to produce production-ready intelligence inside the `/OUTPUT` directory:
* `intersection_output.txt`: An alphabetically sorted, deduplicated target list of shared genes.
* `categories.txt`: A clean metric index mapping out genetic classifications alongside their total computed frequency counts.
