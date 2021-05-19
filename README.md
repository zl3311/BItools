# My learning progress of some Business Intelligence tools

## SQL

**SQL** is like a hard requirement for many DS jobs, so it would be useful to be familiar with it ASAP.

I started with watching some online tutorial videos (Yes, the one with [Mosh](https://youtu.be/7S_tz1z_5bA) :slightly_smiling_face:). The 3 hour video covers like 80% of the necessary materials, and I polished the remaining 20% by solving all leetcode database questions using MySQL.

![1](/SQL/leetcode-SQL.PNG)

Similar with the algorithm questions, easy and medium questions mostly test whether you know the concepts or not (the medium ones are indeed slightly more complex in logic). The hard questions are more challenging and (I believe) are close to real industry-level queries. 

My major takeaways throughout the process are:
* Relational database query languages (like MySQL) are not hard to pick up due to the rigid structure of tabular data, especially if you have background in numpy/pandas packages. In fact, some functions are highly similar, and you might find that the names of some operations are the same (like groupby, count, and all types of joins). Check [here](https://pandas.pydata.org/pandas-docs/stable/getting_started/comparison/comparison_with_sql.html) for more official comparisons from pandas documentations.
* Despite the similarity, there are some drawbacks (and it's not all SQL's fault :upside_down_face:). Because SQL is not designed to perform object-oriented programming (like Python), some data processing procedures are not so handy. Like, you can define a customized function in Python creating/tagging new features using existing ones then apply it along the correct axis. This procedure is only similarly available and convenient in SQL if the rule is consisted of `if-else` statements only, which is much less flexible than Python. Whenever I'm trying to do something this "fancy" in SQL, like `RECURSIVE CTE`, `FUNCTION`, `@`, I always doubt myself "do I have to do this in SQL?" :sweat_smile:. Anyway, SQL is capable of doing 95% of the common data manipulations using the `SELECT ... FROM ...` structure. For more in-depth feature engineering, I prefer doing it in Python.

Overall, the learning process was fun: slightly lost at the begining when I have no idea about the materials but much more comfortable after I knew it. After all the practices, I was able to pass the LinkedIn skill test on MySQL easily.

![2](/SQL/Capture.PNG)

---
## Tableau

I originally thought Tableau is some sort of statistical programming language, like R (I often see Stata with Tableau in job descriptions). Things turned out to be much easier when I put my hands on it :muscle:. 

**Tableau** is simply a data visualization tool **with minimum coding involved**. My understanding is that Tableau is designed for people with limited coding experience, and Salesforce (parent company of Tableau) indeed did a decent job achieving this goal. By clicking the mouse only, it is possible to build a pipeline that ingests data and creates visualizations upon it. I personally like two features about it:
* The visualization dashboard can be set as interactive. After checking the gallery from the Tableau website, I really enjoyed the interactive nature, because it gives users the freedom to explore the data patterns from their own perspectives. Although similar visualization applications have been developed (like Plotly), Tableau is still a popular choice based on my observation.
* The ingestion of data can be made online. This is practically useful when building real-time dashboards for decision makers to understand and react to the business directly.

To learn Tableau, I watched this [tutorial video](https://youtu.be/aHaOIvR00So) and enhanced the skill by accomplishing a project from Coursera. 

In the project:
* I collected the stock related data from Google Finance website using the `GOOGLEFINANCE` API inside Google Sheet (The eco-system of Google applications actually surprised me. I didn't know previously that I could do that in Google Apps). Data can be setup to update automatically.
* The Google Sheet can be connected to the ingestion port of Tableau, and the figures and dashboard can be further constructed upon that. For this project, I created a heatmap of the market share of some major Tech companies as size and their percent of change for the day as color. Also, I created a time series figure of these companies over the past month. Then, these plots are merged into a dashboard. Note that the file here is static, it can be made interactive and online using a paid service of Tableau. 

Check out here for my [code and certificate](/Tableau/).

---
## Facebook Prophet

The name of **Facebook Prophet** was pushed to me several times when I was browsing DS blogs on Medium.com. Out of curiosity, I dived deeper into it.

I do have some experience in time series analysis using different approaches, and I personally classify common methods into two categories:
* Statistics approaches. I put methods like ARIMA family and filter-based methods (Holt Winters, LOWESS, STL decomposition...) into this category. These methods are popular among the statistics and the econometric communities, where interpretability matters a lot more than model performance. It's true that there is nothing bad about interpretability. However, when model performance is a major drawback, interpretability might become relatively less important in these cases, which leads to the popularity of the next category.
* Deep learning approaches. DL-based sequential models, e.g., RNNs, LSTMs, and variations like with CNNs/encoders and decoders, suffer the same common drawback as almost all deep learning methods: **blackbox nature**, which means that it's really a mess to dive deep into the intermediate layers and understand what is actually happening. Despite the mess, DL models are generally better at representing highly nonlinear patterns, which means that these models would most likely outperform the above classic statistics approaches for cases with abundunt data and complex relationships. 

Essentially, Facebook Prophet is similar with the decomposition approaches, where the observed time series is assumed to be the addition of trend, periodic, customized events, and random noise components. [As branded by Facebook](https://facebook.github.io/prophet/), there are four major advantages of Prophet:
* Accurate and fast.
* Fully automatic.
* Tunable forecast.
* Available in R and Python.

Now, where does Facebook Prophet stand? After playing with the package in Python through a Coursera project (as [here](/Prophet/)), where I forecasted the time series of Avacado price, my feeling is mixed. What I like about Prophet is that it is scalable in optimization thus faster in implementation. Also, external information, like holidays, can be manually incorporated into the models, which adds flexibility to model. There are many blogs comparing classic time series models with it, and results are dataset-dependent. While I reserve my attitude about its capability, I really think that Facebook DS team should re-design the API of the package. For example, you have to priorly create the container of the null output dataframe explicitly and call the fitted model that creates the prediction. Seriously, Facebook? I have never seen any time series package with such user-unfriendly design! :-1:

Anyway, I tend to believe that the performances of these recent time series models (Prophet and also DeepAR from Amazon) are somewhere between the two extreme categories as I mentioned above. It's good to see that there are recent progresses from these big techs, but I look forward to seeing them create something more general and powerful in the future.

---

## A/B testing

I watched the [publicly available MOOC on A/B testing](https://www.udacity.com/course/ab-testing--ud257) by Google via Udacity. Since I'm not a subscriber of their nano-degree program, I do not have access to the final project as showcase. I did enjoy their videos though, and I'll talk about my thoughts here.

**A/B testing** is an application of statistical experiment design in the domain of user experience research. That is to say, the theory of hypothesis testing and statistical inference still holds here. 

Here are the procedures of designing an A/B testing experiment:
* construct comparable cohorts (unit of analysis, exposure/duration: relatively short term user patterns are similar, no long term effect)
* setup the hypothesis of variant metric
* sanity check on invariant variables 
* choosing variant metrics
* determining sample size given hypothesis
* sanity check on invariant hypothesis and accept/reject hypothesis

A/B testing is suitable when the analyzed data has fewer columns than rows, and by saying **fewer**, I mean several magnitudes smaller. The reason for such enormous volume of data is that A/B testing (or hypothesis testing in general) is essentially testing the statistical significance of the difference in the parameters of fitted parametric distributions from the control group versus the treatment group. Obviously, the volume of data required (a.k.a., sample size in hypothesis testing) to make a statement in the fashion of A/B testing is related to the level of desired statistical power, variation of the data itself, and the data proximity of the treatment group and the control group.

What I like about A/B testing is its structure. The theory is indeed profound, formally addressing various concerns considering the joint effects of parameter gap, standard deviation, and level of belief. What I don't like about A/B testing is the inefficiency when making inference. The fact that required sample size scales faster than the statistical power does not make sense ([test here via an online calculator](https://www.evanmiller.org/ab-testing/sample-size.html)). In real life, the accessibility of data comes with a cost. If the cost of achieving each 1% increase in statistical power grows even faster than the benefit (statistical power) itself, the diminishing marginal benefit effect will eventually become a major issue capping the power of A/B testing in real life, where the resources of conducting an A/B testing (time, traffic flow) are typically limited.

In short, A/B testing is useful for drawing qualitative statement addressing risk level (like online testing), and other variations of the naive A/B testing like non-parameteric distribution and Bayesian approaches do exist. For the specific evaluation purpose, A/B testing is a good enough tool and worth learning.

---
## Causal inference

The field of **casual inference** is not new, but I came across the name quite recently. It was confusing for me at the beginning by looking at the name. With some knowledge of regression analysis, I have been told that the interpretation of linear regression should only imply correlation but never causality. In other words, using the terminology of graph theory, the relationship between two variables/nodes is undirected rather than singly directed. The question then becomes how to determine the direction of the edge from one side to the other side rather the other way round.

To start with an easier setup, if one variable is observed during the prerequisite procedure of the other variable (like an upstream-downstream setup), it is safe to say that one caused the other. For more general cases, when lacking of context about how data is produced, it is not that easy to assert the causal effect using data only. Beared with such concerns in mind, I explored some common ways of making causal inference by completing a Coursera project (as [here](/Causal%20Inference/)).

The project covered the following methods:
* Fixed-effect regression
* Discontinued regression
* Difference in difference
* Instrumental variable
* Double selection
* Causal forest

My takeaways from the project are:
* **Fixed-effect regression** and **discontinued regression** mostly deal with the more ideal situations, where the treatment variable is assumed to be independent from other explanatory variables and the effects of the treatment variable can be expressed using constant or piece-wise linear addition, which is good enough to represent simple scenarios.
* Similarly, **difference in difference** compares the treatment group with the control group by measuring the linear difference between the actual treatment outcome and the virtual treatment group corrected by the pattern observed for the control group. Again, it relies on the assumption that the effect of the treatment variable is linearly additive to the predicted variable.
* **Instrumental variable** and **double selection** come into the analysis when the explanatory variables are in fact correlated with each other and we are trying to alleviate covariation. What instrumental variable does is reasoning using the concept of conditional independence, and it relies on the selection of covariates as instrumental variable. Double selection addresses the similar problem using an alternative heuristic. It exploits the fact the L1 regularization in LASSO performs feature selection, which prevents the overfitting caused by covariates. By including all non-zero-coefficient predictors in both the LASSO regression models of `response ~ predictor` and `treatment ~ predictor`, double selection aims to avoid the corruption of covariates by simply not including them in final model and leaving the treatment variable as the only controlling factor.
* **Causal forest** is basically an extension of the classic random forest, where the objective is to maximize the difference in outcome given treatment and control variables instead of minimizing prediction error in a typical supervised learning setup. The gist is that it utilizes the fact that bagging algorithms creates a stronger learner in representing nonlinear patterns than generalized linear model and the contribution of treatment variables on differentiating outcomes can be better acknowledged with the strong learner. Happy to see machine learning is making traditional fields better! :wink:

Although I tried out some new methods that I have not been touched before, there is still a long way becoming an expert in the field. I'm currently reading the [probabilistic graphic model](https://mitpress.mit.edu/books/probabilistic-graphical-models) book by Daphne Koller and Nir Friedman, and I find it really interesting. Even though Judia Pearl has already won the 2011 Turing Award for his contribution in the theories of probabilistic causal inference, I believe this field will definitely draw even more attentions in the future.

I'll update this section after I finish reading the book. Stay tuned!
