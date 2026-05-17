# k-means

In This project we are going to use K-Means clustering. This will help us segment credit card customers based on how they use their cards. We do not have a target label for customer groups in our dataset. That is why this is a learning problem.

We will be working with the CC_GENERAL.csv dataset.

About the Dataset

The CC_GENERAL.csv dataset has information about how credit card customers behave. Each row in the dataset is one credit card holder. The columns have variables. These variables tell us about balance, purchases, cash advance, payments and tenure. We want to group customers who're similar together. This will help the company understand the kinds of customers they have. Then they can make marketing strategies for each kind of customer.

The company can use K-Means clustering to find out more, about their customers.

They will use customer-level credit card usage behavior data.

This data will help them design marketing strategies.
The goal is to group customers together.

 1. Why is this an unsupervised learning problem?

Because we don’t have labeled outputs (no target column). The goal is to discover hidden patterns or groups in the data using clustering (K-Means), not to predict a known label.

2. Why did we remove the CUST_ID column?

Because CUST_ID is just an identifier. It does not contain behavioral information about customers, so it would not help clustering and could distort the distance calculations.

3. Which columns had missing values?

Typically in this dataset, missing values appear in features like:

MINIMUM_PAYMENTS
CREDIT_LIMIT

(You can confirm this using df.isnull().sum().)

4. How did you handle the missing values?

We used mean imputation, meaning each missing value was replaced with the average value of that column:

df = df.fillna(df.mean(numeric_only=True))
5. Why is scaling important before applying K-Means?

K-Means is distance-based, so features with larger ranges (like BALANCE or PURCHASES) would dominate the clustering. Scaling ensures all features contribute equally by putting them on the same scale.

We used StandardScaler to normalize the data.

6. Which K value did you choose? Explain using elbow + silhouette score.

You choose K where:

The elbow curve starts to flatten (inertia stops decreasing significantly)
The silhouette score is relatively high compared to other K values

 In most cases for this dataset, a good choice is often K = 4 or K = 5, depending on your plots.

7. Describe each customer segment (cluster summary)

Based on typical credit card segmentation:

Cluster 0: Low activity customers (low balance, low purchases)
Cluster 1: Regular spenders (moderate purchases and balance)
Cluster 2: High spenders (high purchases, high credit usage)
Cluster 3: Cash advance users (high cash advance usage, possibly low purchases)
8. Which cluster may represent high-value customers?

The cluster with:

High PURCHASES
High CREDIT_LIMIT
High BALANCE but controlled usage

 Usually this is the high-spending cluster (often Cluster 2).

9. Which cluster may represent customers who rely more on cash advance?

The cluster with:

High CASH_ADVANCE
Possibly lower purchases

 Typically the cash-advance-heavy cluster (often Cluster 3).

10. How can a company use these clusters for marketing strategy?

Companies can:

Offer premium rewards to high-value customers
Send discount offers to low-activity users to increase engagement
Provide financial management tools to cash-advance users
Create personalized marketing campaigns for each segment
