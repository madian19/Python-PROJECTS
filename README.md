# Python-PROJECTS
Python projects for data analysis and visualization — practical, hands-on, and insight-driven.
# The Analysis 😏

## 1. What are the demanded skills for the top 3 popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here: [PROJECT1.ipynb](PROJECT1.ipynb)

### Visualize Data

```python
fig, ax = plt.subplots(len(job_titles), 1)
for i, job_title in enumerate(job_titles):
    df_plot = df_US_skills_perc[df_US_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x='%skill', y='job_skills', hue='skill_count', palette='dark:b_r', legend=False, ax=ax[i])
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].legend().set_visible(False)
    ax[i].set_xlim(0, 80)
    ax[i].set_xticks([])
    
    for n, v in enumerate(df_plot['%skill']):
        ax[i].text(v + 1, n, f"{v:.1f}%", color='black', va='center')
    fig.suptitle('Likelihood of Skills Requested in US Job Postings', fontsize=16)
    fig.tight_layout()
plt.show()
```
### Results

![Visualization of Top Skills for Data Nerds](images\Skill_demand_TOP3_data_rules.png)

### Insights

- SQL is the most requested skill for Data Analysts and Data Engineers, with it in over half the job postings for both roles. For Data scientists, Python is the most sought-after skill, appearing in 72% of job postings.
- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).
- Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (72%) and Data Engineers (65%).
