# pred-analytics-paym-dflts
Machine Learning: Predicting payment defaults (predictive analytics)

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

Sponsor:  Large communication, IT and entertainment company
Year:     2019

Sometimes customers make purchases the they cannot or do not want to pay for. This leads to a direct loss of money for the the company (project sponsor). In order to minimize such bad debts, a machine learning model was implemented in SAP HANA. This model predicts the likelihood of bad debts based on customer demographics and transactions made. Based on the the result, measures may be taken (e.g. lowder purchase limit).

Goals:
- Build, train and compare different machine learning models
- Compare best model to existing SAP HANA model (ROC-AUC score)
- Create new features (feature engineering)

### Workflow:
![alt text](https://github.com/0LIFR1/pred-analytics-paym-dflts/blob/main/workflow.png)

Supervised Learning and Binary Classification


### Initial Data Preparation
Main findings and tasks:


### Analysis and Preprocessing
Main findings and tasks:
* Highly imbalanced dataset (only 1.14% belong to minority class / do not pay)
* Data quality not ideal, lots of time spent on data analysis and data cleaning
* Removing transaction duplicates
* Deleting various features, also to avoid data leakage
* Grouping and Binning (e.g. languages -> DE, FR, EN, IT and OTHER)
* Feature engineering
* Various aggregations (mean, sum, max, min values)
* Various One-Hot or Binary encodings
* Joining Demographis, Data and Merchants files into one training and test data set

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
* Confusion Matrix
* Precision 0.83, Recall 0.61, F1 Score 0.7
* Model predicts in 83% of all cases class 1 correctly and 61% of the class 1 cases
* ROC-AUC score 0.88 (SAP HANA 0.85)
* Might not be best evaluation metric for this case (Precision and Recall might be more meaningful)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- BUILT WITH -->
## Built With

* [![Next][Next.js]][Next-url]
* [![React][React.js]][React-url]
* [![Vue][Vue.js]][Vue-url]
* [![Angular][Angular.io]][Angular-url]
* [![Svelte][Svelte.dev]][Svelte-url]
* [![Laravel][Laravel.com]][Laravel-url]
* [![Bootstrap][Bootstrap.com]][Bootstrap-url]
* [![JQuery][JQuery.com]][JQuery-url]

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
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vue.js]: https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D
[Vue-url]: https://vuejs.org/
[Angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[Angular-url]: https://angular.io/
[Svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[Svelte-url]: https://svelte.dev/
[Laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[Laravel-url]: https://laravel.com
[Bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[Bootstrap-url]: https://getbootstrap.com
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com 
