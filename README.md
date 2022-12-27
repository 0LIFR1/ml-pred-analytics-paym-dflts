# Predicting payment defaults (machine learning)

<a name="readme-top"></a>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->


<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>    
    <li>
      <a href="##about-the-project">About The Project</a>
      <ul>
        <li><a href="#workflow">Workflow</a></li>
        <li><a href="#data">Data</a></li>
        <li><a href="#initial-data-preparation">Initial Data Preparation</a></li>        
        <li><a href="#analysis-and-preprocessing">Analysis and Preprocessing</a></li>
        <li><a href="#models-and-training">Models and Training</a></li>
        <li><a href="#evaluation">Evaluation</a></li>
      </ul>
    </li>    
    <li><a href="#built-with">Built With</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
  </ol>
</details>


<!-- ABOUT THE PROJECT -->
## About The Project

Sponsor / client: Large communication, IT and entertainment company<br>
Staus: Test

**Summary**:<br>
Sometimes customers make purchases the they cannot or do not want to pay for. This leads to a direct loss of money for the the company (project sponsor). In order to minimize such bad debts, a machine learning model was implemented in SAP HANA. This model predicts the likelihood of bad debts based on customer demographics and transactions made. Based on the the result, measures may be taken (e.g. lower purchase limit).

Goals:
- Build, train and compare different machine learning models
- Compare best model to existing SAP HANA model (ROC-AUC score)
- Create new features (feature engineering)

Machine learning algorithm:
- Binary classification / supervised learning

### Workflow
End-to-end project workflow:
![alt text](https://github.com/0LIFR1/pred-analytics-paym-dflts/blob/main/workflow.png)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Data
Relevant data is exported from the company's datawarehouse into three files

| File | No. of attr. | No. of rec |
| --------------- | --------------- | --------------- |
| Data (transactions) | 4 | > 28 mio |
| Demographics (customer information) | 62 | > 500 k |
| Merchants (merchants information) | 3 | 595 |


### Initial Data Preparation
Main findings and tasks:
* Initial preparation in RStudio (headers, regex)
* Export as csv files for further processing

### Analysis and Preprocessing
Main findings and tasks:
* Highly imbalanced dataset (only 1.14% belong to minority class)
* Data quality not ideal, lots of time spent on data analysis and data cleaning
* Removing transaction duplicates
* Deleting various features, also to avoid data leakage
* Grouping and Binning (e.g. languages -> DE, FR, EN, IT and OTHER)
* Feature engineering
* Various aggregations (mean, sum, max, min values)
* Various One-Hot or Binary encodings
* Joining demographis, data and merchants files into one training and test data set

### Models and Training
Main findings and tasks:
* Training various models / classifiers:
  * Random Forest Classifier
  * Decision Tree Classifier
  * Logistic Regression
  * K-Nearest Neighbors
  * AdaBoost
* High score but poor prediction of minority class
* Imbalanced class distribution requires re-sampling
* Class weight, down sampling of majority class and Synthetic Minority Over-sampling Technique (SMOTE) tested
* Better prediction of minority class prioritized -> avoid reputation damage (false positive cases) 
* Final model: Logistic Regression combined with SMOTE
* Hyperparameter tuning using GridSearchCV

### Evaluation
Main findings and tasks:
* Logistic regression seems to perform best
* Precision 0.83, Recall 0.61, F1 Score 0.7
* ROC-AUC score 0.88 (SAP HANA 0.85)
* ROC-AUC Might not be best evaluation metric for this case (precision and recall might be more meaningful)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- BUILT WITH -->
## Built With

[![Python][python-shield]][python-url] [![RStudio][rstudio-shield]][rstudio-url] [![Jupyter][jupyter-shield]][jupyter-url]\
[![Scikit-learn][scikit-learn-shield]][scikit-learn-url] [![Pandas][pandas-shield]][pandas-url] [![Numpy][numpy-shield]][numpy-url] [![Matplotlib][matplotlib-shield]][matplotlib-url]

<!-- Logo examples
<div>
	<code><img height="50" src="https://user-images.githubusercontent.com/25181517/183914128-3fc88b4a-4ac1-40e6-9443-9a30182379b7.png" alt="Jupyter Notebook" title="Jupyter Notebook" /></code>
	<code><img height="50" src="https://user-images.githubusercontent.com/25181517/183423507-c056a6f9-1ba8-4312-a350-19bcbc5a8697.png" alt="Python" title="Python" /></code>
</div>
-->

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- ROADMAP -->
## Roadmap
There is still room for improvement :-), some ideas:

* Further data analysis, esp. correlation
* Additional Feature Engineering, e.g.: Transactions weekday and time of day (morning, afternoon, etc.)
* Customer location (evaluate x/y coordinates)
* Merchant industrial sector (e.g. public transport)
* PCA
* Cross Validation
* Test more re-sampling methods
* Embedding vs. One-Hot encoding for high cardinality features
* Try unsupervised learning (not sure if result would be better but worth a try)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/github_username/repo_name.svg?style=for-the-badge
[contributors-url]: https://github.com/github_username/repo_name/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[stars-shield]: https://img.shields.io/github/stars/github_username/repo_name.svg?style=for-the-badge
[stars-url]: https://github.com/github_username/repo_name/stargazers
[issues-shield]: https://img.shields.io/github/issues/github_username/repo_name.svg?style=for-the-badge
[issues-url]: https://github.com/github_username/repo_name/issues
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[product-screenshot]: images/screenshot.png
[rstudio-shield]: https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white
[rstudio-url]: https://posit.co/
[jupyter-shield]: https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white
[jupyter-url]: https://jupyter.org/
[python-shield]: https://img.shields.io/badge/Python-FFD43B?style=for-the-badge&logo=python&logoColor=blue
[python-url]: https://www.python.org/
[scikit-learn-shield]: https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white
[scikit-learn-url]: https://scikit-learn.org/stable/
[pandas-shield]: https://img.shields.io/badge/Pandas-2C2D72?style=for-the-badge&logo=pandas&logoColor=white
[pandas-url]: https://pandas.pydata.org/docs/index.html
[numpy-shield]: https://img.shields.io/badge/Numpy-777BB4?style=for-the-badge&logo=numpy&logoColor=white
[numpy-url]: https://numpy.org/
[matplotlib-shield]: https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black
[matplotlib-url]: https://matplotlib.org/
