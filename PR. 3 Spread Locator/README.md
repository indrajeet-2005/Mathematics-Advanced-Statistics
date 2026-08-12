# 📊 Spread Locator --- Statistical Distribution Analysis

> **Advanced Data Analytics & Probability Distribution Project**\
> A statistical analysis of transaction behavior using **Bernoulli,
> Binomial, Poisson, Log-Normal, Pareto/Power-Law, Q-Q analysis, Box-Cox
> transformation, Z-scores, PDF and CDF**.

------------------------------------------------------------------------

## 🚀 Project Overview

**Spread Locator** is a statistical data-analysis project focused on
understanding transaction behavior through probability distributions and
statistical transformations.

The project analyzes a supplied transaction dataset and demonstrates how
different statistical models can be selected according to the nature of
a variable:

-   **Bernoulli Distribution** → transaction success/failure
-   **Binomial Distribution** → weekly transaction-count approximation
-   **Poisson Distribution** → transactions recorded per day
-   **Log-Normal Distribution** → transaction amount modeling
-   **Pareto / Power-Law Distribution** → alternative transaction-amount
    model
-   **Q-Q Plot + Shapiro-Wilk Test** → normality assessment
-   **Box-Cox Transformation** → reduction of positive skew
-   **Z-score Analysis** → threshold analysis for ₹5,000
-   **PDF & CDF** → probability-density and cumulative-probability
    analysis

The final analysis concludes that the **Log-Normal distribution is the
strongest candidate among the tested models for transaction amounts**.

------------------------------------------------------------------------

## 🎯 Project Objectives

The major objectives of this project are to:

1.  Inspect and understand the transaction dataset.
2.  Identify the appropriate probability distribution for different
    transaction variables.
3.  Estimate the probability of transaction success.
4.  Model weekly transaction counts using a Binomial approximation.
5.  Model daily transaction-record counts using a Poisson distribution.
6.  Compare Log-Normal and Pareto models for transaction amounts.
7.  Test whether raw transaction amounts follow a normal distribution.
8.  Apply a Box-Cox transformation to reduce skewness.
9.  Calculate the probability of a transaction exceeding **₹5,000**.
10. Visualize transaction behavior using statistical plots.
11. Translate statistical results into practical business insights.

------------------------------------------------------------------------

## 🧠 Statistical Concepts Covered

  Concept                   Application
  ------------------------- -----------------------------------------
  Bernoulli Distribution    Success vs. Fail transaction outcome
  Binomial Distribution     Weekly transaction-count approximation
  Poisson Distribution      Daily transaction-record count
  Log-Normal Distribution   Transaction amount modeling
  Pareto Distribution       Alternative heavy-tail model
  K-S Test                  Distribution-fit comparison
  AIC                       Model comparison
  Q-Q Plot                  Visual normality assessment
  Shapiro-Wilk Test         Statistical normality test
  Box-Cox Transformation    Skewness reduction
  Z-score                   Distance of ₹5,000 from the sample mean
  PDF                       Transaction amount density
  CDF                       Cumulative probability

------------------------------------------------------------------------

## 📁 Project Structure

``` text
Spread-Locator/
│
├── 📓 PR3_Spread_Locator_Solution.ipynb
├── 📄 PR. 3 Spread Locator.pdf
├── 📊 spread_locator_dataset.xlsx
└── 📘 README.md
```

> The notebook expects the dataset file `spread_locator_dataset.xlsx` to
> be available in the working directory.

------------------------------------------------------------------------

## 🛠️ Tech Stack

### Programming Language

-   🐍 Python

### Libraries

-   **NumPy** --- numerical computation
-   **Pandas** --- data loading, cleaning and analysis
-   **Matplotlib** --- statistical visualization
-   **Seaborn** --- visualization support
-   **SciPy** --- probability distributions, statistical tests and
    fitting
-   **OpenPyXL / Excel engine** --- Excel dataset ingestion through
    Pandas

------------------------------------------------------------------------

## ⚙️ Installation & Setup

### 1. Clone or download the project

``` bash
git clone <your-repository-url>
cd Spread-Locator
```

### 2. Create a virtual environment

``` bash
python -m venv venv
```

### 3. Activate the environment

#### Windows

``` bash
venv\Scripts\activate
```

#### macOS / Linux

``` bash
source venv/bin/activate
```

### 4. Install dependencies

``` bash
pip install numpy pandas matplotlib seaborn scipy openpyxl jupyter
```

### 5. Launch Jupyter Notebook

``` bash
jupyter notebook
```

Open:

``` text
PR3_Spread_Locator_Solution.ipynb
```

------------------------------------------------------------------------

# 📥 Dataset

The analysis uses an Excel dataset named:

``` text
spread_locator_dataset.xlsx
```

The notebook loads it using:

``` python
df = pd.read_excel(DATA_FILE)
```

Important fields used by the analysis include:

-   `transaction_status`
-   `transaction_count`
-   `transaction_date`
-   `transaction_amount`

------------------------------------------------------------------------

# 🔍 Data Inspection

The first stage performs basic dataset inspection:

-   Dataset shape
-   Column names
-   Missing-value counts
-   Data types
-   Transaction-status distribution
-   Transaction-amount descriptive statistics

This establishes the structure and quality of the data before
statistical modeling.

------------------------------------------------------------------------

# 1️⃣ Bernoulli Distribution --- Transaction Success

## Concept

A Bernoulli distribution models a binary outcome with two possible
states:

-   `Success = 1`
-   `Fail = 0`

The project converts the transaction status into a binary variable:

``` python
df["success"] = (df["transaction_status"] == "Success").astype(int)
```

The observed success probability is estimated as:

``` python
p_success = df["success"].mean()
```

### Result

The notebook reports an estimated success probability of approximately:

**44.55%**

Therefore, in this sample, a randomly selected transaction record has
approximately a **44.55% observed probability of being successful**.

------------------------------------------------------------------------

# 2️⃣ Binomial Distribution --- Weekly Transaction Count

The dataset contains a `transaction_count` field representing the number
of transactions made by a customer in a given week.

Because a Binomial distribution requires a fixed number of trials, the
notebook uses the observed maximum transaction count as:

``` text
n = 9
```

The probability parameter is estimated from:

``` text
p = mean(transaction_count) / n
```

The observed transaction-count probabilities are then compared with the
fitted Binomial PMF.

### Visualization

The notebook generates an:

**Observed vs Binomial Distribution**

bar chart.

### Important Assumption

This is explicitly an **analytical approximation**, because the
assignment does not provide a separate fixed number of weekly trials.

------------------------------------------------------------------------

# 3️⃣ Poisson Distribution --- Daily Transactions

The project groups transaction records by `transaction_date`:

``` python
daily_transactions = df.groupby("transaction_date").size()
```

The average number of transaction records per day is used as the Poisson
rate:

``` text
λ = mean daily transaction count
```

### Result

The notebook reports:

**λ ≈ 7.10 transactions per day**

The fitted Poisson PMF is compared with daily transaction behavior.

### Business Interpretation

The Poisson model provides a simple way to describe how many transaction
records are observed on a typical day.

------------------------------------------------------------------------

# 4️⃣ Transaction Amount Modeling

Transaction amounts are positive and strongly right-skewed.

Because of this, the project evaluates two positive-skewed candidate
distributions:

### Model A --- Log-Normal

``` text
Log-Normal Distribution
```

### Model B --- Pareto / Power Law

``` text
Pareto Distribution
```

The models are compared using:

-   **Kolmogorov-Smirnov statistic**
-   **K-S p-value**
-   **AIC**

### Model-selection principle

Generally:

-   Lower K-S statistic → closer distributional fit
-   Higher K-S p-value → less evidence against the fitted distribution
-   Lower AIC → preferred model among comparable candidates

------------------------------------------------------------------------

# 🏆 5️⃣ Final Model --- Log-Normal

The notebook concludes that the:

## **Log-Normal Distribution**

is the strongest candidate among the tested models for transaction
amounts.

The conclusion is supported by:

1.  Transaction amounts are strictly positive.
2.  The raw transaction amounts are strongly right-skewed.
3.  The Log-Normal model produces a much smaller K-S statistic than the
    fitted Pareto model.
4.  The Log-Normal K-S p-value is high in the supplied sample.
5.  The Pareto model performs substantially worse under the same
    comparison.
6.  The Box-Cox transformation also confirms substantial skew in the
    original amounts.

------------------------------------------------------------------------

# 6️⃣ Q-Q Plot & Normality Testing

The project uses a Q-Q plot to visually compare raw transaction amounts
against a theoretical normal distribution.

A strong systematic deviation from the reference line indicates that the
raw values are not normally distributed.

The notebook also applies the:

## Shapiro-Wilk Test

The analysis reports statistical evidence against normality for the raw
transaction amounts.

### Key Insight

The transaction amounts should **not automatically be treated as
normally distributed**.

This is important because many statistical calculations become
misleading when a highly skewed variable is forced into a normal model.

------------------------------------------------------------------------

# 7️⃣ Box-Cox Transformation

The project applies a Box-Cox transformation because transaction amounts
are positive and strongly skewed.

The notebook estimates:

``` text
Box-Cox λ ≈ -0.181
```

The transformation substantially reduces the positive skewness and
produces a more symmetric distribution.

### Visualization

Two histograms are compared:

-   Original transaction amounts
-   Transaction amounts after Box-Cox transformation

------------------------------------------------------------------------

# 8️⃣ ₹5,000 Threshold Analysis

The project investigates:

> **What is the probability that a transaction exceeds ₹5,000?**

Three approaches are compared.

### A. Normal Approximation

The z-score is calculated as:

``` text
z = (x - mean) / sample standard deviation
```

For:

``` text
x = ₹5,000
```

the notebook reports:

``` text
Z-score ≈ 0.823
```

The corresponding normal-based probability is approximately:

**20.52%**

------------------------------------------------------------------------

### B. Empirical Probability

The actual observed sample proportion above ₹5,000 is:

**11.36%**

or:

**25 out of 220 records**

------------------------------------------------------------------------

### C. Fitted Log-Normal Probability

The fitted Log-Normal model estimates:

**P(X \> ₹5,000) ≈ 13.84%**

------------------------------------------------------------------------

## 📌 Why the Three Results Differ

  Method                   Approximate Probability
  ---------------------- -------------------------
  Normal approximation                  **20.52%**
  Empirical sample                      **11.36%**
  Fitted Log-Normal                     **13.84%**

The difference demonstrates an important statistical principle:

> **The choice of probability model matters.**

Because transaction amounts are strongly right-skewed, the normal
approximation should be treated as a rough approximation rather than the
preferred model.

------------------------------------------------------------------------

# 9️⃣ PDF & CDF Analysis

The fitted Log-Normal distribution is used to calculate and visualize:

## PDF --- Probability Density Function

The PDF shows where transaction amounts are more concentrated under the
fitted model.

## CDF --- Cumulative Distribution Function

The CDF represents:

``` text
P(X ≤ x)
```

It can be used to estimate the probability that a transaction amount is
below a selected threshold.

Together, PDF and CDF provide a useful view of the distribution's shape
and cumulative behavior.

------------------------------------------------------------------------

# 📊 Key Results

  Metric                          Result
  ------------------------------- ----------------
  Records analyzed                **220**
  Bernoulli success probability   **≈ 44.55%**
  Poisson daily λ                 **≈ 7.10**
  Box-Cox λ                       **≈ -0.181**
  ₹5,000 z-score                  **≈ 0.823**
  Normal P(X \> ₹5,000)           **≈ 20.52%**
  Empirical P(X \> ₹5,000)        **≈ 11.36%**
  Observed amount \> ₹5,000       **25 / 220**
  Log-Normal P(X \> ₹5,000)       **≈ 13.84%**
  Best tested amount model        **Log-Normal**

------------------------------------------------------------------------

# 💡 Business Insights

Although this is primarily a statistical project, the results can
support practical decision-making.

### 1. Transaction success monitoring

The observed success rate of approximately **44.55%** can be used as a
baseline for monitoring transaction performance.

### 2. Daily operational planning

A Poisson rate of approximately **7.10 transaction records per day**
provides a simple baseline for understanding daily transaction volume.

### 3. Spending behavior

Transaction amounts are strongly right-skewed, meaning a small number of
larger transactions can extend the upper tail.

### 4. Better probability modeling

The Log-Normal model is more suitable than a normal model for the
transaction amounts tested here.

### 5. Threshold-based analysis

The ₹5,000 analysis demonstrates why businesses should compare empirical
probabilities with fitted statistical models instead of relying on a
normal approximation alone.

------------------------------------------------------------------------

# ⚠️ Statistical Assumptions & Limitations

This project is an analytical/statistical exercise, so the following
limitations are important.

### Binomial assumption

The Binomial model uses:

``` text
n = observed maximum transaction_count = 9
```

This is an approximation because the dataset does not specify an
independent fixed number of weekly trials.

### Normal probability assumption

The normal-based probability for ₹5,000 is only an approximation because
the raw transaction amounts are not normally distributed.

### Distribution comparison

The Log-Normal model is preferred **among the tested candidates**. This
does not prove that it is the universally correct real-world
distribution.

### Poisson interpretation

The Poisson model describes transaction-record counts aggregated by
date. It should not automatically be interpreted as a complete model of
all real-world customer transaction behavior.

### Dataset scope

All conclusions are based on the supplied sample and may not generalize
to a larger or different population.

------------------------------------------------------------------------

# 📈 Visualizations Included

The notebook includes statistical visualizations such as:

-   📊 Observed vs Binomial PMF
-   📊 Poisson distribution fit
-   📉 Transaction amount Q-Q plot
-   📊 Original transaction amount histogram
-   📊 Box-Cox transformed histogram
-   📈 Log-Normal PDF
-   📈 Log-Normal CDF

------------------------------------------------------------------------

# 🧪 Reproducibility

To reproduce the analysis:

1.  Install Python and the required libraries.
2.  Place `spread_locator_dataset.xlsx` in the notebook's working
    directory.
3.  Open `PR3_Spread_Locator_Solution.ipynb`.
4.  Run the notebook from top to bottom.
5.  Review the generated tables, statistical tests and visualizations.

------------------------------------------------------------------------

# 📚 Learning Outcomes

After completing this project, you can demonstrate practical
understanding of:

-   Probability distributions
-   Exploratory data analysis
-   Statistical parameter estimation
-   Distribution fitting
-   K-S testing
-   AIC-based model comparison
-   Normality testing
-   Q-Q plots
-   Data transformation
-   Z-score calculations
-   Probability estimation
-   PDF/CDF interpretation
-   Statistical reasoning for business data

------------------------------------------------------------------------

# 🏗️ Possible Future Improvements

The project can be extended with:

-   [ ] Interactive dashboard using **Power BI**
-   [ ] Interactive visualizations using **Plotly**
-   [ ] Automated statistical model selection
-   [ ] Confidence intervals for estimated parameters
-   [ ] Bootstrap-based probability estimates
-   [ ] Additional distributions such as Gamma, Weibull and Exponential
-   [ ] Formal goodness-of-fit comparison across more candidate models
-   [ ] Time-series analysis of transaction volume
-   [ ] Customer-level behavioral segmentation
-   [ ] Anomaly/outlier detection
-   [ ] Predictive modeling for transaction success
-   [ ] Streamlit deployment
-   [ ] Production-ready data pipeline

------------------------------------------------------------------------

# 👨‍💻 Project Files

  -------------------------------------------------------------------------
  File                                  Description
  ------------------------------------- -----------------------------------
  `PR3_Spread_Locator_Solution.ipynb`   Complete Python statistical
                                        analysis

  `PR. 3 Spread Locator.pdf`            Project/report document

  `spread_locator_dataset.xlsx`         Input transaction dataset

  `README.md`                           Project documentation
  -------------------------------------------------------------------------

------------------------------------------------------------------------

# 🌟 Final Conclusion

The Spread Locator project demonstrates how probability distributions
can be applied to real transaction data to extract meaningful
statistical insights.

The analysis shows that different variables require different
statistical approaches:

-   **Bernoulli** for binary transaction outcomes
-   **Binomial** for an approximate fixed-trial transaction-count model
-   **Poisson** for daily transaction-record counts
-   **Log-Normal** for positively skewed transaction amounts
-   **Box-Cox** for reducing skewness
-   **Z-scores** for threshold analysis
-   **PDF/CDF** for understanding distribution behavior

The most important modeling conclusion is that the **Log-Normal
distribution provides the strongest fit among the tested
transaction-amount models**, while the raw transaction amounts do not
follow a normal distribution well.

This project therefore demonstrates not only how to calculate
statistical measures, but also how to **select, evaluate and interpret
statistical models based on the actual shape and behavior of data**.

------------------------------------------------------------------------

## ⭐ If you found this project useful

If you are using this project for learning, portfolio development, or
data-analysis practice, consider:

-   ⭐ Starring the repository
-   🍴 Forking the project
-   📝 Sharing your improvements
-   💼 Adding the project to your Data Analyst portfolio

------------------------------------------------------------------------

### 📌 Project Type

**Statistical Data Analysis \| Probability Distributions \| Python \|
EDA \| Business Analytics**

### 🔖 Keywords

`Python` `Pandas` `NumPy` `SciPy` `Matplotlib` `Seaborn` `Statistics`
`Probability` `Data Analysis` `EDA` `Bernoulli` `Binomial` `Poisson`
`Log-Normal` `Pareto` `Box-Cox` `Q-Q Plot` `Z-Score` `PDF` `CDF`
`Business Analytics`
