# BLEGroupID
The Github repository contains the following:
- The labeling, preprocessing and modeling scripts used in the thesis
- The most relevant plots used in the thesis
- This README file and a requirements.txt file to help install libraries and provie guidance
- The mid-term and final presentation slides
### **The code sections which actually run code and perform an action are commented at the top of the respective code box in the Juypter notebooks with: "Code Field X"**

All other code boxes only define methods or variables but do not directly execute any code.
To install the libraries needed to run the scripts, simply run:

`pip install -r requirements.txt`

Python 3.12 is required to run the code locally.

## Labeling scripts (dataset_labeling_samsung.ipynb, dataset_labeling_apple.ipynb):
These scripts require a raw dataset with a defined path. Certain parameters, such as the labeling conditions for the phone, may depend on the dataset. These variables are commented directly in the code to indicate how and when to adjust them. The already labeled datasets are available via Nextcloud. 
Below, the code fields and their purpose are explained:

- **Code Field 0**: Defines global variables. Must be run before labeling a new dataset to reinitialize parameters.
- **Code Field 1**: Reads the raw dataset, initializes tracking variables/lists, assigns labels, and drops malformed packets.
- **Code Field 2**: Reassigns sources based on revised labeling conditions.
- **Code Field 3**: Final evaluation check; prints label distribution and verifies there are no duplicate source labels.
- **Code Field 4**: Removes remaining noise sources from interference-free datasets. Writes the updated dataframe to file.

## Modeling scripts (modeling_samsung.ipynb, modeling_apple.ipynb):
These scripts load labeled datasets, apply preprocessing, perform modeling, and generate evaluations. The notebook generally follows a top-down flow. Not all sections must be executed; some (e.g., learning curves) are optional. Code is extensively commented for guidance. 
Below is an overview of the code fields:

- **Code Field 1**: Loads datasets, encodes dummy columns, and calculates aggregated source features.
- **Code Field 2**: Adds time-based features of packet occurrences within defined windows.
- **Code Field 3**: Bins columns and balances packet counts per source address.
- **Code Field 4**: Creates a 2:1 noise-to-target version of the evaluation dataset.
- **Code Field 5**: Prints average column cardinalities for training vs. evaluation sets.
- **Code Field 6**: Runs supervised models (e.g., RF, MLP), including training, evaluation, and plotting.
- **Code Field 7**: Plots learning curve for non-split training of the RF model.
- **Code Field 8**: Plots learning curve for source-split training of the RF model.
- **Code Field 9**: Runs unsupervised models to find best parameters or top-performing models.
- **Code Field 10**: Analyzes clustering results, extracts detected target devices and their company IDs.
- **Code Field 11.1**: Plots cluster ground truth vs. correct/incorrect label assignments.
- **Code Field 11.2**: Plots cluster ground truth vs. correct/incorrect label assignments in four separate subplots. Useful if the data is dense and overlaps.
- **Code Field 12.1**: Visualizes a single target device highlighted in the cluster.
- **Code Field 12.2**: Visualizes a single target device highlighted in the cluster, each visualization split into two subplots. Useful if the data is dense and overlaps.
- **Code Field 13**: Visualizes a single target device highlighted in the cluster together with correct/incorrect label assignment.

