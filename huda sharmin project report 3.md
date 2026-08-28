### **RFM CUSTOMER SEGMENTATION** 

_Using Recency, Frequency, Monetary Analysis and K-Means Clustering_ 

### **Submitted By** 

### **Huda sharmin Feroz ali** 

Guide: Satish R Pawale 

Organization: Syntelligence Tech, Pune 

GitHub Link: htps://github.com/hudasharmee2n-coder/customer_segmentaton_project 

Class: BCA TY (5th Sem) Roll Number: 67 

Project Type: Data Analytics / Machine Learning Dataset: Online Retail Transaction Data 

# **Abstract** 

This project presents a customer segmentation system based on RFM (Recency, Frequency, Monetary) analysis and K-Means clustering. The project uses an Online Retail transaction dataset containing 541,909 transaction records and eight original fields. After removing records without CustomerID, cancelled invoices, invalid quantities/prices, and duplicate records, 392,692 transaction rows remained. RFM values were then calculated for each customer. Extreme monetary and frequency values above the 99th percentile were removed for clustering, leaving 4,250 customer profiles. The RFM variables were standardized and K-Means clustering was applied. Four customer clusters were selected and interpreted as Champions, Loyal Customers, At Risk, and Hibernating/Lost customers. The resulting segments can support targeted marketing, customer retention, loyalty programs, cross-selling, and win-back campaigns. 

### **Keywords** 

RFM Analysis • Customer Segmentation • K-Means • Machine Learning • Retail Analytics 

• Customer Behaviour 

## **Table of Contents** 

1. Introduction 

2. Problem Statement 

3. Objectives 

4. Scope of the Project 

5. Applications 

6. Dataset Description 

7. Technologies and Tools 

8. Methodology 

9. Data Preprocessing 

10. RFM Analysis 

11. Exploratory Analysis 

12. K-Means Clustering 

13. Results and Segment Interpretation 

14. Business Recommendations 

15. Advantages 

16. Limitations 

17. Future Scope 

18. Conclusion 

19. References 

20. Appendix: Project Workflow 

# **1. Introduction** 

Understanding customer behaviour is an important part of modern retail analytics. A retailer may have thousands of customers, but not all customers purchase with the same frequency, spend the same amount, or remain active for the same length of time. Treating every customer in the same way can therefore lead to inefficient marketing and missed revenue opportunities. 

This project uses RFM analysis to describe customer purchasing behaviour through three measures: Recency, Frequency, and Monetary value. These measures are combined with K-Means clustering to automatically divide customers into groups with similar purchasing patterns. 

# **2. Problem Statement** 

The main problem addressed by this project is how to identify meaningful customer groups from transaction data so that a business can design more relevant marketing and retention strategies. The project aims to transform raw transaction records into actionable customer segments. 

# **3. Objectives** 

- Clean and prepare the Online Retail transaction dataset. 

- Calculate customer-level Recency, Frequency, and Monetary (RFM) metrics. 

- Identify patterns in customer purchasing behaviour. 

- Standardize RFM variables so that they can be compared during clustering. 

- Use K-Means clustering to create customer segments. 

- Interpret each segment in business terms. 

- Provide practical recommendations for marketing and customer relationship management. 

# **4. Scope of the Project** 

- The project focuses on transaction-based customer segmentation. It covers data cleaning, RFM feature engineering, exploratory visualization, feature scaling, K-Means clustering, segment interpretation, and business recommendations. It does not attempt to build a sales forecasting model, recommendation engine, churn prediction model, or real-time customer system. 

# **5. Applications** 

|**Applicaton**|**Purpose**|
|---|---|
|Targeted Marketng|Create diferent campaigns for high-value, loyal,<br>inactve, and at-risk customers.|
|Customer Retenton|Identfy customers whose recency and<br>purchasing actvity indicate a risk of becoming<br>inactve.|
|Loyalty Programs|Give Champions and other valuable customers<br>VIP rewards, early access, or loyalty benefts.|
|Cross-Selling and Upselling|Encourage Loyal Customers to increase<br>purchase frequency or move toward the<br>Champion segment.|
|Win-Back Campaigns|Use special ofers and reminders to re-engage<br>Hibernatng/Lost customers.|
|Marketng Budget Optmizaton|Prioritze marketng resources toward segments<br>with stronger potental returns.|



# **6. Dataset Description** 

The notebook uses the Online Retail dataset. The original dataset contains 541,909 transaction records and eight columns. The fields identified in the project are: 

|**Field**|**Descripton**|
|---|---|
|InvoiceNo|Invoice number identfying a transacton.|
|StockCode|Product/item code.|
|Descripton|Product descripton.|
|Quantty|Number of units purchased.|
|InvoiceDate|Date and tme of the transacton.|
|UnitPrice|Price per unit.|
|CustomerID|Customer identfer.|
|Country|Customer's country.|



# **7. Technologies and Tools** 

|**Tool**|**Use in Project**|
|---|---|
|Python|Programming language used for data analysis<br>and machine learning.|
|Pandas|Data loading, cleaning, transformaton,<br>grouping, and aggregaton.|
|Matplotlib|Visualizaton of distributons, WCSS, and<br>customer cluster counts.|
|Seaborn|Statstcal visualizatons such as histograms and<br>boxplots.|
|Scikit-learn|StandardScaler and KMeans implementaton.|
|Jupyter Notebook|Interactve environment used to execute and<br>document the analysis.|
|Excel|Source format of the Online Retail dataset.|



# **8. Methodology** 

The project follows the workflow below: 

- Load the Online Retail dataset. 

- Inspect the data structure and missing values. 

- Remove customers without CustomerID. 

- Remove cancelled invoices. 

- Remove transactions with non-positive Quantity or UnitPrice. 

- Remove duplicate records. 

- Calculate TotalPrice = Quantity × UnitPrice. 

- Create customer-level Recency, Frequency, and Monetary metrics. 

- Remove extreme Frequency and Monetary values above the 99th percentile. 

- Standardize the RFM variables. 

- Evaluate K values using the WCSS/elbow approach. 

- Apply K-Means with four clusters. 

- Compare cluster-level RFM averages and visualize segment behaviour. 

- Assign business meanings and recommendations to the segments. 

# **9. Data Preprocessing** 

The original dataset contained 541,909 rows. The notebook removed records with missing CustomerID, cancelled invoices identified by InvoiceNo beginning with 'C', transactions with Quantity ≤ 0, transactions with UnitPrice ≤ 0, and duplicate rows. After these cleaning operations, 392,692 rows remained. 

A new TotalPrice variable was calculated as Quantity multiplied by UnitPrice. This value represents the transaction-level monetary contribution used in the customer-level Monetary calculation. 

# **10. RFM Analysis** 

RFM analysis converts transaction history into three customer-level behavioural measures: 

|**Metric**|**Meaning**|
|---|---|
|Recency|Number of days since the customer's most<br>recent purchase. Lower values indicate more<br>recent actvity.|
|Frequency|Number of unique invoices associated with the<br>customer. Higher values indicate more frequent<br>purchasing.|
|Monetary|Total transacton value generated by the<br>customer. Higher values indicate greater<br>spending.|



The reference date was defined as one day after the maximum InvoiceDate in the cleaned transaction data. Recency was calculated from this reference date to each customer's latest purchase. Frequency was calculated using the number of unique InvoiceNo values, while Monetary was the sum of TotalPrice. 

# **11. Exploratory Analysis** 

The notebook visualizes the distributions of Recency, Frequency, and Monetary values using histograms. The project also examines the cluster distribution and uses boxplots to compare the RFM measures across clusters. 

To reduce the effect of extreme observations on clustering, customers above the 99th percentile of Monetary and Frequency were excluded. This produced 4,250 customer profiles for the clustering stage. 

# **12. K-Means Clustering** 

Before clustering, the three RFM variables were standardized using StandardScaler. Standardization is important because the variables are measured on different scales. K-Means was then evaluated for k values from 1 to 10 using Within-Cluster Sum of Squares (WCSS). Based on the notebook workflow, four clusters were selected. 

K-Means was configured with n_clusters=4, random_state=42, and n_init=10. The model assigned every prepared customer profile to one of four clusters. 

# **13. Results and Segment Interpretation** 

The following table reports the cluster-level mean values produced by the notebook. These averages form the basis for the business interpretation of each segment. 

|**Cluster**|**Mean Recency**|**Mean Frequency**|**Mean Monetary**|**Interpretaton**|
|---|---|---|---|---|
|0|51.58|2.25|683.27|At Risk|
|1|19.53|14.53|7,430.16|Champions|
|2|252.54|1.47|429.20|Hibernatng / Lost|
|3|30.35|7.06|2,637.40|Loyal Customers|



### **Cluster 1 – Champions** 

This segment has the lowest mean Recency (19.53 days), the highest mean Frequency (14.53), and the highest mean Monetary value (7,430.16). These customers are highly active, purchase frequently, and generate substantial value. 

Recommended action: protect the relationship through loyalty rewards, VIP treatment, early access to products, and personalized offers. 

### **Cluster 3 – Loyal Customers** 

This group has a low mean Recency of 30.35 days and relatively strong purchasing activity, with mean Frequency of 7.06 and mean Monetary value of 2,637.40. They are valuable active customers with potential to become Champions. 

Recommended action: use upselling, cross-selling, personalized recommendations, and loyalty incentives. 

### **Cluster 0 – At Risk** 



<!-- Start of picture text -->
25<br>ie)<br>350 17500 8<br>300 20 15000<br>0 0<br>250 8 12500<br>Fn > 15 .<br>&‘ 200 fe) 8 y5 Oo6  £| 10000<br>@ ; . |<br>150 2 10 7500 Q<br>100 ) 5000 a)<br>fe)<br>50 5 fsfa ) 2500<br>°<br>00—<br>0<br>01 2 3 0 1 2 3 0 1 2 3<br>Cluster Cluster Cluster<br><!-- End of picture text -->

Produces actionable groups that can directly support marketing decisions. 

Scalable to larger transaction datasets with suitable computing resources. 

# **16. Limitations** 

RFM uses only three behavioural dimensions and does not directly include product preferences, demographics, or customer satisfaction. 

K-Means requires a chosen number of clusters; the project selected four clusters using the WCSS/elbow workflow. 

Outlier removal changes the customer population used for clustering. 

Cluster labels such as 'Champions' and 'At Risk' are business interpretations, not labels directly learned by K-Means. 

The notebook does not evaluate campaign response or prove that the recommendations increase revenue. 

# **17. Future Scope** 

Add customer lifetime value (CLV) and churn prediction to complement RFM. 

Compare K-Means with hierarchical clustering, DBSCAN, or Gaussian mixture models. 

Use automated model-selection and cluster-quality measures such as silhouette score. 

Create an interactive dashboard for monitoring customer segments. 

Track how customers move between segments over time. 

Connect segments to actual campaign outcomes and optimize marketing ROI. 

Include country, product category, seasonality, and basket-level features for richer segmentation. 

# **18. Conclusion** 

The project successfully demonstrates how transaction-level retail data can be transformed into useful customer segments using RFM analysis and K-Means clustering. The analysis began with 541,909 transaction records and, after data cleaning, retained 392,692 valid transaction rows. Customer-level RFM features were created, extreme Frequency and Monetary observations were removed, and 4,250 customer profiles were standardized for clustering. 

Four distinct behavioural groups were identified. Cluster 1 represents the strongest customers and is interpreted as Champions; Cluster 3 represents Loyal Customers; Cluster 0 represents At Risk customers; and Cluster 2 represents Hibernating/Lost customers. These segments provide a practical foundation for targeted marketing, loyalty management, customer retention, and win-back strategies. 

# **19. References** 

Project source notebook: RFM_Customer_Segmentation.ipynb. 

Online Retail transaction dataset used by the project (loaded from Online Retail.xlsx). 

Pandas documentation and Python data-analysis workflow used in the notebook. 

Scikit-learn KMeans and StandardScaler methods used in the notebook. 

Matplotlib and Seaborn visualizations used for exploratory and cluster analysis. 

# **20. Appendix: Project Workflow** 

Core computational workflow represented in the submitted notebook: 

1. Load Online Retail.xlsx 

2. Remove missing CustomerID records 

3. Remove cancelled invoices 

4. Keep Quantity > 0 and UnitPrice > 0 

5. Remove duplicates 

6. TotalPrice = Quantity × UnitPrice 

7. Calculate customer-level Recency, Frequency and Monetary 

8. Remove Frequency and Monetary values above the 99th percentile 

9. Standardize RFM features 

10. Evaluate k = 1...10 using WCSS 

11. Fit K-Means with 4 clusters 

12. Compare cluster averages and visualize segments 

13. Interpret clusters and recommend business actions 

### **— End of Project Report —** 

