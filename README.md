# My learning progress of some Business Intelligence tools

## SQL
**SQL** is like a hard requirement for many DS jobs, so it would be useful to be familiar with it ASAP.

I started with watching some online tutorial videos (Yes, the one with [Mosh](https://youtu.be/7S_tz1z_5bA) :slightly_smiling_face:). The 3 hour video covers like 80% of the necessary materials, and I polished the remaining 20% by solving all leetcode database questions using MySQL.

![1](/SQL/leetcode-SQL.PNG)

Similar with the algorithm questions, easy and medium questions mostly test whether you know the concepts or not (the medium ones are indeed slightly more complex in logic). The hard questions are more challenging and (I believe) are close to real industry-level queries. 

My major takeaways throughout the process are:
* Relational database query languages (like MySQL) are not hard to pick up due to the rigid structure of tabular data, especially if you have background in numpy/pandas packages. In fact, some functions are highly similar, and you might find that the names of some operations are the same (like groupby, count, and all types of joins). Check [here](https://pandas.pydata.org/pandas-docs/stable/getting_started/comparison/comparison_with_sql.html) for more official comparisons from pandas documentations.
* Despite the similarity, there are some drawbacks (and it's not all SQL's fault :upside_down_face:). Because SQL is not designed to perform object-oriented programming (like Python), some data processing procedures are not so handy. Like, you can define a customized function in Python creating/tagging new features using existing ones then apply it along the correct axis. This procedure is only similarly available and convenient in SQL if the rule is consisted of '<if-else>' statements only, which is much less flexible than Python. Whenever I'm trying to do something "fancy" in SQL, like `RECURSIVE CTE`, `FUNCTION`, `@`, I always doubt myself "do I have to do this in SQL?" :sweat_smile:. Anyway, SQL is capable of doing 95% of the common data manipulations. For more in-depth feature engineering, I prefer doing it in Python.

Overall, the learning process was fun: slightly lost at the begining when I have no idea about the materials but so much comfortable when I know it. After all the practices, I passed the LinkedIn skill test on MySQL easily.

![2](/SQL/Capture.PNG)

---
## Tableau

I originally thought Tableau is some sort of statistical programming language, like R (I often see Stata with Tableau in job descriptions). Things turned out to be much easier when I put my hands on it :muscle:. 

**Tableau** is simply a data visualization tool **with minimum coding involved**. My understanding is that Tableau is designed for people with limited coding experience, and Salesforce (parent company of Tableau) indeed did a decent job achieving this goal. By clicking the mouse only, it is possible to build a pipeline that ingests data and creates visualizations upon it. I personally like two features about it:
* The visualization dashboard can be set as interactive. After checking the gallery from the Tableau website, I really enjoyed the interactive nature, because it gives users the freedom to explore the data patterns from their own perspectives. Although similar visualization applications have been developed (like Plotly), Tableau is still a popular choice based on my observation.
* The ingestion of data can be made online. This is practically useful when building real-time dashboards for decision makers to understand and react to the business directly.

To learn Tableau, I watched the [tutorial video](https://youtu.be/aHaOIvR00So) and enhanced the skill by accomplishing a project from Coursera. In the Coursera project:
* I collected the stock related data from Google Finance website using the `GOOGLEFINANCE` API inside Google Sheet (The eco-system of Google applications actually surprised me. I didn't know previously that I could do that in Google Apps). Data can be setup to update automatically.
* The Google Sheet can be connected to the ingestion port of Tableau, and the figures and dashboard can be further constructed upon that. For this project, I created a heatmap of the market share of some major Tech companies as size and their percent of change for the day as color. Also, I created a time series figure of these companies over the past month. These plots are merged into a dashboard as shown [here](BItools/Tableau/Dashboard 1.pdf). Note that this static file can be made interactive and online using a paid service of Tableau. 

Checkout here for my [certificate](BItools/Tableau/Coursera QMR8WGH7GL8J.pdf).

---

## A/B testing
screenshot

## Facebook Prophet
certificate and sample code
difference with X11 and decomposition-based approaches

## Naive causal inference
certificate and sample code
mention probalistics graphic models
