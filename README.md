# Ex-02_DS_Outlier

# AIM:
To detect and remove the outliers in the given data set and save the final data.

# EXPLANATION:
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.

# ALGORITHM:
# Step 1
Import the required packages(pandas,numpy,scipy)
# Step 2
Read the given csv file
# Step 3
Convert the file into a dataframe and get information of the data.
# Step 4
Remove the non numerical data columns using drop() method.
# Step 5
Detect the outliers in the data set using z scores method.
# Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
# Step 7
Check if the outliersare removed from data set using graphical methods.
# Step 8
Save the final data set into the file.

# PROGRAM:
```
Developed by: Mitta.Yashaswi
Register number:212221230062

import pandas as pd
df=pd.read_csv('weight.csv')
df

#removing non numerical columns
df=df.drop("Gender",axis=1)
print('After removing Non numeric columns:')
df

#graph to display outliers
df.boxplot()

#calculating z scores to detect outliers
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
print(z)

#removing outliers from weight
df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1

#checking if outliers are removed through graph
df1.boxplot()

#removing outliers from height
df2=df.copy()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
IQR=q3-q1
df_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
df_new

#checking if outliers are removed through graph
df_new.boxplot()

#final dataset
df_new

#saving data file
df.to_csv('weight.csv', index=False)
```

# OUTPUT:
# Initial data set
![image](https://user-images.githubusercontent.com/94619247/161670517-e8619bee-6a25-4888-afad-88538e7f9dd7.png)


# Data set after removing non numerical sets
![image](https://user-images.githubusercontent.com/94619247/161670550-b1dbe0c8-46e8-4e69-8416-ac3f756940ad.png)


# Graph displaying initial dataset with outliers
![image](https://user-images.githubusercontent.com/94619247/161670585-83cca9ee-6b6e-41f3-a66f-7d43ce68cc4b.png)


# Z scores to detect outliers
![image](https://user-images.githubusercontent.com/94619247/161670619-1ced307e-4248-4713-8f9f-e4c1f26c6adb.png)


# Data set after removing outliers in weight using z scores and list manipulation
![image](https://user-images.githubusercontent.com/94619247/161670650-36e16b76-3aec-4c7b-b195-b2e3dd4b1da4.png)


# Graph after removing outliers in weight
![image](https://user-images.githubusercontent.com/94619247/161670681-4ec8a5b8-68a8-4a61-a28d-71a5cc68039b.png)


# Data set after removing outliers in height using Interquartile Range(IQR)
![image](https://user-images.githubusercontent.com/94619247/161670708-9e09b814-3a86-4ef5-b625-933ec0d58a67.png)


# Final graph after removing all outliers
![image](https://user-images.githubusercontent.com/94619247/161670731-e8a11d03-ef77-46d9-bfc5-bf77b62b14fe.png)


# Final data set
![image](https://user-images.githubusercontent.com/94619247/161670811-36020489-9e0a-4bf0-b2a1-83ae19022eb7.png)


# RESULT:
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
