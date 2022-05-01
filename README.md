# OFDClean

## 1. Overview
OFDClean is a framework for holistically finding a set of minimal repairs such that data satisfies the given Ontology Functional Dependencies (OFDs) w.r.t. the modified ontologies.

## 2. Datasets

Dataset, ofds, senses of clinical data of [Python code](https://github.com/ltzheng/OFDClean/tree/master/Python/datasets) and [Java code](https://github.com/ltzheng/OFDClean/tree/master/Java/data). 

We use two real datasets for OFDClean:

<a href="https://www.kaggle.com/datasets/kiva/data-science-for-good-kiva-crowdfunding?select=loan_themes_by_region.csv">Kiva</a>: Kiva database describes loans issued over two years via the Kiva.org online crowdfunding platform to financially excluded citizens around the world. There are 670K records and 15 attributes,  including loan principal amount, loan activity, country code, country, region, funded time and usage.

<a href="https://arxiv.org/pdf/0908.0567.pdf">Clinical</a>: The Linked Clinical Trials (LinkedCT.org) database describes clinical patient data characteristics such as the clinical study, country, countrycode, medical diagnosis, medicine, disease, symptoms, treatment, and outcomes. We use a portion of the dataset with 250K records and 15 attributes.

<a href="https://github.com/zzheng0620/OFDClean/blob/master/Python/datasets/data.csv">Sample Data</a>: The subset of Clinical data with 7 attributes and 3394 records: id, countrycode, country, disease, medicine, status, clinical study. The following table shows 5 records as an example:

| id        | countrycode      | country  | disease      | medicine  | status | clinical study
|------------- |-------------| ------------| ------------- |-------------| ------------| ------------|
|1	        |CA		        |Canada		        |asthma		        |Advair		        |complete		        |research
|2		        |CANADA	     |Canada		        |asthma		        |Advair		        |active		        |clinical
|3		        |GER		       |Germany		        |asthma		        |Advair		        |active		        |clinical
|4		        |GERMANY		   |Germany		        |asthma		        |Advicor		        |active		        |clinical
|5		        |DE		        |Germany		        |asthma_attacks		|Advair		        |active		        |clinical
| ... ...     | ... ...  |   ... ...    | ... ...     | ... ...  |   ... ...    |   ... ...    |

The ontology with senses and OFDs for the Sample data are shown at <a href="https://github.com/zzheng0620/OFDClean/tree/master/Python/datasets/senses/clinical">Senses</a> and <a href="https://github.com/zzheng0620/OFDClean/blob/master/Python/datasets/clinical.csv">OFDs</a>, respectively.


## 3. Getting Started
The code consists of two parts: Python code and Java code. <br>

Python code: (1) assigns initial sense for each equvilence class (eq), and (2) refines the local sense for each eq to achieve global sense assignment. <br>

Java code: (1) finds the ontology repair candiates, (2) for each k-combinations of candiates, compute the minimal data repair by beam search algorithm, and (3) report the Pareto-optimal solution for data and ontology repair.


### 3.1 Prerequisites
Java v1.8 <br>
Python 3.6 <br>

### 3.2 Prerequisites

Input data should align with the format in directory `datasets`

onfigure the path of data, OFDs, and senses in `main.py`, then run `python main.py`.

 Python code 

- Initial sense assignment
- Local sense refinement
- Provided by Longtao Zheng


 Java code 

- Repair data by beam search
- Provided by Zheng Zheng


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




# CurrentClean

## 2. Datasets

We use four real data collections. The table below gives the data characteristics, showing a range of data sizes w.r.t. the number of entities (N ), number of attributes n, number of cells (|D|), and number of updates (|H|).

<table style="text-align: left; width: 674px; height: 60px;" border="1" cellspacing="2" cellpadding="2">
<tbody>
<tr>
<td>&nbsp;</td>
<td>Mimic</td>
<td>Sensor</td>
<td>Trans</td>
<td>NBA</td>
</tr>
<tr>
<td>N</td>
<td>60,000</td>
<td>58</td>
<td>256,000</td>
<td>3,000</td>
</tr>
<tr>
<td>n</td>
<td>27</td>
<td>4</td>
<td>6</td>
<td>44</td>
</tr>
<tr>
<td>|D|</td>
<td>1,620,000</td>
<td>232</td>
<td>1,280,000</td>
<td>1,320,000</td>
</tr>
<tr>
<td>|H|</td>
<td>2,438,327</td>
<td>117,323</td>
<td>5,035,648</td>
<td>2,074,356</td>
</tr>
</tbody>
</table>

### 2.1 Sensor
We collected sensor readings from a corporate data center reporting temperature, humidity, air pressure and voltage (approximately every 20s) on server racks over a week. We consult with domain experts who provided expected update dependencies between attributes (e.g., humidity changes cause a change in temperature), and acceptable domain attribute values (e.g., temp ranges in the data center). These dependencies and domain ranges serve as ground truth to evaluate CurrentClean's comparative accuracy and performance. The dataset can be found at <a href="http://www.cas.mcmaster.ca/~zhengz13/Dataset/Sensor.rar" download="Sensor.rar">Sensor</a>. The ground truth can be found at <a href="http://www.cas.mcmaster.ca/~zhengz13/Sensor-GroundTruth.pdf">Sensor-GroundTruth.pdf</a>.

### 2.2 Mimic
<p>The Mimic database contains hospital data for 60,000 patients describing vital signs, lab tests, and medications. Researchers seeking to use the database must formally request access with the steps in <a href="https://mimic.physionet.org/gettingstarted/access/">MimicAccess</a>. We use a subset of the dataset and extract the update history over these values for one week by comparing successive data snapshots. The schema and attributes description are shown in <a href="http://www.cas.mcmaster.ca/~zhengz13/Mimic-Schema.xlsx">Mimic-Schema.xlsx</a>.&nbsp;For ground truth (<a href="http://www.cas.mcmaster.ca/~zhengz13/Mimic-GroundTruth.pdf">Mimic-GroundTruth.pdf</a>), we consult with domain experts who provided update relationships that occur between the attributes (e.g., changes in oxygen saturation trigger changes in respiratory rate), along with acceptable attribute domain ranges.</p>

### 2.3 Trans
<p>The&nbsp;<a href="https://archive.ics.uci.edu/ml/datasets/Online%20Retail#">Trans</a> dataset contains customer product purchases for a UK online retailer occurring between 2010 and 2011. The dataset describes 4207 products, and their quantity, price, and date of purchase by 4373 customers from different countries. Due to the variability in update patterns, we use this dataset to evaluate the prevalence of different update patterns and relational chains. A product and customer are considered stale, if there has been no purchase activity for 3 and 6 months, respectively.</p>

### 2.4 NBA
<p>The <a href="http://www.cas.mcmaster.ca/~zhengz13/Dataset/NBA.zip" download="NBA.zip">NBA dataset</a> provides player statistics for 3000 NBA players, and their teams from 1978 to 2016. We extract the updates each year by comparing successive instances, to reflect changes such as player salaries, and trades. We use this dataset to evaluate the prevalence of update patterns and relational chains. The schema can be found at <a href="https://data.world/jgrosz99/nba-player-data-1978-2016/workspace/data-dictionary">NBASchema</a>, and the&nbsp;<a href="https://www.basketball-reference.com/about/glossary.html">Glossary</a> describes each attribute.</p>

## 3. Getting Started
### 3.1 Prerequisites
Java v1.8 <br>
DeepDive v0.8.0 <br>

### 3.2 Install DeepDive
CurrentClean uses DeepDive to extend probabilistic inference with logical reasoning. DeepDive is a new type of data management system that enables one to tackle extraction, integration, and prediction problems in a single system, which allows users to rapidly construct sophisticated end-to-end data pipelines, such as dark data BI (Business Intelligence) systems.<br>

Please follow the steps to launch or install DeepDive: <a href="http://deepdive.stanford.edu/quickstart">DeepDive Quick Start</a>

### 3.3 Preprocess Dataset
Run <a href="https://github.com/zzheng0620/CurrentClean/tree/main/DeepDive">utility.py</a> to generate input files for DeepDive. <br>
Take Sensor dataset (mentioned in Section 2.1) as an example. It generates 5 files as follows: <br>

**cell.tsv**: all the cells in a relation. <br>
| relation_column_attribute        | relation_column      | relation_attribute  |
| ------------- |-------------| ------------|
| Sensor_1_Temperature   | Sensor_1   |   Sensor_Temperature |
| Sensor_1_Humidity      | Sensor_1   |   Sensor_Humidity    |
| Sensor_1_AirPressure   | Sensor_1   |   Sensor_AirPressure |
| Sensor_1_Voltage       | Sensor_1   |   Sensor_Voltage     |
| Sensor_2_Temperature   | Sensor_2   |   Sensor_Temperature |
| ... ...     | ... ...  |   ... ...    |

**lastupd.tsv**: each cell and its last update time. <br>
| relation_column_attribute        | timestamp     |
| ------------- |-------------|
| Sensor_12_Voltage	|1522986490|
| Sensor_29_Voltage	|1522986490|
|Sensor_51_Voltage	|1522986490|
|Sensor_53_Voltage	|1522986490|
| ... ...     | ... ...  |

**probabilistic.tsv**: attribute name in the relation. <br>
| relation_attribute  |
| ------------- |
| Sensor_Temperature|
| Sensor_Humidity|
| Sensor_AirPressure|
| Sensor_Voltage|

**time.tsv**: all the update times in the history. <br>
| timestamp  |
| ------------- |
| 1522986490|
|1522986500|
|1522986510|
|1522986520|
|... ...|

**updated.tsv**: all the updated cells with times in the history. <br>
| relation_column_attribute        | timestamp     |
| ------------- |-------------|
| Sensor_57_Voltage	|1522986490|
|Sensor_8_Voltage	|1522986490|
|Sensor_13_Voltage	|1522986500|
|Sensor_16_Voltage	|1522986500|
| ... ...     | ... ...  |

### 3.4 Learn Update Patterns
Compile with Deepdive. <br>
```Bash
$ deepdive compile #Bash
```
Run with Deepdive. <br>
```Bash
$ deepdive run #Bash
```
Learn model with Deepdive. <br>
```Bash
$ deepdive model learn #Bash
```
Move the output file <a href="https://github.com/zzheng0620/CurrentClean/tree/main/Input">UpdPatterns</a> from folder /CurrentClean/tree/main/DeepDive/Output/ to folder /CurrentClean/tree/main/Input/

### 3.5 Identify and Repair Stale Cells 
Run the Java main code <a href="https://github.com/zzheng0620/CurrentClean/tree/main/src">CurrentClean.java</a> in folder /CurrentClean/tree/main/src/, and find the restults in folder /CurrentClean/tree/main/Output. <br>

Continue with the example of Sensor data, you will find two files as the results: <br>

**stalecells**: all the identified stale cells with stale probabilities.<br>
| stale cell (relation_column_attribute)        | probability     |
| ------------- |-------------|
|Sensor_47_AirPressure| 0.90 |
|Sensor_48_Temperature| 0.84 |
|Sensor_8_Temperature | 0.83 |
|Sensor_9_Humidity    | 0.94 |
|... ...| ... ...|

**repairs**: all the possible repairs and probabilities for each stale cell.<br>
| stale cell (relation_column_attribute)        | value: probability     | value: probability     | value: probability     |
| ------------- |-------------|-------------|-------------|
|Sensor_21_Temperature|27.8: 0.67|27.7: 0.17|28.0: 0.16|
|Sensor_49_Voltage|3.07: 1.0|
|Sensor_6_Humidity|14.2: 0.5|14.6: 0.25|14.4: 0.25|
|Sensor_50_Temperature|22.1: 0.5|22.0: 0.5|
|... ...| ... ...|




