# LoGo Dataset Analysis with Flan v2

This directory is designed to analyze the correspondence between the datasets used in the **LoGo (LoRA on the Go)** paper and the **Google Flan v2 (Flan 2022) collection**

## 📁 Directory Structure

```text
.
├── dataset_list.txt         # List of datasets addressed in the LoGo paper
├── flan/                    # Active flan package (restructured from the original Flan/flan/...)
├── flan_original/           # Original flan repository structure prior to modification
├── data/                    # Directory for path adjustment to import the flan library
├── test_1                   # Test 1: Script to contrast LoGo datasets with flan/v2/tasks
├── test_2                   # Test 2: Script to contrast LoGo datasets with flan_collection_info.csv
├── test_3                   # Test 3: Analysis of datasets matched at test_2 but inconsistent with flan/v2/tasks
├── matching_result_1        # Output result from Test 1
├── matching_result_2        # Output result from Test 2
└── matching_result_3        # Output result from Test 3

```

---

## 🧪 Test Descriptions

### **Test 1: Tasks vs. LoGo Datasets**

* Verify if the datasets specified in the LoGo paper match the `SeqIO` Tasks defined in `flan/v2/tasks.py`.

### **Test 2: Collection Info vs. LoGo Datasets**

* Determine the presence of LoGo datasets based on the Flan v2 metadata file, `flan/v2/flan_collection_info.csv`.

### **Test 3: Deep Discrepancy Analysis**

* Investigate exception cases where a dataset is matched in `test_2` (metadata level) but differs in its actual implementation or application within `flan/v2/tasks`.

---

## 🛠 Library Setup (Path Manipulation)

To ensure the `import flan` statement works correctly within the Python environment, the following structural adjustments were made:

1. **Original Structure**: `./Flan/flan/v2/...`
2. **Modified Structure**:
* `./Flan/flan/` -> `./flan/`
* `./Flan/` -> `./flan_original/`


3. **Result**: By configuring the `sys.path`, the environment can successfully execute `import flan.v2` to access `SeqIO` Task and Mixture definitions.

---

## 📊 Results Summary

* Detailed outputs for each test are documented in the respective `matching_result_x` files.
* **Matching Result 1**: Records direct matching success rates at the Task level.
* **Matching Result 2**: Confirms inclusion based on the collection metadata.
* **Matching Result 3**: Specifies datasets with implementation inconsistencies between the paper and Flan v2.

---

