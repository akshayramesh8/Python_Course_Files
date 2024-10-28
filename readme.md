_this summary doc is still in the works.. visit again soon :)_

- Overview
- The Questions
- Tools I Used
- Data Preparation and Cleanup
- The Analysis
- Results & Insights

Recommended README.md components:
![alt text](image-5.png)

# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?


View my notebook with detailed steps here:
[2_Skill_Demand.ipynb](3_Project\2_Skill_Demand.ipynb)

### Visualize Data

```python

fig, ax = plt.subplots(len(job_titles), 1)

sns.set_theme(style= 'ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    # df_plot.plot(kind='barh', x='job_skills', y='skill_percent', ax=ax[i], title = job_title)
    sns.barplot(data= df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue= 'skill_percent', palette= 'dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].legend().set_visible(False)
    ax[i].set_xlim(0,80)

    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{v:.0f}%', va= 'center')
    
    if i != len(job_titles) - 1:
        ax[i].set_xticks([])
        
fig.suptitle('Likelihood of Top Skills in Job Postings', fontsize= 15)
fig.tight_layout()
plt.show()

```

### Results

!['Visualization of Likelihood of Top Skills'](image-1.png)

### Insights

### 1. **Data Analyst**:
   - **SQL** is the most in-demand skill, with 51% of job postings requiring it. This emphasizes the critical role of SQL in data analysis for querying databases.
   - **Excel** is also highly sought after, appearing in 41% of postings, reflecting its widespread use for data manipulation and reporting.
   - **Tableau** and **Python** are moderately in demand, required in 28% and 27% of job postings, respectively. Tableau is popular for data visualization, while Python is favored for more advanced analytics and automation.
   - **SAS** is the least common skill among the top five, listed in 19% of job postings. It is typically used in statistical analysis and might be more niche depending on the industry.

### 2. **Data Engineer**:
   - **SQL** leads again with 68% of job postings, showing that SQL's role is even more critical for Data Engineers than for Data Analysts.
   - **Python** follows closely with 65%, which is vital for scripting and automating data pipelines.
   - **AWS** (Amazon Web Services) is required in 43% of postings, highlighting the need for cloud computing skills in data engineering.
   - **Azure** and **Spark** are tied, appearing in 32% of job postings. Azure signifies the demand for cloud services expertise, while Spark is essential for big data processing.

### 3. **Data Scientist**:
   - **Python** is the dominant skill for Data Scientists, required in 72% of job postings, underlining its importance for machine learning, statistical analysis, and general-purpose programming.
   - **SQL** is the second most required skill (51%), reinforcing its foundational role across data roles.
   - **R** comes in third at 44%, used for statistical analysis and data visualization.
   - **SAS** and **Tableau** are equally required (24%), indicating that while they are valuable, they are less critical compared to Python and SQL.

### **Overall Insights**:
- **SQL** and **Python** are universally important across all three roles, with SQL being a crucial skill across the board and Python particularly vital for Data Scientists and Engineers.
- **Cloud computing skills (AWS, Azure)** and **big data processing (Spark)** are essential for Data Engineers, reflecting the role's focus on building and maintaining data infrastructure.
- **Data visualization (Tableau, Excel)** remains a key skill for Data Analysts, while **statistical tools (R, SAS)** are more emphasized in Data Scientist roles.

These insights suggest that for anyone aspiring to enter or excel in these roles, a strong foundation in SQL and Python is essential, with additional specialized skills depending on the specific career path.


## 2. How are in-demand skills trending for Data Analysts?

### Visualize Data

``` python

df_plot = df_DA_US_percent.iloc[:, :5]
sns.lineplot(data= df_plot, dashes= False, legend= 'full', palette= 'tab10')
sns.set_theme(style='ticks')
sns.despine()

from matplotlib.ticker import PercentFormatter
ax= plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

for i in range(5):
    if i!=3:
        plt.text(11.85, df_plot.iloc[-1, i], df_plot.columns[i], ha='right', va='bottom')
    if i == 3:
        plt.text(11.55, df_plot.iloc[-1, 3], df_plot.columns[3], ha='center', va='top')
        
plt.show()

```

### Results

![alt text](image-3.png)
![Trending Top Skills for Data Analysts in the US](3_Project\images\3_Skills_Trend.png)

*Bar graph visualizing the trending top skills for data analysts in the US in 2023.*


![alt text](image-4.png)
### Insights







![alt text](image-2.png)

Testing to see source control change


