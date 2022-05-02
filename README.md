# OFDClean

## 1. Overview
OFDClean is a framework for holistically finding a set of minimal repairs such that data satisfies the given Ontology Functional Dependencies (OFDs) w.r.t. the modified ontologies.

## 2. Datasets
We use two real datasets for OFDClean:

<a href="https://www.kaggle.com/datasets/kiva/data-science-for-good-kiva-crowdfunding?select=loan_themes_by_region.csv">Kiva</a>: Kiva database describes loans issued over two years via the Kiva.org online crowdfunding platform to financially excluded citizens around the world. There are 670K records and 15 attributes,  including loan principal amount, loan activity, country code, country, region, funded time and usage.

<a href="https://arxiv.org/pdf/0908.0567.pdf">Clinical</a>: The Linked Clinical Trials (LinkedCT.org) database describes clinical patient data characteristics such as the clinical study, country, countrycode, medical diagnosis, medicine, disease, symptoms, treatment, and outcomes. We use a portion of the dataset with 250K records and 15 attributes.

<a href="https://github.com/zzheng0620/OFDClean/blob/master/Python/datasets/data.csv">Sample Data</a>: The subset of Clinical data with 7 attributes and 40 records: id, countrycode, country, disease, medicine, symptoms, clinical study. The ontology with senses and OFDs for the Sample data are shown at <a href="https://github.com/zzheng0620/OFDClean/tree/master/Python/datasets/senses/clinical">Senses</a> and <a href="https://github.com/zzheng0620/OFDClean/blob/master/Python/datasets/OFDs.txt">OFDs</a>, respectively. The following table shows some example records of Sample Data.

| id        | countrycode      | country  | symptoms        | disease      | medicine  |
| ------------- |-------------| ------------| ------------- |-------------| ------------|
|       1 |      US | USA |  joint pain | osteoarthritis | ibuprofen |
|        2 |      IN | India | joint pain  | osteoarthritis | NSAID  |
|       3 |     CA | Canada | joint pain  | osteoarthritis | naproxen |
|        4 |      IN | Bharat | nausea  | migraine |  analgesic  |
|        5 |       US | America | nausea  | migraine |  tylenol |
|        6 |      US | USA |  nausea  |  migraine |  acetaminophen |
| ... ...     | ... ...  |   ... ...    | ... ...     | ... ...  |   ... ...    |


## 3. Getting Started
The code consists of two parts: Python code and Java code, which focuses on sense assignment and repair, respectively. <br>

Sense assignment ([Python code](https://github.com/ltzheng/OFDClean/tree/master/Python/)): (1) assigns initial sense for each equvilence class, and (2) refines the local sense for each equvilence class to achieve global sense assignment. <br>

Data and ontology repair ([Java code](https://github.com/ltzheng/OFDClean/tree/master/Java/)): (1) finds the ontology repair candiates, (2) for each k-combinations of candiates, computes the minimal data repair by beam search algorithm, and (3) reports the Pareto-optimal solution for data and ontology repair.


### 3.1 Prerequisites
Java v1.8 <br>
Python 3.6 <br>

### 3.2 Sense Assignment

Put the OFDs (OFDs.txt), dataset (data.csv), and ontology with senses (medicine.csv) in the following directory. Note: Input data should align with the format in directory. <br>
```Bash
$ ../OFDClean/tree/master/Python/datasets
```

Onfigure the path of data, OFDs, and senses in the main file. <br>
```Bash
$ ../OFDClean/blob/master/Python/main.py
```

Run `main.py`. <br>
```Bash
$ python main.py
```

Sense assignment result `senses.txt` can be found at `/OFDClean/tree/master/Python/output`.<br>
For example, sense assignment result of Sample data is shown as follows:

| equivalence class (tuple id)       | sense     |
| ------------- |-------------|
| {2,14,15,33}	|FDA|
| {11,12,13,19,20,24,27,28,35,37,39,40}	|FDA|
| {1,3,5,6,7,8,9,10,16,21,29,32}	|MoH|
| {4,17,18,22,23,25,26,30,31,34,36,38}	|FDA|
| {2,11,12,13,14,15,19,20,24,27,28,33,35,37,39,40}     | FDA |

### 3.3 Data and Ontology Repair
Put the OFDs (OFDs.txt), dataset (data.csv), ontology with senses (ontology.csv), and the sense assignment for each equvilence class (senses.txt) in the following directory. Note: Input data should align with the format in directory. <br>
```Bash
$ ../OFDClean/tree/master/Java/data
```

Onfigure the path of data, OFDs, and senses in the main file. <br>
```Bash
$ ../OFDClean/tree/master/Java/src/AppMain.java
```

Run `AppMain.java` in IDE or in command line. <br>
```Bash
$ java -jar AppMain.jar
```

## 4. Source code

The source code is available at https://github.com/mac-dsl/OFDClean. 

## 5. References
[1] S. Baskaran, A. Keller, F. Chiang, L. Golab, and J. Szlichta. Efficient discovery of ontology functional dependencies. In CIKM, pages 1847–1856, 2017. <br>
[2] Z. Zheng, L. Zheng, M. Alipour, F. Chiang, L. Golab, J. Szlichta, S. Baskaran, and A. Keller. Contextual data cleaning with ontology functional dependencies. ACM Journal of Data and Information Quality (JDIQ), 25 pages, 2022.<br>
[3] Z. Zheng. Contextual data cleaning with ontology FDs. In Proceedings of the 2021 ACM SIGMOD International Conference on Management of Data, pages
2911–2913, 2021. <br>
[4] M. Alipour, Z. Zheng, F. Chiang, L. Golab, and J. Szlichta. Contextual data cleaning. 2018 IEEE 34th International Conference on Data Engineering (ICDE), pages 21–24, 2018. <br>
[5] Z. Zheng, M. Alipour, Z. Qu, I. Currie, F. Chiang, L. Golab, and J. Szlichta. Fastofd: Contextual data cleaning with ontology functional dependencies. 21st International Conference on Extending Database Technology (EDBT), pages 694–697, 2018. <br>
[6] O. Hassanzadeh, A. Kementsietsidis, L. Lim, R. J. Miller, and M. Wang. 2009. LinkedCT: A Linked Data Space for Clinical Trials. Technical Report CSRG-596. University of Toronto. <br>
[7] Kiva. Data science for good: Kiva crowdfunding. https://www.kaggle.com/datasets/kiva/data-science-for-good-kiva-crowdfunding?select=loan_themes_by_region.csv <br>
[8] National Library of Medicine. Biomedical terminology, ontologies. https://mor.nlm.nih.gov, 2016.
