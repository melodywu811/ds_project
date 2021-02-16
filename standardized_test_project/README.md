# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Test Analysis

**Submitted by: Melody Wu**  
**Submitted on: Feb 5, 2021**

### Content  

This executive summary is organized as below:

1. Problem Statement
2. Datasets
3. Deliverables
4. Key Fidings
5. Conclusions and Recommendations

### 1. Problem Statement

In order to increase the number of student applying to 4-year colleges, and ultimately to increase college attendance and attainment in California, the Department of Education is proposing a "Test for Success CA" Program to the State of California, which aims to provide extra funding for school districts. With this funding, the school districts can implement relevant interventions, such as free test prep workshops and fee waivers.

The goal of this program increase ACT/SAT participation rate to further increase the number of students applying to four-year colleges. By analyzing the ACT/SAT data and identifying the school districts that have lower ACT/SAT test participation rates, the State of California can allocate resources to school districts in need more efficiently and equitably.

### 2. Datasets

This project analyzes the below datasets:
* [`act_2019.csv`](./data/act_2019.csv): 2019 ACT Scores by State
* [`sat_2019.csv`](./data/sat_2019.csv): 2019 SAT Scores by State
* [`act_2019_ca.csv`](./data/act_2019_ca.csv): 2019 ACT Scores in California by School
* [`sat_2019_ca.csv`](./data/sat_2019_ca.csv): 2019 SAT Scores in California by School

#### Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---|
|**state**|*string*|2019 ACT/SAT Scores by State|The name of the State|
|**act_participation**|*float*|2019 ACT/SAT Scores by State|The percentage of the ACT participants of a given State|
|**act_composite**|*float*|2019 ACT/SAT Scores by State|The averaged ACT scores of a given State|
|**sat_participation**|*float*|2019 ACT/SAT Scores by State|The percentage of the SAT participants of a given State|
|**sat_total**|*integer*|2019 ACT/SAT Scores by State|The averaged SAT Total scores of a given State|
|**ccode**|*float*|2019 SAT Scores of California, 2019 ACT Scores of California|The identifier of a county|
|**cdcode**|*float*|2019 SAT Scores of California, 2019 ACT Scores of California|The identifier of a school district|
|**scode**|*float*|2019 SAT Scores of California, 2019 ACT Scores of California|The identifier of a school|
|**cname**|*string*|2019 SAT Scores of California, 2019 ACT Scores of California|The name of a county|
|**dname**|*string*|2019 SAT Scores of California, 2019 ACT Scores of California|The name of a school district. N/A = County Level Record|
|**enroll12**|*float*|2019 SAT Scores of California, 2019 ACT Scores of California|The number of Grade 12 students enrolled in a given school|
|**numtsttakr12**|*float*|2019 SAT Scores of California, 2019 ACT Scores of California|The number of Grade 12 students taken the ACT|
|**enroll11**|*float*|2019 SAT Scores of California, 2019 ACT Scores of California|The number of Grade 11 students enrolled in a given school|
|**numtsttakr11**|*float*|2019 SAT Scores of California, 2019 ACT Scores of California|The number of Grade 12 students taken the ACT|
|**participation_1112**|*float*|2019 SAT Scores of California|The SAT participation rate of Grade 12 and Grade 11 in a given school|

### 3. Deliverables

In the repository that submitted on Google Classroom, the below materials serve as the submission packet to this project.

- A README.md (this current executive summary)
- Technical notebook (Jupyter Notebook)
- Presentation slides in PDF [(link to the presentation is also provided here)](https://docs.google.com/presentation/d/16fgoxlUA8fu-BdrPnkwIoKCnyifdbWX0P35iMMlgXWE/edit?usp=sharing)
- csv files with project recommendations lists
 - List of school district with schools having 0% SAT participation rates
 - List of school district with schools having below state average SAT participation rate  

**Delivered datasets**
 * [`zero_districts.csv`](./data/zero_districts.csv): School Districts with Schools Having 0% SAT participation rates
 * [`below_mean_districts.csv`](./data/below_mean_districts.csv): School Districts with Schools Having Below Average SAT participation rates
 * [`act_sat_2019.csv`](./data/act_sat_2019.csv): 2019 ACT and SAT Scores by State after data cleaning
 * [`sat_2019_ca_clean.csv`](./data/sat_2019_ca_clean.csv): 2019 SAT Scores in California by School after data cleaning


### 4. Key Findings  

**Benchmarking with other States**
- California has a lower ACT participation rate (23%) when benchmarking with the averaged state participation rate (58.7%).  
- California has a higher SAT participation rate (62%) when benchmarking with the averaged state participation rate (58.6%).
- Amongst the 12 states in the last quartile (25% quartile) of ACT participation rates, California has the lowest SAT participation rate.

**In California, some school districts have extremely low test participation rates:**
- There are 105 school districts have schools with 0% SAT participation rate
- There are 469 school districts have schools with SAT participation rates below state average (25%)

### 5. Conclusions and Recommendations
Based on our analysis of the 2019 State SAT/ACT Data and the 2019 California SAT Data, we see an urgent need of a program, such as the "Test for Success CA" that we are proposing here, to provide funding for school districts to improve their students' ACT/SAT participation rates, to further improve the college application rates, and ultimately to improve college attendance and attainment.

**Recommendations for rolling out the "Test for Success Program:**
- Stage 1: school districts with ZERO participation rate schools
- Stage 2: school districts have school participation rates below state average
- Stage 3: all school districts in California

**Next Step:**
- Approve and implement the "Test for Success CA" Project
- School districts in stage 1 to do a in-house check and proposal school-level programs/interventions to use the budget
- The Department of Education to set up working committee to oversea "Test for Success CA"
- The working committee to discuss plans for Stage 2 implementation

---
