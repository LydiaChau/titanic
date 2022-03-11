# titanic

##### import library
import pandas as pd\
import matplotlib.pyplot as plt\
import seaborn as sns\
%matplotlib inline

##### read csv file
df = pd.read_csv("titanic.csv")

##### print top 5 rows
df.head()

##### print variable names
print(df.columns)

## Class
##### Count value of each class
df["Pclass"].value_counts()

##### Bar chart of each class count
sns.set(style="darkgrid")
ax = sns.countplot(x="Pclass", data=df)

##### Survival rate of each class
table = pd.pivot_table(df,index=["Pclass"],values=["Survived"],aggfunc="mean")\
table

##### Survival rate of each class - bar chart
df[(df["Survived"] == 1)].pivot_table(index="Pclass", values="Survived", aggfunc='count')
'''bar chart of survival rate of each class'''
Pclass = ["Class 1", "Class 2", "Class 3"]
Survival_rate = [0.63, 0.47, 0.24]
#plt.figure(figsize=(10,5))
plt.bar(Pclass, Survival_rate, color = "green")
plt.title("Survival rate of each class")
plt.xlabel("Pclass")
plt.ylabel("Survival_rate")
plt.show()

## Sex
##### count no. of passenger of each sex
df["Sex"].value_counts()
##### count no. of survivor of each sex
df[(df["Survived"] == 1)].pivot_table(index="Sex", values="Survived", aggfunc='count')
##### survival rate of each sex
table = pd.pivot_table(df,index=["Sex"],values=["Survived"],aggfunc="mean")
table
##### survival rate of each sex - bar chart
Pclass = ["Female", "Male"]
Survival_rate = [0.74, 0.19]
plt.bar(Pclass, Survival_rate, color = "blue")
plt.title("Survival rate of each sex")
plt.xlabel("Sex")
plt.ylabel("Survival_rate")
plt.show()

## Age
##### Average age of the survived/ not survived
table = pd.pivot_table(df,index=["Survived"],values=["Age"],aggfunc="mean")\
table
##### Average age of the survived/ not survived - barchart
Survived = ["0=Not Survived", "1=Survived"]
Mean_age = [30.63, 28.34]
#plt.figure(figsize=(10,5))
plt.bar(Survived, Mean_age, color = "red")
plt.title("Average age of the survived")
plt.xlabel("Survived")
plt.ylabel("Mean_age")
plt.show()

## Conclusion
##### survival rate in respective to the sex and class
table = pd.pivot_table(df,index=["Sex","Pclass"],values=["Age", "Survived"],aggfunc="mean")\
table
##### survival rate in respective to the sex and class - barchart
sns.catplot(x="Sex", y="Survived", hue="Pclass", kind="bar", data=df)
