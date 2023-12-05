# P2P-Bondora-Financial-risk-modelling-of-European-lending-platform
The main purposes of this analysis are to summarize the characteristics of variables that can affect the loan status and to get some ideas about the relationships among variables. Find the target variables EMI, ELA and PROI from the given data and find how the variables can affect the target variables.
# Team:
1)Vijaya Pawar  
2)Nithin S    
3)Abhishek Jog   
4)Aman Gupta   
5)Ankita Mane   
6)Fahad Sarfraz    
7)Maruf Abduzohirov  
8)Nagendra Prasad  
9)Navika    
10)Shubham Dhadag  
11)uktamnishonov  
12)Vivek  

# Table Content   
1.REQUIREMENT AND ANALYSIS  
2.PROJECT PLANNING   
3.DESIGN     
4.DEVELOPMENT  
5.DEPLOYMENT     
6.ACKNOWLEDGEMENT   
7. CONTACT  

# 1.REQUIREMENT AND ANALYSIS
## 1 INTRODUCTION 
• Bondora is an investment platform that stands at the forefront of the peer-to-peer (P2P) lending landscape, facilitating direct connections between borrowers and lenders and revolutionizing traditional lending paradigms.  
 • Bondora has carved its niche as a pioneering European P2P lending platform, facilitating direct interactions between borrowers seeking financial assistance and investors seeking diversification and returns   
• The requirements for this project encompass the following aspects:  
 1. Conducting credit risk assessment for new borrowers.   
2. Determining the probability of default for new borrowers.  

## 2 About Data

• The data for the study has been retrieved from a publicly available dataset provided by a leading European P2P lending platform (Bondora).   
• The dataset, sourced from Bondora, encompasses defaulted and non-defaulted loans spanning from March 1, 2009, to January 27, 2020.   
• The data provides a comprehensive view of borrower demographics, financial profiles, and loan transactions.   
• The project emphasizes the importance of minimizing default risks while maximizing returns, pivotal in navigating P2P lending complexities.  
 • By examining borrower behavior, financial aspects, and asymmetric information, the project contributes to a nuanced understanding of credit risk dynamics.   
• The analysis aims to extract meaningful insights from the dataset, potentially revealing trends, correlations, and factors that are significant predictors of default. These insights can shape future lending practices and inform risk assessment methodologies

##  3 Tools and Technology 

• Pandas for Data Preprocessing
 • Pandas, Numpy, Matplotlib and Seaborn for Exploratory Data Analysis(EDA) 
• Pandas, Numpy and PCA for Feature Engineering 
• Pandas, Numpy, sklearn and pickle for Modeling and pipeline 
• AWS – EC2 for Deployment

# 2.PROJECT PLANNING

## Introduction to Project Planning:
In this section, we detail the strategic planning and execution of the financial risk modelling project using P2P Bondora lending platform dataset. This project aimed to develop predictive models to asses the likelihood of loan default and additional predictions for EMI, ELA and PROI. Also, proving insights into key factors influencing lending risk.

## Project Goals and Objectives:

1.	Develop predictive models to accurately determine whether the Borrower’s loan application is likely to result in a default.   
2.	Create models to predict the Equated Monthly Installments (EMI), Eligible Loan Amount (ELA), and Preferred Rate of Interest for each loan application (PROI).

## Scope and Deliverables:

The scope of the project included working extensively with the P2P Bondora lending platform dataset. The main deliverables are as follows:  
•	A cleaned and preprocessed dataset suitable for predictive modelling.  
•	Trained machine learning models for loan default prediction.  
•	Models to predict EMI, ELA and PROI for loan applications.  
•	Thorough evaluation of model performance and accuracy.  

# 3.DESIGN




![99](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/1b76621c-7a24-4fda-9dce-c596d6a9bb8d)




![13](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/ba4f8946-a5b3-4891-9267-ceaa3843b3c4)





![14](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/45df1f56-37ad-4f41-a84c-e8ad3c5f5f34)





![12](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/355c98d7-b4ce-4a0a-ac7f-f1d63524ae76)

# 4.DEVELOPMENT  

4.1 Data preprocessing.   
4.2 Exploratory Data Analysis   
4.3 Feature Engineering for Default Status   
4.4 Classification Modeling   
4.5 Feature Selection ( preferred EMI , preferred ROI , ELA)   
4.6 Regression Modeling  
4.7 Pipeline Creation   
4.8 Deployment     
4.9 UI App creation  

# 4.1 Data Preprocessing
•	The dataset contains 118 columns and 134529 rows Range Index.  
•	Apart from missing value features there are some features which will have no role in default prediction like 'ReportAsOfEOD', 'LoanId', 'LoanNumber', 'ListedOnUTC', 'UserName','LoanApplicationStartedDate', 'ApplicationSignedWeekday', 'DateOfBirth', 'IncomeFromPension', 'IncomeFromFamilyAllowance', 'IncomeFromSocialWelfare', 'IncomeFromLeavePay', 'IncomeFromChildSupport', 'IncomeOther', 'StageActiveSince',    
•	Removing the columns having missing value for then 40% missing values. After removing null columns now we have 68 columns and 134529 Rows for further use.    
•	Here status columns is the variable which helps to create target variable. The reason for not making status as target variable is that it has there unique values current, Late and repaid. There is no default features but there is a feature default date which tells us when the borrower has defaulted means on which date the borrower defaulted. So, we will be combining Status and Default date features for creating target variable.   
•	df_2['Defaultstatus'].value_counts()   
       1    91614   
       0    42904      
       Name: Defaultstatus, dtype: int64
•	We saw in numeric column distribution there are many columns which are present as numeric but they are actually categorical as per data description such as Verification type, Language code, Gender, Use of loan, Education, Marital status, employmentStatus, OccupationArea etc, so we will convert these features to categorical features.    
•	Target variable creation for risk evaluation and assessment:    
After a through research to identify 3 new procedures to evaluate the 3 target assessment features agreed upon on the planning stage we came up with these algorithms.    
•	Now our data is ready for EDA.   

# 4.2 Exploratory Data Analysis

•	Univariate analysis  
•	Bivariate analysis  
•	Multivariate analysis  

Blue shows the data of whole dataset(default and non default) while red shows only the dataset of default condition.  

No. of loans taken in which year
plt.figure(figsize = (20,5))  
plt.subplot(1,2,1)  
df_1.LoanYear.value_counts().plot(kind = 'bar')  
plt.subplot(1,2,2)   
df_default.LoanYear.value_counts().plot(kind = 'bar', color = 'r')  
print(df_1.LoanYear.value_counts())  
df_default.LoanYear.value_counts()  

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/2c7a6545-a9e1-4af7-8434-355c3bd62817)

plt.figure(figsize = (15,10))  
plt.subplot(3,2,1)  
sns.distplot(df_1.BidsPortfolioManager)  
plt.subplot(3,2,2)  
sns.distplot(df_default.BidsPortfolioManager, color = 'r')  
plt.subplot(3,2,3)  
sns.distplot(df_1.BidsApi)  
plt.subplot(3,2,4)  
sns.distplot(df_default.BidsApi, color = 'r')  
plt.subplot(3,2,5)  
sns.distplot(df_1.BidsManual)  
plt.subplot(3,2,6)  
sns.distplot(df_default.BidsManual, color = 'r')  
plt.show()

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/cc61b11d-b316-48e0-8dc8-d33a71687bb2)

plt.figure(figsize = (20,5))  
plt.subplot(1,2,1)  
df_1.NewCreditCustomer.value_counts().plot(kind = 'bar')  
plt.subplot(1,2,2)  
df_default.NewCreditCustomer.value_counts().plot(kind = 'bar', color = 'red')  
print(df.NewCreditCustomer.value_counts())  
df_default.NewCreditCustomer.value_counts()  


![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/d50edb22-1310-42de-9610-148f943af694)

plt.figure(figsize = (15,15))   
plt.subplot(3,2,1)   
sns.distplot(df_1.AppliedAmount)  
plt.subplot(3,2,2)   
sns.distplot(df_default.AppliedAmount, color = 'r')  
plt.subplot(3,2,3)  
sns.distplot(df_1.Amount)  
plt.subplot(3,2,4)  
sns.distplot(df_default.Amount, color = 'r')  
plt.subplot(3,2,5)  
sns.distplot(df_1.Interest)  
plt.subplot(3,2,6)  
sns.distplot(df_default.Interest, color = 'r')

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/4e3ee9e9-90a7-4bbc-91eb-cc4c8b5b0d40)

plt.figure(figsize = (15,5))  
plt.subplot(1,2,1)  
sns.histplot(df_1.Age)  
plt.grid()  
plt.subplot(1,2,2)  
sns.histplot(df_default.Age, color = 'r')  
plt.grid()  

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/74734f70-59f7-47ad-a245-5afd3a30f192)

plt.figure(figsize = (20,5))  
plt.subplot(1,2,1)  
df_1.Country.value_counts().plot(kind = 'pie', autopct = '%1.1f%%')   
plt.subplot(1,2,2)   
df_default.Country.value_counts().plot(kind = 'pie', autopct = '%1.1f%%')  
print(df_1.Country.value_counts())  
df_default.Country.value_counts()  
from 296 loan from sk country, 269 are the default ones
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/dbf33c02-a5b2-459e-b3d6-6950637a6b5a)
plt.figure(figsize = (20,5))  
plt.subplot(1,2,1)   
df_1.LoanTenure.value_counts().plot(kind = 'pie', autopct = '%1.1f%%')  
plt.subplot(1,2,2)  
df_default.LoanTenure.value_counts().plot(kind = 'pie', autopct = '%1.1f%%')  
print(df_1.LoanTenure.value_counts())  
df_default.LoanTenure.value_counts()  

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/088f8b6d-f5d1-4905-be70-efeb6ac5887f)

plt.figure(figsize = (15,5))  
plt.subplot(1,2,1)  
sns.distplot(df_1.MonthlyPayment)  
plt.grid()  
plt.subplot(1,2,2)  
sns.distplot(df_default.MonthlyPayment, color = 'red')  
plt.grid()

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/d081b0eb-5125-4d87-bc85-66184359f17c)
plt.figure(figsize = (20,5))  
plt.subplot(1,2,1)  
df_1.EmploymentStatus.value_counts().plot(kind = 'bar')  
plt.subplot(1,2,2)  
df_default.EmploymentStatus.value_counts().plot(kind = 'bar',color = 'red')  
print(df_1.EmploymentStatus.value_counts(), df_1.EmploymentStatus.isnull().sum())  
df_default.EmploymentStatus.value_counts(), df_default.EmploymentStatus.isnull().sum()

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/03f9122b-2eb2-4e78-8905-b8ead7ec7698)
plt.figure(figsize = (15,5))  
plt.subplot(1,2,1)  
sns.distplot(df_1.IncomeTotal)  
plt.grid()  
plt.subplot(1,2,2)  
sns.distplot(df_default.IncomeTotal, color = 'red')  
plt.grid()  
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/7049a63d-8877-40ed-bdaa-8641e2db4ce9)

plt.figure(figsize = (20,5))  
plt.subplot(1,2,1)  
df_1.VerificationType.value_counts().plot(kind = 'pie', autopct = '%1.1f%%')  
plt.subplot(1,2,2)  
df_default.VerificationType.value_counts().plot(kind = 'pie', autopct = '%1.1f%%')  
print(df_1.VerificationType.value_counts())  
df_default.VerificationType.value_counts()

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/ecc78164-a84d-406e-8e08-0dcb2f403f0d)

plt.figure(figsize = (20,5))  
plt.subplot(1,2,1)  
df_1.Gender.value_counts().plot(kind = 'bar')  
plt.subplot(1,2,2)  
df_default.Gender.value_counts().plot(kind = 'bar', color = 'red')  
print(df_1.Gender.value_counts())  
df_default.Gender.value_counts()  
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/ed9305b5-a1ab-4a99-9f3f-411215ba68b9)
Employment time with the current employer  
plt.figure(figsize = (20,5))  
plt.subplot(1,2,1)  
df_1.EmploymentDurationCurrentEmployer.value_counts().plot(kind = 'bar')  
plt.subplot(1,2,2)  
df_default.EmploymentDurationCurrentEmployer.value_counts().plot(kind = 'bar', color = 'red')  
print(df_1.EmploymentDurationCurrentEmployer.value_counts(),   
df_1.EmploymentDurationCurrentEmployer.isnull().sum())  
df_default.EmploymentDurationCurrentEmployer.value_counts(),   df_default.EmploymentDurationCurrentEmployer.isnull().sum()
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/b1282a0d-070b-4d7f-bee6-6b592753f600)
plt.figure(figsize = (20,5))  
plt.subplot(1,2,1)  
df_1.HomeOwnershipType.value_counts().plot(kind = 'bar')  
plt.subplot(1,2,2)  
df_default.HomeOwnershipType.value_counts().plot(kind = 'bar', color = 'red')  
print(df_1.HomeOwnershipType.value_counts(), df_1.HomeOwnershipType.isnull().sum())  
df_default.HomeOwnershipType.value_counts(), df_default.HomeOwnershipType.isnull().sum()
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/f69ee24a-6148-41b2-a377-10563b427e79)
plt.figure(figsize = (15,5))  
plt.subplot(1,2,1)  
sns.histplot(df_1.ExistingLiabilities)  
plt.grid()  
plt.subplot(1,2,2)  
sns.histplot(df_default.ExistingLiabilities, color = 'red')  
plt.grid()  
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/c93b566c-378b-4111-9a33-86e21fc6aa2a)
its the probability of Expected Loss calculated by the current Rating model  
plt.figure(figsize = (15,5))  
plt.subplot(1,2,1)  
sns.histplot(df_1.ExpectedLoss)  
plt.grid()  
plt.subplot(1,2,2)  
sns.histplot(df_default.ExpectedLoss, color = 'red')  
plt.grid()
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/89cd27ba-ce58-47e7-9942-a67e9511e25e)
probabilty of loss which assumed default is actually default loan  
plt.figure(figsize = (20,5))  
plt.subplot(1,2,1)  
sns.distplot(df_1.LossGivenDefault)  
plt.subplot(1,2,2)  
sns.distplot(df_default.LossGivenDefault, color = 'red')  
plt.show()
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/0ae865d6-f478-4473-9aea-208b2da57cf0)
Expected Return calculated by the current Rating model  
plt.figure(figsize = (20,5))  
plt.subplot(1,2,1)  
sns.distplot(df_1.ExpectedReturn)  
plt.subplot(1,2,2)  
sns.distplot(df_default.ExpectedReturn, color = 'red')  
plt.show()
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/0f67a8c8-3116-4427-9e3b-b3a5d2854d9c)
Probability of Default, refers to a loan’s probability of default within one year horizon  
plt.figure(figsize = (15,5))  
plt.subplot(1,2,1)  
sns.histplot(df_1.ProbabilityOfDefault)  
plt.grid()  
plt.subplot(1,2,2)  
sns.histplot(df_default.ProbabilityOfDefault, color = 'red')  
plt.grid()
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/5e776acb-c367-4ffb-b4b2-2ff6ebc181f2)

already we have converted the status feature into 2 category of deafault and not default case  
df_1['Status'].value_counts().plot(kind = 'bar')  
df_1['Status'].value_counts()   

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/b1597df7-18de-4e85-bf13-9d568a117666)

sns.boxplot(df_1.AppliedAmount)  
plt.show()  

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/193d635b-134e-49d0-85a9-8e186aa58cb7)

sns.boxplot(df_1.Amount)  
plt.show()   

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/55009a8f-f9cc-4d16-9b8f-6c7ea729a939)

sns.boxplot(df_1.Interest)  
plt.show()    

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/70b095f2-6c0d-4d72-9849-d0d438c05376)

loaninfo('Status')   

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/ea71ee68-77a2-4847-907b-9c32067cfab4)

Ploting a scatter plot against Amount and the LoanDuration to find any pattern  
sns.scatterplot(x='Amount',y="LoanTenure",data=df_1,hue='Defaultstatus')  
plt.show()  

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/60fceaf0-8a6e-4345-b72b-3bd53b59d239)    

Ploting a scatter plot against Amount and the Monthly Payment to find any pattern  
sns.scatterplot(x='Amount',y='MonthlyPayment',data=df_1,hue='Defaultstatus')  
plt.show() 

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/09029ea3-b345-41b5-b463-63a36c897090)

sns.scatterplot(x='Interest',y="LoanTenure",data=df_1,hue='Defaultstatus')  
plt.show()

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/a2fc3cc8-6c54-4a1a-8458-523ec8dda602)   

sns.scatterplot(x='Amount',y='ProbabilityOfDefault',data=df_1,hue='Defaultstatus')  
plt.show()   

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/a479f660-e6b4-4c68-8f08-8b610c3e9968)    

# Eda for target variable(EMI, ELA and ROI)
sns.histplot(df_1['EMI']) 

 ![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/22e6b25f-9b7f-48ca-9b76-d5533a46e84e)    
 
sns.histplot(df_1['ROI'])   

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/d1ad495a-1ca8-4cb7-9849-2771e96479e4)   

sns.histplot(df_1['PROI'])   

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/1528e84e-003d-4421-a03e-15f94d6ddb9b) 

sns.histplot(df_1['ELA'])    

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/04b35898-bd52-40de-807c-010a6378498e)   

sns.scatterplot(x='Interest', y='EMI', data=df_1)    

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/f461d843-b098-4ca4-a6c2-de6819315ef3)    

sns.scatterplot(x='LoanTenure', y='EMI', data=df_1)    

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/39896382-5abe-46d1-b572-faf1e2c953a0)     

sns.scatterplot(x='Amount', y='EMI', data=df_1)  

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/ab3c9c7a-d0a1-4f6a-8491-6bd90990d4ae)    

sns.scatterplot(x='Amount', y='EMI', data=df_1)    

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/28168799-454d-4bdf-8dd3-6da85d7417b9)     

sns.scatterplot(x='Amount', y='EMI', data=df_1)   

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/28a93728-74e8-40f8-bf1a-244e8e7e5a14)    

sns.scatterplot(x='MonthlyPayment', y='EMI', data=df_1)    

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/94f571ba-b096-4dd8-8fc3-6c9eb5241aa9)    

sns.scatterplot(x='IncomeTotal', y='EMI', data=df_1)  

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/736efe5a-a3d9-42c9-8998-2465434e0f3d)

sns.scatterplot(x='DebtToIncome', y='EMI', data=df_1) 

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/706deb24-ae56-472c-9143-73c6f8639a96)   

sns.boxplot(x='NewCreditCustomer', y='EMI', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/2bf3250e-376e-4f39-8e4d-da26926f9f3b)

sns.scatterplot(x='AppliedAmount', y='ROI', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/4892c678-fe18-4233-929e-3be5af816f8d)

sns.scatterplot(x='Interest', y='ROI', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/701b4c88-9ea9-4d2d-9094-d7048f56d29c)

sns.scatterplot(x='Amount', y='ROI', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/69848a2d-03e7-464f-bf97-85e2b5b1185d)

sns.scatterplot(x='DebtToIncome', y='ROI', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/0c4fc777-960e-4fc2-92ef-371840056723)

sns.scatterplot(x='InterestAmount', y='ROI', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/3bd90af8-f580-4265-90f7-1b09d902aa62)

sns.scatterplot(x='TotalAmount', y='ROI', data=df_1) 

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/d813bb68-797d-4659-9b54-36b0e38fbb7b)

sns.scatterplot(x='Amount', y='PROI', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/46c300f3-4fd8-415d-8297-2df093f16804)

sns.scatterplot(x='AppliedAmount', y='PROI', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/d8c72e0d-c304-4e20-b375-cb3ea0fabcbc)

sns.scatterplot(x='DebtToIncome', y='PROI', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/74617d6c-73e6-4431-862c-f11c875414da)

sns.scatterplot(x='AppliedAmount', y='ELA', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/7640734a-b5ca-41c1-be09-42c6ba9c55de)

sns.scatterplot(x='Interest', y='ELA', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/85f43dff-b4da-4790-bed7-7bb1d24c90b5)

sns.scatterplot(x='LoanTenure', y='ELA', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/ab808e7d-cc66-417e-b952-910600eee23d)

sns.scatterplot(x='DebtToIncome', y='ELA', data=df_1)

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/5e202e66-fc13-492b-b29e-66c89b561957)


## Multivariate Analysis

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/5097bd8b-c547-4ce5-a214-58c6eba374a6)

# 4.3 Feature Engineering for Default Status
•	Dropping the features which were used in target variables calculations¶. 'InterestAmount', 'Amount', 'AppliedAmount', 'Interest', 'LoanTenure', 'TotalAmount', 'ROI', 'IncomeTotal', 'DebtToIncome'.  
•	Removing unnecessary columns like 'BiddingStartedOn', 'LoanDate', 'FirstPaymentDate', 'MaturityDateOriginal', 'MaturityDate_Last', 'County','City', 'CreditScoreEsMicroL', 'Education', 'OccupationArea', 'CreditScoreEsMicroL',   

## Handling Missing Values:  
 Filling the obsereved missing values  
df_2.HomeOwnershipType.fillna(df_2['HomeOwnershipType'].mode, inplace = True)  
df_2.EmploymentStatus.fillna(df_2['EmploymentStatus'].mode, inplace = True)  
df_2['MonthlyPayment'].fillna(df_2['MonthlyPayment'].mean(), axis = 0, inplace = True)  

Data Encoding:  
df_2['WorseLateCategory'] = df_2['WorseLateCategory'].replace('61-90', 3)  
df_2['WorseLateCategory'] = df_2['WorseLateCategory'].replace('31-60', 2)  
df_2['WorseLateCategory'] = df_2['WorseLateCategory'].replace(['91-120', '121-150'], 4)   
df_2['WorseLateCategory'] = df_2['WorseLateCategory'].replace(['01-Jul','Aug-15','16-30'], 1)  
df_2['WorseLateCategory'] = df_2['WorseLateCategory'].replace(['180+','151-180'], 5)  
df_2['WorseLateCategory'].fillna(0, inplace = True)  
lb = LabelEncoder()  
colums_lb =   
['VerificationType','NewCreditCustomer','Gender','Country','MaritalStatus','ActiveScheduleFirstPaymentReached','Status', 'Restructured', 'Rating']  
Encoding the UseofLoan Column  
df_2['UseOfLoan'] = df_2['UseOfLoan'].replace(['Home improvement','Real estate','Loan consolidation'],   1)df_2['UseOfLoan'] = df_2['UseOfLoan'].replace(['Vehicle','Business'],  
2)df_2['UseOfLoan'] = df_2['UseOfLoan'].replace(['Travel','Health','Education'], 
3)df_2['UseOfLoan'] = df_2['UseOfLoan'].replace(['Other'],  4)
Encoding the EmployementStatus column
df_2=df_2.replace({'EmploymentStatus' : { 'Unemployed' : 1,'Partially employed' : 2,'Fully employed':3,'Self-employed':4,'Entrepreneur':5,'Retiree':6}})
Ecoding the EmploymentDurationCurrentEmployer Column
df_2['EmploymentDurationCurrentEmployer'] = df_2['EmploymentDurationCurrentEmployer'].replace(['Other'], 1)
df_2['EmploymentDurationCurrentEmployer'] = df_2['EmploymentDurationCurrentEmployer'].replace(['TrialPeriod','UpTo1Year',], 2)
df_2['EmploymentDurationCurrentEmployer'] = df_2['EmploymentDurationCurrentEmployer'].replace(['UpTo2Years','UpTo3Years','UpTo4Years'], 3)
df_2['EmploymentDurationCurrentEmployer'] = df_2['EmploymentDurationCurrentEmployer'].replace(['UpTo5Years','MoreThan5Years','Retiree'],4)
Encoding the OcuupationArea Column
df_2['OccupationArea'] = df_2['OccupationArea'].replace([1], 1)
df_2['OccupationArea'] = df_2['OccupationArea'].replace([2,3,4,5,6], 2)
df_2['OccupationArea'] = df_2['OccupationArea'].replace([7,8,9,10], 3)
df_2['OccupationArea'] = df_2['OccupationArea'].replace([11,12,13,14],4)
df_2['OccupationArea'] = df_2['OccupationArea'].replace([15,16,17,18,19],4)

Encoding the HomeOwnershipType Column
df_2['HomeOwnershipType'] = df_2['HomeOwnershipType'].replace(['Mortgage',], 1)  
df_2['HomeOwnershipType'] = df_2['HomeOwnershipType'].replace(['Owner','Joint ownership','Living with parents'], 2)  
df_2['HomeOwnershipType'] = df_2['HomeOwnershipType'].replace(['Tenant, unfurnished property','Tenant, pre-furnished property'], 3)   
Encoding the DefaultStatus Column  
df_2=df_2.replace({'Defaultstatus' : { 'Default' : 0,'Not-Default' : 1}})  
for i in colums_lb:  
    df_2[i]=lb.fit_transform(df_2[i])
    
## Handling Outliers
columns = ['BidsPortfolioManager','BidsApi','BidsManual','ApplicationSignedHour','Age','AppliedAmount','Amount','Interest',"LoanTenure", 'MonthlyPayment', 'IncomeFromPrincipalEmployer', 'IncomeTotal', 'ExistingLiabilities', 'LiabilitiesTotal','RefinanceLiabilities',' DebtToIncome', 'FreeCash', 'MonthlyPaymentDay', 'PlannedInterestTillDate', 'ExpectedLoss', 'LossGivenDefault', 'ExpectedReturn', 'ProbabilityOfDefault', 'PrincipalOverdueBySchedule', 'PrincipalPaymentsMade','InterestAndPenaltyPaymentsMade', 'PrincipalBalance', 'InterestAndPenaltyBalance', 'AmountOfPreviousLoansBeforeLoan', 'PreviousRepaymentsBeforeLoan', 'PreviousEarlyRepaymentsCountBeforeLoan', 'NextPaymentNr', 'NrOfScheduledPayments', 'LoanYear']    
for i in columns:   
        Q1 = df_2[i].quantile(0.25)    
    Q3 = df_2[i].quantile(0.75)    
    IQR = Q3 - Q1        
    ft_max = Q3 + 1.5*IQR   
    ft_min = Q1 - 1.5*IQR   
    df_2[i] = np.where(df_2[i] > ft_max, ft_max, df_2[i])   
    df_2[i] = np.where(df_2[i] < ft_min, ft_min, df_2[i])    
sns.boxplot(df_2['Amount'])    
plt.show()   

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/d5ebb0b2-48b1-4a66-92be-fcdc27ece124)

sns.boxplot(df_2['Interest'])
plt.show()

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/731c1214-eb12-41a0-9975-d358a38b7e74)

### Splittting data into training and testing
x = df_2.drop('Defaultstatus', axis = 1)  
y = df_2['Defaultstatus']  
x_train,x_test,y_train,y_test = train_test_split(x,y,test_size=0.2,random_state=0)  
X_train,Y_train = sampling.fit_resample(x_train,y_train)  
X_train.shape,Y_train.shape  

### Standardization  
scalar = StandardScaler()  
 Scaling the X_train dataset  
XS_train = pd.DataFrame(scalar.fit_transform(X_train),columns = X_train.columns)  
 Scaling the X_test dataset  
XS_test = pd.DataFrame(scalar.fit_transform(x_test),columns = x_test.columns)

### Feature Selection
plt.figure(figsize=(20,20))  
sns.heatmap(XS_train.corr(),annot=True)  
plt.show()
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/cca46db6-d19f-40e1-b6d1-908cfbb32968)
### Removing Constant Features:  
var_thres = VarianceThreshold(threshold = 0)  
var_thres.fit(XS_train)  
means we have two features whose variance is 0 or we can say that they have constant data  
cons_fet = [i for i in XS_train.columns if i not in XS_train.columns[var_thres.get_support()]]  len(cons_fet)  
cons_fet  
XS_train.drop(cons_fet,axis=1,inplace=True)  
XS_test.drop(cons_fet,axis=1,inplace=True)  

### Multicolinearity:
Developing a function which can retrieve the columns which shows multinearity  

### Mutual Information:
mutual_info = mutual_info_classif(XS_train,Y_train)  
mutual_info  
array([0.20169315, 0.1060333 , 0.1955464 , 0.01433886, 0.21638859,
       0.05593735, 0.04582366, 0.22598829, 0.01709734, 0.03353352,
       0.18540779, 0.17661884, 0.10458443, 0.12044686, 0.05983482,
       0.02788782, 0.02599009, 0.08541878, 0.04181927, 0.03348982,
       0.17065879, 0.07836144, 0.18930829, 0.15936651, 0.03772364,
       0.21898094, 0.02673044, 0.13267877, 0.19639441, 0.2540309 ,
       0.17724943, 0.39542758, 0.10376378, 0.41853536, 0.00582952,
       0.20793635, 0.13453254, 0.04451893, 0.13359603, 0.41853885,
       0.02524073, 0.07515113, 0.06301719, 0.51315476, 0.09276694,
       0.1103697 , 0.11289243])  

mutual_info = pd.Series(mutual_info)  
mutual_info.index = XS_train.columns  
mutual_info.sort_values(ascending=False)  
mutual_info.sort_values(ascending = False).plot.bar(figsize = (20,10))  
plt.show()  
![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/605169bb-8a34-4607-ad2f-cfbbebd649c7)
best_cols = SelectKBest(mutual_info_classif,k=25)  
best_cols.fit(XS_train,Y_train)  
select_fetr = XS_train.columns[best_cols.get_support()]  
select_fetr  
Index(['BidsPortfolioManager', 'BidsApi', 'BidsManual',
       'ApplicationSignedHour', 'Age', 'AppliedAmount', 'Interest',
       'MonthlyPayment', 'HomeOwnershipType', 'IncomeTotal',
       'ExistingLiabilities', 'MonthlyPaymentDay', 'PlannedInterestTillDate',
       'ExpectedLoss', 'LossGivenDefault', 'ExpectedReturn',
       'PrincipalOverdueBySchedule', 'Status', 'WorseLateCategory',
       'PrincipalPaymentsMade', 'PrincipalBalance',
       'InterestAndPenaltyBalance', 'NextPaymentNr', 'InterestAmount', 'ROI'],
      dtype='object')  
XS_trian = XS_train[select_fetr]  
XS_test = XS_test[select_fetr]

### Model Building before PCA
Lr_model = LogisticRegression()  
Lr_model.fit(XS_trian,Y_train)  
Lr_model.score(XS_test,y_test)  

### Principle Compound Analysis(PCA) Dimensionality Reduction Method¶
df_train = pd.concat([XS_trian,Y_train],axis=1)  
y_test = y_test.reset_index()  
y_test.drop('index',axis=1,inplace=True)  
df_test = pd.concat([XS_test,y_test],axis=1)  
df_3 = pd.concat([df_train,df_test],ignore_index=True)  
X = df_3.drop('Defaultstatus',axis=1)  
Y = df_3['Defaultstatus']  
pca = PCA(0.40)  
X_pca = pca.fit_transform(X)  
pca.n_components_  
X_pca = pd.DataFrame(X_pca)  
X_pca

# 4.4 Classification Modeling
## Logistics Regression
x_train,x_test,y_train,y_test = train_test_split(X_pca,Y,test_size=0.2,random_state=0)  
Lr_model = LogisticRegression()  
Lr_model.fit(x_train,y_train)  
Lr_model.score(x_test,y_test)  
y_pred = Lr_model.predict(x_test)  
Lr_model.predict_proba(x_test)  
print(confusion_matrix(y_pred, y_test))  
print(classification_report(y_pred, y_test))  
print(accuracy_score(y_pred, y_test))  
parameters = {
    'C': [0.01, 0.1, 1, 10, 100],  
     'penalty': ['l1', 'l2', 'Elasticnet', None],  
    'solver': ['lbfgs', 'liblinear', 'sag', 'saga']  
}   
lr_clf = GridSearchCV(Lr_model, param_grid=parameters, cv=5, n_jobs=-1)  
lr_clf.fit(x_train,y_train)  
lr_clf.best_params_  
y_pred_clf_lr = lr_clf.predict(x_test)

## Navie Bayes - GaussianNB

gnb = GaussianNB()  
gnb.fit(x_train, y_train)  
y_pred = gnb.predict(x_test)  
print(confusion_matrix(y_pred, y_test))  
print(classification_report(y_pred, y_test))  
print(accuracy_score(y_pred, y_test))  

## Navie Bayes - BernoulliNB

BNB = BernoulliNB()  
BNB.fit(x_train, y_train)  
y_pred = BNB.predict(x_test)  
print(confusion_matrix(y_pred, y_test))  
print(classification_report(y_pred, y_test))  
print(accuracy_score(y_pred, y_test))  

## Trying the model prediction using train dataset
y_pred = Lr_model.predict(x_train)  
print(confusion_matrix(y_pred, y_train))  
print(accuracy_score(y_pred, y_train))  
print(classification_report(y_pred, y_train))

## Conclusion
After building and evaluating three different models, here are the conclusions based on their accuracies: Logistic Regression Model: Accuracy: 83.23%   
Conclusion: The logistic regression model performed the best among the three models, achieving an accuracy of 83.23%. This suggests that the logistic regression model is well-suited for the given dataset and is able to capture the underlying patterns effectively. With its interpretability and relatively high accuracy, the logistic regression model may be a good choice for this problem. Naive Bayes Bernoulli Model: Accuracy: 81.43%   
Conclusion: The Naive Bayes Bernoulli model achieved an accuracy of 82.65%. While this is a respectable accuracy, it lags behind the logistic regression model's performance. The Naive Bayes Bernoulli model assumes independence between features and represents the data as binary features. Although it didn't perform as well as the logistic regression model, it can still be considered a useful and interpretable model, especially if interpretability is a key requirement. Naive Bayes Gaussian Model: Accuracy: 79.56%   
Conclusion: The Naive Bayes Gaussian model achieved an accuracy of 88.69%. This model assumes that the features follow a Gaussian (normal) distribution, which might not be the best assumption for all datasets. Despite that, it still performed well, falling in between the accuracy of the Bernoulli Naive Bayes and the logistic regression models.   
Overall, the logistic regression model demonstrated the highest accuracy, followed by the Naive Bayes Gaussian model and then the Naive Bayes Bernoulli model. However, model selection should not be based solely on accuracy. It's essential to consider other factors like its precision, recall and f1 score value.

# 4.5 Feature Selection ( preferred EMI , preferred ROI , ELA)
## EMI
### MI Regressor approach

selected_fetures_for_EMI = np.union1d(np.union1d(EMI_top['MI'].values, EMI_top['Select K'].values),
                                                 EMI_top['ExtraTreeRegressor'].values)  

selected_fetures_for_EMI  
array(['Age', 'Amount', 'ApplicationSignedHour', 'AppliedAmount',
       'BidsApi', 'BidsManual', 'BidsPortfolioManager', 'Country',
       'DebtToIncome', 'Education', 'ExpectedLoss', 'ExpectedReturn',
       'Gender', 'Interest', 'InterestAmount',
       'InterestAndPenaltyPaymentsMade', 'LanguageCode', 'LoanTenure',
       'LoanYear', 'LossGivenDefault', 'ModelVersion', 'MonthlyPayment',
       'NewCreditCustomer', 'PlannedInterestTillDate', 'PrincipalBalance',
       'PrincipalPaymentsMade', 'ProbabilityOfDefault', 'ROI', 'Rating',
       'TotalAmount', 'UseOfLoan', 'VerificationType'], dtype=object)

## ROI

selected_fetures_for_ROI = np.union1d(np.union1d(ROI_top['MI'].values, ROI_top['Select K'].values),  
                                                 ROI_top['ExtraTreeRegressor'].values)  
selected_fetures_for_ROI  
array(['Age', 'Amount', 'ApplicationSignedHour', 'AppliedAmount',
       'BidsApi', 'BidsManual', 'BidsPortfolioManager', 'Country',
       'DebtToIncome', 'EmploymentStatus', 'ExistingLiabilities',
       'ExpectedLoss', 'ExpectedReturn', 'FreeCash', 'Gender',
       'IncomeFromPrincipalEmployer', 'IncomeTotal', 'Interest',
       'LanguageCode', 'LiabilitiesTotal', 'LoanTenure', 'LoanYear',
       'LossGivenDefault', 'MaritalStatus', 'ModelVersion',
       'MonthlyPayment', 'NewCreditCustomer', 'NextPaymentNr',
       'OccupationArea', 'PreviousRepaymentsBeforeLoan',
       'PrincipalPaymentsMade', 'ProbabilityOfDefault', 'ROI',
       'TotalAmount', 'UseOfLoan', 'VerificationType'], dtype=object)  

## ELA

selected_fetures_for_ELA = np.union1d(np.union1d(ELA_top['MI'].values, ELA_top['Select K'].values),   
                                                 ELA_top['ExtraTreeRegressor'].values)  
selected_fetures_for_ELA  
array(['Age', 'Amount', 'AmountOfPreviousLoansBeforeLoan',
       'ApplicationSignedHour', 'AppliedAmount', 'BidsApi', 'BidsManual',
       'BidsPortfolioManager', 'Country', 'DebtToIncome', 'Education',
       'ExistingLiabilities', 'ExpectedLoss', 'ExpectedReturn',
       'FreeCash', 'Gender', 'HomeOwnershipType',
       'IncomeFromPrincipalEmployer', 'IncomeTotal', 'Interest',
       'InterestAmount', 'LanguageCode', 'LiabilitiesTotal', 'LoanTenure',
       'LoanYear', 'LossGivenDefault', 'ModelVersion', 'MonthlyPayment',
       'MonthlyPaymentDay', 'NewCreditCustomer',
       'NoOfPreviousLoansBeforeLoan', 'PlannedInterestTillDate',
       'PreviousRepaymentsBeforeLoan', 'PrincipalBalance',
       'PrincipalOverdueBySchedule', 'PrincipalPaymentsMade',
       'ProbabilityOfDefault', 'Restructured', 'Status', 'TotalAmount',
       'VerificationType'], dtype=object)  

relevant_features = np.union1d(np.union1d(selected_fetures_for_EMI, selected_fetures_for_ROI), selected_fetures_for_ELA)  
len(relevant_features) , relevant_features  
(49,  
 array(['Age', 'Amount', 'AmountOfPreviousLoansBeforeLoan',
        'ApplicationSignedHour', 'AppliedAmount', 'BidsApi', 'BidsManual',
        'BidsPortfolioManager', 'Country', 'DebtToIncome', 'Education',
        'EmploymentStatus', 'ExistingLiabilities', 'ExpectedLoss',
        'ExpectedReturn', 'FreeCash', 'Gender', 'HomeOwnershipType',
        'IncomeFromPrincipalEmployer', 'IncomeTotal', 'Interest',
        'InterestAmount', 'InterestAndPenaltyPaymentsMade', 'LanguageCode',
        'LiabilitiesTotal', 'LoanTenure', 'LoanYear', 'LossGivenDefault',
        'MaritalStatus', 'ModelVersion', 'MonthlyPayment',
        'MonthlyPaymentDay', 'NewCreditCustomer', 'NextPaymentNr',
        'NoOfPreviousLoansBeforeLoan', 'OccupationArea',
        'PlannedInterestTillDate', 'PreviousRepaymentsBeforeLoan',
        'PrincipalBalance', 'PrincipalOverdueBySchedule',
        'PrincipalPaymentsMade', 'ProbabilityOfDefault', 'ROI', 'Rating',
        'Restructured', 'Status', 'TotalAmount', 'UseOfLoan',
        'VerificationType'], dtype=object))   

## Standardization

scaler = StandardScaler()  
final_data[relevant_features] =scaler.fit_transform(final_data[relevant_features])    
print("_________________________________________________________________________________________")   
x = final_data    
y = regression_target_variables # target variables    

 Splitting data into train and test   
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.33, random_state=42)   
degree = 2 --> means that one new variable will be added for each input feature depending on  
 data features   
from sklearn.preprocessing import PolynomialFeatures  
poly = PolynomialFeatures(degree=2)   
x_train_poly = poly.fit_transform(x_train)   
x_test_poly = poly.fit_transform(x_test)   

# 4.7 Regression Modeling

## Linear Regression   
from sklearn.linear_model import LinearRegression   
model = LinearRegression()   
model.fit(x_train_poly, y_train)   
y_pred = model.predict(x_test_poly)    
from sklearn.metrics import mean_squared_error    
from sklearn.metrics import r2_score    
y_true = [3, -0.5, 2, 7]    
mse = mean_squared_error(y_test, y_pred)   
r2 = r2_score(y_test, y_pred)    
print("Polynomial Regression for Multiple Linear Regression :\nMean Squared Error:", mse)    
print("R-squared (R2) Score:", r2)    
print(f'Training score : {model.score(x_train_poly,y_train)} \nTest score :  
{model.score(x_test_poly, y_test)}')  
print("_________________________________________________________________________________________")   
Polynomial Regression for Multiple Linear Regression :   
Mean Squared Error: 7904807.788518265    
R-squared (R2) Score: 0.684391013781631    
Training score : 0.7770557653998381     
Test score : 0.684391013781631  

## Ridge Regression       
from sklearn.linear_model import Ridge    
ridge_model = Ridge()   
ridge_model.fit(x_train_poly, y_train)    
y_pred1 = ridge_model.predict(x_test_poly)   
mse = mean_squared_error(y_test, y_pred1)   
r2 = r2_score(y_test, y_pred1)    
print("Polynomial Regression for Multiple Linear Regression :\nMean Squared Error:", mse)   
print("R-squared (R2) Score:", r2)    
print(f'Training score : {ridge_model.score(x_train_poly,y_train)} \nTest score :  
{ridge_model.score(x_test_poly, y_test)}')   
print("_________________________________________________________________________________________")   
Polynomial Regression for Multiple Linear Regression :     
Mean Squared Error: 9009143.612434143    
R-squared (R2) Score: 0.6842464180664324    
Training score : 0.7767806390612461    
Test score : 0.6842464180664324   

# 4.8 Pipeline Creation

from sklearn.pipeline import Pipeline   
from sklearn.neighbors import KNeighborsClassifier    
x = df_3.drop('Defaultstatus', axis = 1)    
y = df_3['Defaultstatus']    
Splitting the data   
x_train,x_test,y_train,y_test = train_test_split(x,y,test_size=0.2,random_state=0)   

## Classifier Model
### 1. Knn pipeline
Creating the pipeline   
knn_pipeline = Pipeline( [ ('Standard Scaling', StandardScaler()) , ('PCA' , PCA(n_components = 4) ), ('KNN Classifier',KNeighborsClassifier() ) ])   
Fitting the pipeline on the training data  
knn_pipeline.fit(x_train, y_train)   
Pipelining predictions   
y_pred = knn_pipeline.predict(x_test)   
Calculating the pipeline accuracy   
print('Test accuracy = ', round(accuracy_score(y_test, y_pred)*100, 2), '%')   
print(classification_report(y_test,y_pred))   
Test accuracy =  94.06 %  

### XGB classification model   
Creating the pipeline     
from xgboost import XGBClassifier       
xgb_pipeline =  Pipeline( [ ('Standard Scaling', StandardScaler()) , ('PCA' , PCA(n_components = 4) ) ,('XGB Classifier' , XGBClassifier() ) ])       
 Fitting the pipeline on the training data      
xgb_pipeline.fit(x_train, y_train)        
 Pipelining predictions       
y_pred = xgb_pipeline.predict(x_test)       
Calculating the pipeline accuracy         
print('Test accuracy = ', round(accuracy_score(y_test, y_pred)*100, 2), '%')       
print(classification_report(y_test,y_pred))      
Test accuracy =  93.84 %    

## Regression Model:    
## XGB Regression Pipeline   
regression_pipelines_data = final_data.copy()   
x_reg = regression_pipelines_data   
y_reg = regression_target_variables   
reg_x_train, reg_x_test, reg_y_train, reg_y_test = train_test_split(x_reg, y_reg,  
test_size=0.2, random_state=35)   
Creating the pipeline   
from xgboost import XGBRegressor   
xgb_reg_pipeline = Pipeline( [ ('Standard Scaling', StandardScaler()) , ('XGB Regression' , XGBRegressor() ) ] )   
Fitting the pipeline on the training data    
xgb_reg_pipeline.fit(reg_x_train, reg_y_train)   
Pipelining predictions   
y_pred = xgb_reg_pipeline.predict(reg_x_test)   
Calculating the pipeline scores   
mse = mean_squared_error(reg_y_test, y_pred)   
r2 = r2_score(reg_y_test, y_pred)   
print("Polynomial Regression for XGB regression pipeline :\nMean Squared Error:", mse)   
print ( "R-squared (R2) Score:", r2 )   
print('Test accuracy : ', xgb_reg_pipeline.score(reg_x_test , reg_y_test))   
Polynomial Regression for XGB regression pipeline :   
Mean Squared Error: 7002565.603516835   
R-squared (R2) Score: 0.7350848140005289   
Test accuracy :  0.7350848140005289   

## Lasso Regression pipeline

Creating the pipeline   
from sklearn.linear_model import MultiTaskLasso    
lasso_pipeline = Pipeline( [ ('Standard Scaling', StandardScaler()) , ('polynomial', PolynomialFeatures(degree=2) ) ,('Lasso Regressor' , MultiTaskLasso(alpha=1e-05) ) ] )   
Fitting the pipeline on the training data   
lasso_pipeline.fit(reg_x_train, reg_y_train)   
Pipelining predictions   
y_pred = lasso_pipeline.predict(reg_x_test)   
 Calculating the pipeline scores   
mse = mean_squared_error(reg_y_test, y_pred)   
r2 = r2_score(reg_y_test, y_pred)   
print("Polynomial Regression for Lasso regression pipeline :\nMean Squared Error:", mse)    
print ( "R-squared (R2) Score:", r2 )   
print('Test accuracy : ', lasso_pipeline.score(reg_x_test , reg_y_test))    
Polynomial Regression for Lasso regression pipeline :    
Mean Squared Error: 9833976.515810799    
R-squared (R2) Score: 0.7399686386998136   
Test accuracy :  0.7399686386998136  

## Decision Tree Regression pipeline

Creating the pipeline   
from sklearn.tree import DecisionTreeRegressor   
dt_reg_pipeline = Pipeline( [ ('Standard Scaling', StandardScaler()) , ('Decision Tree Regression' ,DecisionTreeRegressor())])   
Fitting the pipeline on the training data   
dt_reg_pipeline.fit(reg_x_train, reg_y_train)   
Pipelining predictions   
y_pred = dt_reg_pipeline.predict(reg_x_test)   
Calculating the pipeline scores   
mse = mean_squared_error(reg_y_test, y_pred)   
r2 = r2_score(reg_y_test, y_pred)   
print("Polynomial Regression for Decision Tree regression pipeline :\nMean Squared Error:", mse)   
print ( "R-squared (R2) Score:", r2 )  
print('Test accuracy : ', dt_reg_pipeline.score(reg_x_test , reg_y_test))   

Polynomial Regression for Decision Tree regression pipeline :   
Mean Squared Error: 21412926.383504998   
R-squared (R2) Score: 0.24461518489194578   
Test accuracy :  0.24461518489194578  

## Ridge Regression pipeline

Creating the pipeline    
ridge_pipeline = Pipeline( [ ('Standard Scaling', StandardScaler()) , ('polynomial', PolynomialFeatures(degree=2) ) , ('Ridge Regression' , Ridge() ) ] )   
Fitting the pipeline on the training data    
ridge_pipeline.fit(reg_x_train, reg_y_train)   
Pipelining predictions  
y_pred = ridge_pipeline.predict(reg_x_test)   
Calculating the pipeline scores   
mse = mean_squared_error(reg_y_test, y_pred)   
r2 = r2_score(reg_y_test, y_pred)   
print("Polynomial Regression for Ridge regression pipeline :\nMean Squared Error:", mse)   
print ( "R-squared (R2) Score:", r2 )    
print('Test accuracy : ', ridge_pipeline.score(reg_x_test , reg_y_test))   
pipe = Pipeline(steps=[ ('Standard Scalling' , StandardScaler() ) , ('polynomial', PolynomialFeatures(degree=2) ) ,('ridge' , Ridge() ) ]  )   
param_grid = { 'ridge__alpha': np.logspace(0, 4, 5)}    
search = GridSearchCV(pipe, param_grid, cv=5 ,return_train_score=False)    
search.fit(reg_x_train, reg_y_train)   
print("Best parameter (CV score=%0.3f):" % search.best_score_)    
print(search.best_params_)   
Polynomial Regression for Ridge regression pipeline :   
Mean Squared Error: 7834331.876826879    
R-squared (R2) Score: 0.7403341423694877  
Test accuracy :  0.7403341423694877  
Best parameter (CV score=0.722):  
{'ridge__alpha': 10000.0}  

## Multiple Linear Regression

Creating the pipeline   
from sklearn.linear_model import LinearRegression    
ml_reg_pipeline = Pipeline( [ ('Standard Scaling', StandardScaler()) , ('Multi Linear Regression' , LinearRegression() ) ] )   
Fitting the pipeline on the training data   
ml_reg_pipeline.fit(reg_x_train, reg_y_train)   
Pipelining predictions   
y_pred = ml_reg_pipeline.predict(reg_x_test)  
Calculating the pipeline scores   
mse = mean_squared_error(reg_y_test, y_pred)   
r2 = r2_score(reg_y_test, y_pred)   
print("Mean Squared Error:", mse)   
print ( "R-squared (R2) Score:", r2 )   
print('Test accuracy : ', ml_reg_pipeline.score(reg_x_test , reg_y_test))   
Mean Squared Error: 130846949.71801478   
R-squared (R2) Score: 0.7221879193146132  
Test accuracy :  0.7221879193146132  

•	The accuracy of linear regression and KNN classifier is good so we can use for future use.  
•	The output is 2 pickle files for the 2 pipelines to be used in UL.  


# 4.9 UI App creation
-Using Flask, HTML5, and CSS; we created a web application.  
1)app.py --> for Flask to run the app and preprocess the input data from the web forum and make it match the attributes expected by the pipeline file and furthermore run the pipeline files.
2)index.html --> Individual borrower entry using a web forum.  

-UI
To facilitate user interaction with the model, we designed a simple and user-friendly front-end interface using HTML and CSS. This interface allow investors to input borrower data and receive predictions based on the model's analysis.

# 5.DEPLOYMENT

After combining and saving our pipelines, we provided detailed steps and code for deploying the model. This included creating a Flask application, and deploying the model on our local system. This allowed investors to access the model and make predictions using the data they input and the model running at the background.

![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/cd4dc3d1-17c0-4ee4-aa53-e0c33f8c8260)


![image](https://github.com/Technocolabs100/P2P-Bondora-Financial-risk-modelling-of-European-lending-platform/assets/129476049/c3944a42-c618-45df-8903-74e09ab95ce7)

# 6.ACKNOWLEDGEMENT

We would like to thank the following resources and libraries for their invaluable contribution to this project:  

Scikit-learn   
Target creation report by Nour Ibrahim  
Flask  
Multiple Output Regression by Krish Naik  
Pipeline Creation by CampusX  

# 7. CONTACT
If you have any questions or suggestions regarding this project, feel free to reach out to us:
1. Vijaya Sanjarao pawar
pawarvijaya666@gmail.com
2. Nithin s
nithinsatheesh2@gmail.com
3. Aman Deep Gupta
amandeepgupta154@gmail.com
4. Vivek
vt57299@gmail.com
5. Ankita Arjunrao Mane
ankitamane108@gmail.com
6. Navika M S
navika.ms716@gmail.com
7. Maruf Abduzohirov 
marufabduzohirov44@gmail.com
8. Abhishek Jog
jogabhishek184@gmail.com
9. Shubham Dhadage
shubhamcd205@gmail.com
10. Fahad Sarfraz
fahadsarfraz81@gmail.com
11. Nagendra Prasad R
prasadrnag@gmail.com
