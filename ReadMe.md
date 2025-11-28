# DATA EXTRACTION
## Conference Websites
For the following conferences, the data extraction is done from the HTML tags of static websites, using the BeautifulSoup library. The year-wise data of Paper titles, Paper Abstract, List of Authors and their affiliations (if available) are collected.
- Coling (2024-2025)
- KDD (2023-2025)
- ACL (2023-2025)<br>
<p> An illustration is shown below, for the KDD 2023 conference website. The similar process is followed for the 7 other websites. </p>

 - **STEP 1** <br>
   Search for accepted papers' list in KDD 2023 and get the correct website URL. The following link contains the list of all accepted papers in KDD 2023 : https://kdd.org/kdd2023/research-track-papers/index.html

- **STEP 2**
  <img width="1911" height="885" alt="image" src="https://github.com/user-attachments/assets/a6f05936-a999-4ce6-9783-f081208d110d" />
  <br> Right-click on the desired section of the website and click on Inspect. The "Elements" tab opens by default with the html tag highlighted, that contains the desired section of the website.

- **STEP 3** <br>
  Observe the html tags that contain all the desired information. Use BeautifulSoup library to script the extraction and storage of this information. Use the following code snippet to install and use BeautifulSoup library in python.

  ``` python
  !pip install BeautifulSoup
  import BeautifulSoup
  ```

For the following conferences, the websites containing accepted papers' details are dynamic, i.e., the data is not directly stored in the HTML tags. The data resides in the backend, in the form of JSON, which is rendered into the frontend, using Javascript.
- CVPR (2023 - 2025)
- AAAI (papercopilot github : 2023 - 2025)

## arXiv Website
The arXiv website is a static website. <img width="830" height="30" alt="image" src="https://github.com/user-attachments/assets/f6244e75-9872-4526-8e77-a07f11a9345a" /> <br>
This is the URL when a specific paper is searched by title. The paper titles are re-formatted using string formatting to update the search URL for every paper. The website is inspected in similar fashion to look for HTML tags that contain "Submitted/v1 submitted/originally announce".

## OpenReview Website
The data for the following conferences are collected from OpenReview, which is a dynamic website. The details in this website are rendered from data stored as JSON in the backend, using JavaScript. 
- ICLR (2023-2025)
- ICML (2023-2025)
- NeurIPS (2023-2024)
<br> To access the endpoint API URL that directs to this JSON databse, the following steps need to be followed. The illustration is being shown for ICLR 2025. Similar process is being followed for the remaining 7 websites.
 - **STEP 1**
   <br> <img width="1818" height="888" alt="image" src="https://github.com/user-attachments/assets/c614d9bd-9daf-4159-b594-bc6bc1870552" />
   Right click on the desired conference website, of a specific year, and a specific recommendation category. Click on inspect.
   
 - **STEP 2**
   <br> <img width="1915" height="707" alt="image" src="https://github.com/user-attachments/assets/4fa0900a-139f-45c1-9d84-dc376a2f1f63" />
   Navigate to the "Networks" tab. Press Ctrl+R to reload the page.

 - **STEP 3**
   <br> <img width="1024" height="714" alt="image" src="https://github.com/user-attachments/assets/67afa238-1ac7-4325-a68e-1cd70aebeed4" />
   Look for the endpoint API URL, redirecting to the JSON database, for the desired recommendation category. The entire data is split into offsets, for rendering across multiple pages on the frontend. Note the number of pages in each category and update offset in the URL, using string formatting to download the JSON.

 - **STEP 4**
   <br> Use the authorids in this json to collect author information like name and affiliation details. Use the forumid in this json, to extract review data as JSON, against each paper.


# DATASET STATISTICS

The dataset extraction statistics have been provided in the following table.


| Conference | Data source                             | Review Data       | Collection method | Raw format | 2023                                                                                                                                                                     | 2024                                                                                                                                                          | 2025                                                                                                                         | Call for Papers | Review Deadlines | Output format | Affiliations available |
| ---------- | --------------------------------------- | ------------------------- | ----------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ------------- | --------------- | ------------- | ----------------- |
| ICML       | OpenReview                              | available from 2025<br>No | done by title     | csv        | accept (poster) : 1673<br>accepted (oral & poster) : 155                                                                                                                           | accept (oral) : 144<br>accept (poster) : 2275<br>accept (spotlight) : 191                                                                                               | accept (oral) : 108<br>accept (poster) : 2938<br>accept (spotlight) : 211<br>rejected : 162<br>retracted acceptance : 3                | TRUE          | TRUE            | csv           | TRUE              |
| ICLR       | OpenReview                              | 2023 collected            | done by title     | csv        | poster : 1202<br>submitted : 2220<br>withdrawn/rejected : 1144<br>top 25% : 281<br>top 5% : 90                                                                                     | accept (oral) : 86<br>accept (poster) : 1807<br>accept (spotlight) : 367<br>rejected : 3433<br>withdrawn : 1658<br>desk rejected : 52                                   | accept (oral) : 213<br>accept (poster) : 3111<br>accept (spotlight) : 380<br>rejected : 4914<br>withdrawn : 2984<br>desk rejected : 70 | TRUE          | TRUE            | csv           | TRUE              |
| NeurIPS    | OpenReview                              | 2023 collected            | done by title     | csv        | accept (oral) : 67<br>accept (poster) : 2773<br>accept (spotlight) : 378<br>rejected : 176                                                                                         | accept (oral) : 61<br>accept (poster) : 3648<br>accept (spotlight) : 326<br>rejected : 201                                                                              | No data                                                                                                                                | TRUE          | TRUE            | csv           | TRUE              |
| KDD        | website                                 | No                        | done by title     | csv        | 313                                                                                                                                                                                | 411                                                                                                                                                                     | 552                                                                                                                                    | TRUE          | TRUE            | csv           | TRUE              |
| CVPR       | website                                 | No                        | done by title     | csv        | 2359                                                                                                                                                                               | 2806                                                                                                                                                                    | 2966                                                                                                                                   | TRUE          | TRUE            | csv           | TRUE              |
| ACL        | website                                 | No                        | done by title     | csv        | 1074                                                                                                                                                                               | 941                                                                                                                                                                     | 1701                                                                                                                                   | TRUE          | TRUE            | csv           | FALSE             |
| EMNLP      | website                                 | No                        | done by title     | csv        | awards : 23<br>industry accepted : 74<br>long papers : 898<br>long papers findings : 853<br>short papers : 144<br>short paper findings : 196<br>system demonstration accepted : 51 | awards : 23<br>accepted papers findings : 993<br>industry accepted : 121<br>main conference accepted : 1256<br>tacl accepted : 32<br>system demonstration accepted : 50 | 3304 (Main Conference + Findings)                                                                                                      | TRUE          | TRUE            | csv           | FALSE             |
| Coling     | website                                 | No                        | done by title     | csv        | No Data                                                                                                                                                                            | 1556                                                                                                                                                                    | awards : 15<br>industry track accepted : 69<br>long : 650<br>short : 93<br>sytem demo acc : 20                                         | TRUE          | TRUE            | csv           | FALSE             |
| AAAI       | paper copilot<br>github endpoint<br>API | No                        | done by title     | csv        | 1721                                                                                                                                                                               | 2342                                                                                                                                                                    | 3032                                                                                                                                   | TRUE          | TRUE            | csv           | TRUE              |



# DATA TRANSFORMATION
Flat JSON can be converted to csv format using the following lines of code.

``` python
import json
import pandas as pd

with open("path/to/downloaded.json", "r") as file:
    data = json.load(file)

df = pd.Dataframe(data)
df.to_csv("output.csv", index = False)
```

To convert nested JSON to csv, access only the necessary fields using keywords and write onto a new csv file.

# DATA CLEANING AND PROCESSING
In order to visualize insights from the extracted data, the data needs to be cleaned by dropping duplicate indexing columns and dropping entries with `NaN` values. 
For joining multiple tables, use `df = pandas.merge(df1, df2, on = "<column name to match>", how = "left"`.
For merging multiple csv-s into 1. use `df = pandas.concat(df1, df2, index = False`.

<p> Load this processed data and use the following libraries to visualize insights from the collected data. <br>
  
  ```  python
  import matplotlib.pyplot as plt
  import numpy as np
  import pandas as pd
  import seaborn as sns
  from scipy.interpolate import make_interp_spline
  ```
</p>

# HYPOTHESIS TESTING : CHI - SQUARED TEST

Chi-squared hypothesis testing is used to determine if there is a statistically significant difference between observed data and expected data, helping to see if two categorical variables are independent or related. It is a non-parametric test that analyzes categorical data to assess the goodness of fit (how well a sample distribution matches an expected distribution) or to test for independence between two variables.

## Test 1 : 
Submitting to arXiv makes any difference to papers getting accepted, irrespective of the time-frame​.

The code snippet for this test is as follows :

``` python
from scipy.stats import chi2, chi2_contingency

data = pd.DataFrame({'Accepted': [sum(ICLR2023)+sum(NIPS2023), ICLR[-3]+NeurIPS[-3]-sum(ICLR2023)-sum(NIPS2023)], 'Rejected': [sum(ICLR2023rej)+sum(NIPS2023rej), 1144+176-sum(ICLR2023rej)-sum(NIPS2023rej)]}, #keep changing the number of entries
                    index=["on Arxiv (before Review Deadline)", "not on Arxiv(before Review deadline)"])

print(data)

# Perform Chi-Squared Test
chi2_statistic, p, dof, expected = chi2_contingency(data)
log_p = chi2.logsf(chi2_statistic, dof)

print("Chi-Squared Statistic:", chi2_statistic)
print("Degrees of Freedom:", dof)
print(f"p-value:, {p:.50e}")
print("log p-value : ", log_p)
print("Expected Frequencies:\n", expected)
```

The contigency table is as follows :

```
                                        Accepted  Rejected
on Arxiv (before Review Deadline)         
not on Arxiv(before Review deadline)      
```

## Test 2 : 
Submitting to arXiv before Review Deadline makes any difference to papers getting accepted, irrespective of the time-frame​.

The code snippet for this test is as follows :

``` python
from scipy.stats import chi2, chi2_contingency

data = pd.DataFrame({'Accepted': [ICLR2023[0]+NIPS2023[0], ICLR[-3]+NeurIPS[-3]-ICLR2023[0]-NIPS2023[0]], 'Rejected': [ICLR2023rej[0]+NIPS2023rej[0], 1144+176-ICLR2023rej[0]-NIPS2023rej[0]]}, #keep changing the number of entries
                    index=["on Arxiv (before Review Deadline)", "not on Arxiv(before Review deadline)"])

print(data)

# Perform Chi-Squared Test
chi2_statistic, p, dof, expected = chi2_contingency(data)
log_p = chi2.logsf(chi2_statistic, dof)

print("Chi-Squared Statistic:", chi2_statistic)
print("Degrees of Freedom:", dof)
print(f"p-value:, {p:.50e}")
print("log p-value : ", log_p)
print("Expected Frequencies:\n", expected)
```

The contigency table is as follows :

```
                                      Accepted  Rejected
on Arxiv (between CfP to Review)         
not on Arxiv(between CfP to Review)      
```
