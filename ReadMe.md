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

# PRE-PRINT POLICIES 
- ICLR : https://iclr.cc/Conferences/2026/AuthorGuide
- NeurIPS : https://neurips.cc/Conferences/2025/CallForPapers
- ICML : https://icml.cc/Conferences/2025/CallForPapers
- AAAI : https://aaai.org/conference/aaai/aaai-25/review-process/
- ACL : https://aclrollingreview.org/anonymity/
- EMNLP : https://2025.emnlp.org/calls/main_conference_papers/
- COLING : https://coling2025.org/calls/main_conference_papers/?utm_source=chatgpt.com#anonymity-period
- KDD : https://kdd2025.kdd.org/research-track-call-for-papers/
- CVPR : https://cvpr.thecvf.com/Conferences/2025/AuthorGuidelines

# AFFILIATIONS 
<p>The list of top 25 unversities, top 25 oragnizations, bottom 25 universities and bottom 25 organizations has been customized for every conference. For universities, the ranking reference is taken from https://csrankings.org/#/index?all&world . For organizations, LLMs have been used for ranking reference. Following is the merged list of each of the 4 affiliation categories, across all conferences and all years. </p>

## TOP 25 RANKED UNIVERSITIES
* Zhejiang University
* Peking University
* Shanghai Jiao Tong University
* The Chinese University of Hong Kong
* Nanyang Technological University
* Carnegie Mellon University
* Tsinghua University
* Stanford University
* National University of Singapore
* Shanghai Jiaotong University
* Nanjing University
* ETH Zurich
* Beihang University
* Massachusetts Institute of Technology
* Wuhan University
* Yonsei University
* The University of Hong Kong
* Harbin Institute of Technology
* City University of Hong Kong
* Georgia Institute of Technology
* University of Maryland, College Park
* Nankai University
* The Chinese University of Hong Kong, Shenzhen
* KAIST
* University of Michigan
* University of Science and Technology of China
* Fudan University
* Huazhong University of Science and Technology
* Xiamen University
* South China University of Technology
* Seoul National University
* Sun Yat-Sen University
* Institute of automation, Chinese academy of science, Chinese Academy of Sciences
* Xidian University
* Johns Hopkins University
* Shanghai AI Laboratory
* Massachusetts Institute of Technology(mit.edu)
* Stanford University(stanford.edu)
* Peking University(pku.edu.cn)
* Carnegie Mellon University(cmu.edu)
* Tsinghua University, Tsinghua University(tsinghua.edu.cn)
* New York University(nyu.edu)
* University of California, San Diego(ucsd.edu)
* Nanyang Technological University(ntu.edu.sg)
* Tsinghua University(tsinghua.edu.cn)
* University of California Berkeley(berkeley.edu)
* Princeton University(princeton.edu)
* University of Texas at Austin(utexas.edu)
* Georgia Institute of Technology(gatech.edu)
* Harvard University(harvard.edu)
* University of Cambridge(cam.ac.uk)
* Zhejiang University(zju.edu.cn)
* Nanjing University(nju.edu.cn)
* National University of Singapore(nus.edu.sg)
* Yale University(yale.edu)
* Korea Advanced Institute of Science & Technology(kaist.ac.kr)
* Northeastern University(northeastern.edu)
* Swiss Federal Institute of Technology(ethz.ch)
* Eberhard-Karls-Universität Tübingen(uni-tuebingen.de)
* Shanghai Jiaotong University(sjtu.edu.cn)
* Cornell University(cornell.edu)
* University of California,San Diego(ucsd.edu)
* University of California,Los Angeles(ucla.edu)
* University of Pennsylvania(upenn.edu)
* University of Southern California(usc.edu)
* University of California,Berkeley(berkeley.edu)
* University of Illinois at Urbana-Champaign
* University of Virginia
* Beijing University of Posts and Telecommunications
* Emory University
* The Hong Kong University of Science and Technology (Guangzhou
* University of Illinois Urbana-Champaign
* Hong Kong University of Science and Technology
* Renmin University of China
* KTH Royal Institute of Technology
* University of Science and Technology of China; State Key Laboratory of Cognitive Intelligence
* University of Electronic Science and Technology of China(uestc.edu.cn)
* Institute of Computing Technology, Chinese Academy of Sciences(ict.ac.cn)
* University of Oxford(ox.ac.uk)
* Seoul National University(snu.ac.kr)
* University of Maryland, College Park(umd.edu)
* Fudan University(fudan.edu.cn)
* Shanghai Jiao Tong University
* Tsinghua University
* University of Science and Technology of China
* Zhejiang University
* Massachusetts Institute of Technology
* University of Electronic Science and Technology of China
* Carnegie Mellon University
* State Key Laboratory for Novel Software Technology, Nanjing University, China
* College of Computer Science and Technology, Zhejiang University
* Harvard University
* National Key Laboratory for Novel Software Technology, Nanjing University, Nanjing 210023, China
* National University of Singapore
* Northeastern University
* Stanford University
* The Chinese University of Hong Kong
* Huazhong University of Science and Technology
* School of Computer Science and Engineering, Nanyang Technological University, Singapore
* State Key Laboratory of Networking and Switching Technology, Beijing University of Posts and Telecommunications
* Rochester Institute of Technology
* Department of Electronic Engineering, Tsinghua University
* Nanyang Technological University
* Peking University
* Politecnico di Milano
* School of Computer Science and Engineering, Sun Yat-sen University
* University of Oxford

## BOTTOM 25 RANKED UNIVERSITIES

* University of Science and Technology of China
* Huazhong University of Science and Technology
* Xiamen University
* South China University of Technology
* Seoul National University
* Institute of automation, Chinese academy of science, Chinese Academy of Sciences
* Xidian University
* Johns Hopkins University
* Shanghai AI Laboratory
* Tencent
* Institute of automation, Chinese academy of science(nlpr.ia.ac.cn)
* AI,Westlake University(westlake.edu.cn)
* Aarhus University(au.dk)
* Aarhus University(ece.au.dk)
* Aerospace Engineering & AI,Seoul National University(snu.ac.kr)
* Allen Institute for AI(allenai.org)
* Allen school of computer science and engineering,University of Washington(uw.edu)
* Analytics and Operations,National University of Singapore(nus.edu.sg)
* Applied AI Institute (A2I2),Deakin University(deakin.edu.au)
* Artificial Intelligence,Yonsei University(yonsei.ac.kr)
* Auburn University(auburn.edu)
* Australian Artificial Intelligence Institute,University of Technology Sydney(uts.edu.au)
* Bayerische Julius-Maximilians-Universität Würzburg(uni-wuerzburg.de)
* Beijing Institute of Mathematical Sciences and Applications(bimsa.cn)
* Beijing University of Posts and Communications(bupt.edu)
* Ben Gurion University of the Negev(bgu.ac.il)
* Berlin Institute for the Foundations of Learning and Data(tu-berlin.de)
* University of California, Los Angeles(cs.ucla.edu)
* University of Utah(cs.utah.edu)
* A*STAR(cfar.a-star.edu.sg)
* AGI Center, Ant Research Institute(antgroup.com)
* AI & Data Science, Monash University(monash.edu.au)
* AI Core,Zhongguancun Institute of Artificial Intelligence(zgci.ac.cn)
* AI Institute, Innopolis University(innopolis.university)
* AI4SCI,Centre for Artificial Intelligence and Robotics Hong Kong, Chinese Academy of Sciences(cair-cas.org.hk)
* AIRI(airi.edu)
* AMCS, GRASP,University of Pennsylvania(upenn.edu)
* American University
* Anhui Province Key Laboratory of Big Data Analysis and Application; State Key Laboratory of Cognitive Intelligence
* BOSS Zhipin
* Baylor University
* Beijing Technology and Business University
* Brandeis University
* C3.ai Digital Transformation Institute
* CAS Key Laboratory of GIPAS, University of Science and Technology of China
* CENTAI Institute
* CRIPAC, MAIS, Institute of Automation, Chinese Academy of Sciences
* Case Western Reserve University
* Center for Frontier AI Research, Agency for Science and Technology and Research (A*STAR)
* China Electric Power Research Institute
* China’s Aviation System Engineering Research Institute
* Clemson University
* University of British Columbia(cs.ubc.ca)
* University of Chicago(cs.uchicago.edu)
* Université Paris-Dauphine (Paris IX)(lamsade.dauphine.fr)
* AI Centre, Department of Computer Science,University College London, University of London(ucl.ac.uk)
* 1Advanced Research Lab, NavInfo Europe, The Netherlands
* 1Gaoling School of Artiﬁcial Intelligence, Renmin University of China, Beijing, China
* 2Beijing Key Laboratory of Big Data Management and Analysis Methods, Beijing, China
* 2Department of Mathematics and Computer Science, Eindhoven University of Technology, The Netherlands
* 360 DigiTech, Inc
* 3Huawei London Research Center, UK
* 3School of Computer Science, Beijing University of Posts and Telecommunications, China
* 4Guangxi Key Lab of Multi-Source Information Mining and Security, Guangxi Normal University, Guilin 541004, China
* AGH University
* AI Division, School of Engineering, Westlake University, Hangzhou
* AI Initiative, King Abdullah University of Science and Tech, Saudi Arabia+Jarvis Lab, Tencent, Shenzhen 518057, China
* AI Lab, CyberAgent, Japan
* AI Research and Innovation Laboratory, School of Engineering, Westlake University
* AI Research and Innovation Laboratory, Institute of AI Industry Research
* AI4Bharat
* AIRI

## TOP 25 RANKED ORGANIZATIONS

* OpenAI
* Google Research
* DeepMind
* Meta AI
* Facebook
* Microsoft Research
* Amazon AI
* IBM Research
* Snowflake
* Databricks
* Hugging Face
* NVIDIA Research
* Stanford University AI Lab
* MIT CSAIL
* CMU Machine Learning Department
* Berkeley AI Research (BAIR)
* Allen Institute for AI (AI2)
* Huawei Noah's Ark Lab
* Salesforce Research
* Adobe Research
* Tencent AI Lab
* ByteDance AI Lab
* Qualcomm AI Research
* Bytedance NLP Lab
* Apple Machine Learning Research
* Ant Financial / Alibaba DAMO Academy


## BOTTOM 25 RANKED ORGANIZATIONS

* Alibaba Group
* Huawei Technologies Ltd.
* Tencent AI Lab
* AI Institution,Vivo(vivo.com)
* 4Paradigm Inc.(4paradigm.com)
* AI Advanced Technology,SK hynix(sk.com)
* AI Core Research,Toyota Motor Europe(toyota-europe.com)
* AI Research,Salesforce(salesforce.com)
* AI,Reality Defender(realitydefender.com)
* AI/ML,GlaxoSmithKlein(gsk.ai)
* ASAPP(asapp.com)
* ASAPP Inc.(asapp.com)
* Alibaba Group US
* Amazon Search Science and AI
* Amazon Web Services
* Beijing Big Data Centre
* ByteDance
* Bytedance Research
* CITIC Securities
* Calculation Consulting
* Capinfo Company Limited
* Spotify(spotify.com)
* 2012 Labs,Huawei Technologies Ltd.(huawei.com)
* ADLR,NVIDIA(nvidia.com)
* AFSL,Samsung(samsung.com)
* AI Algorithm,Sengine(sengine.ai)
* AI Center,Samsung(samsung.com)
* AI Foundations,CapitalOne(capitalone.com)
* AI Frontier,Microsoft(microsoft.com)
* AI Institution,OPPO(oppo.com)
* AI LAB Bytedance(bytedance.com)
* AI Lab,ByteDance Inc.(bytedance.com)
* AI Lab,Kangma Biotech(healthcodon.com)
* AI Lab,NAVER(navercorp.com)
* 1Advanced Research Lab, NavInfo Europe, The Netherlands
* 360 DigiTech, Inc
* 3Huawei London Research Center, UK
* AIRS Company, Hyundai Motor Group
* AWS AI Labs + IBM Research AI
* Air Force Research Laboratory
* Algorithmics and Computational Complexity, Technische Universit ¨at Berlin
* Algorithms and Complexity Group, Technische Universit ¨at Wien, Vienna, Austria
* Alibaba Cloud Computing Ltd.
* Alibaba DAMO Academy
* Alibaba Group
* Alibaba US, DAMO Academy, Decision Intelligence Lab
* Alibaba group, China
* Amazon Science
* Amgen Research (Munich) GmbH, Munich, Germany
* Ant Group + Alibaba Inc
* Ant Group, Hangzhou, China + Toyota Technological Institute at Chicago, Chicago, IL, United States
* Apple
* Apple + Google Research
* Applied Research Center (ARC), Tencent PCG
* Autonomous Learning Group, Max Planck Institute for Intelligent Systems, Tübingen, Germany
* Beijing Academy of Artificial Intelligence
* Beijing Academy of Artificial Intelligence, Beijing, China
* Beijing Rongda Technology Co., Ltd., China
* Boehringer Ingelheim RCV GmbH & Co KG, Vienna, Austria
