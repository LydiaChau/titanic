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

[titanic.csv](https://github.com/LydiaChau/titanic/files/8229637/titanic.csv)

## Results
This report is about analysis of Titanic dataset.  There are 891 observations, with 12 variables in the dataset.   We will analyze whether the class, gender and age are associated with the survival rate.

##### Pclass VS Survival rate
The number of passengers in Class 1, Class 2 and Class 3 is 216, 184 and 491 respectively.  The survival rate of Class 1, Class 2 and Class 3 is 0.63, 0.47 and 0.24 respectively.

![image](https://user-images.githubusercontent.com/97926477/157814626-02abdb9f-4198-4e56-9c58-1c3704847804.png)

From the statistics showed, Class 1 has higher survival rate than Class 2 and Class 3.  In Titanic, Class 1 is the upper class, Class 2 is middle class and Class 3 is low class.

##### Sex VS Survival rate
There are 314 females and 577 males.  The survival rate of female and male is 0.74 and 0.19 respectively.  It shows that female has a higher survival rate than male.

![image](https://user-images.githubusercontent.com/97926477/157815950-b5a83c1e-c972-4d6b-846f-92bc29d0b065.png)

##### Age VS Survival rate
The average age of survived and not survived is 30.63 and 28.34 respecitvely.  Based on the age information we cannot conclude the age has large association with the survival rate.

![image](https://user-images.githubusercontent.com/97926477/157816103-b21f4478-3915-4438-ba86-e7441736a151.png)

[Titanic.docx](https://github.com/LydiaChau/titanic/files/8229694/Titanic.docx)
