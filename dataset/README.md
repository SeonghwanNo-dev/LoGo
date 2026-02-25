# LoGo Dataset Analysis with Flan v2

This directory is designed to analyze the correspondence between the datasets used in the **LoGo (LoRA on the Go)** paper and the **Google Flan v2 (Flan 2022) collection**, specifically focusing on validating task matching through `SeqIO`.

## 📁 Directory Structure

```text
.
├── dataset_list.txt         # List of datasets addressed in the LoGo paper
├── dataset/
│   ├── data/                # Directory for path adjustment to import the flan library
│   ├── flan/                # Active flan package (restructured from the original Flan/flan/...)
│   ├── flan_original/       # Original flan repository structure prior to modification
│   ├── test_1/              # Test 1: Script to contrast LoGo datasets with flan/v2/tasks
│   ├── test_2/              # Test 2: Script to contrast LoGo datasets with flan_collection_info.csv
│   └── test_3/              # Test 3: Analysis of datasets matched at test_2 but inconsistent with flan/v2/tasks
├── matching_result_1        # Output result from Test 1
├── matching_result_2        # Output result from Test 2
└── matching_result_3        # Output result from Test 3

```

---

## 🧪 Test Descriptions

### **Test 1: Tasks vs. LoGo Datasets**

* **Objective**: Verify if the datasets specified in the LoGo paper match the `SeqIO` Tasks defined in `flan/v2/tasks.py`.
* **Details**: Analyzes the mapping between the official `SeqIO` Task Names and the dataset nomenclature used in the paper.

### **Test 2: Collection Info vs. LoGo Datasets**

* **Objective**: Determine the presence of LoGo datasets based on the Flan v2 metadata file, `flan_collection_info.csv`.
* **Details**: Conducts a statistical comparison between the "Source Dataset" field in the CSV and the entries in `dataset_list.txt`.

### **Test 3: Deep Discrepancy Analysis**

* **Objective**: Investigate exception cases where a dataset is matched in `test_2` (metadata level) but differs in its actual implementation or application within `flan/v2/tasks`.
* **Details**: Extracts and describes datasets that exist in the metadata but have task definitions (prompts, options, or shot-settings) that deviate from the LoGo paper's methodology.

---

## 🛠 Library Setup (Path Manipulation)

To ensure the `import flan` statement works correctly within the Python environment, the following structural adjustments were made:

1. **Original Structure**: `Flan/flan/v2/...`
2. **Modified Structure**:
* The nested `flan/` subdirectory was moved to the root level as `dataset/flan/`.
* The original top-level directory was renamed to `dataset/flan_original/` for archival purposes.


3. **Result**: By configuring the `sys.path`, the environment can successfully execute `import flan.v2` to access `SeqIO` Task and Mixture definitions.

---

## 📊 Results Summary

* Detailed outputs for each test are documented in the respective `matching_result_x` files.
* **Matching Result 1**: Records direct matching success rates at the Task level.
* **Matching Result 2**: Confirms inclusion based on the collection metadata.
* **Matching Result 3**: Specifies datasets with implementation inconsistencies between the paper and Flan v2.

---

