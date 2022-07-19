
# Cars DATA Analysis

This is a certain analysis on the types of cars that are there in the diferent coutries.
In which we will be doing certain Data Visualizations.

## DATASET
The Dataset comprises of the different
columns with unique values.
Some of them are:-
1. Make
2. Model
3. Origin Country
4. Engine type
5. Miles per Gallon, etc..

## Data Analysis Tools

### 1. Simple Imputer(For Null Values)
The Dataset contained certain 
*Missing Values* in it, for which I used the most
common Data Preprocessing tool of Machine 
Learning library that is Simple Imputer, and 
replaced the missing values with the 'Most Frequent Values'

![SI](https://user-images.githubusercontent.com/109500969/179671707-703f2183-92a1-4103-b0cf-3927173d146d.png)


### 2. Classifying
After that the 'Origin' column was sorted 
according to the required countries, where we 
have selected Asia and Europe for our Analysis.

### 3. Sorting
Now as per our requirements, we have to analyse
the data for Light Motor Vehicles only, for which
the cars that weighs more than 4000 kgs where
removed from the dataset.

### 4. Combining two columns as one
As per our dataset we have observed that the 
fuel consumption for the city and highway are 
given seperately, for which we have taken the average 
for both and stored the same into a new column.
## Data Visualization
All those columns which are termed to be as 
unwanted are removed before graphical representation,
 After that the countplot command from the 
seaborn library is used for determining the
frequency distribution barplot.

### Example:

![Count](https://user-images.githubusercontent.com/109500969/179671704-813f599c-3608-4cd2-9528-d0e2f4bd2b84.png)


## Deployment

To deploy this project run

```bash
# Cars Data Analysis

## Importing the dataset and Libraries

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

cars = pd.read_csv("/content/Cars Data.csv")

## Find the Rows and colummn for the DATAFRAME

cars.shape

## Handling the null Values of the Dataframe

cars.isnull().sum()

from sklearn.impute import SimpleImputer
imputer = SimpleImputer(missing_values = np.nan , strategy ='most_frequent')
cars['Cylinders'] = imputer.fit_transform(cars['Cylinders'].values.reshape(-1,1))

cars.isnull().sum()

# Some Exploratory Data Analysis

## Classifing the Origin columns as per required condition

w = cars['Origin'].isin(['Asia', 'Europe'])
cars[w].head(5)

## Remove the values where weight is more than 4000

cars[~(cars['Weight'] > 4000)].head(5)                                    

## Add the value of 3 in the complete column in order to standardize it.

cars['MPG_City'] = cars['MPG_City'].apply(lambda x:x+3)
cars.head(5)

## Now Miles per Gallon (MPG) to be combined and transformed to one column as average of both the two values MPG_city and MPG_Highway

cars.insert(10, 'MPG', value= round((cars['MPG_City']+ cars['MPG_Highway'])/2))
cars.drop(columns=['MPG_City', 'MPG_Highway', 'Length', 'Weight', 'Wheelbase', 'Invoice'], inplace=True)

cars.head(2)

## Some graphical Analysis of dataframe

cars['DriveTrain'].value_counts()

sns.countplot(cars['DriveTrain'])

cars['Origin'].value_counts()

sns.countplot(cars['Origin'])

cars['Type'].value_counts()

sns.countplot(cars['Type'])
```


# Hi, I'm Avichal Srivastava! 👋
You can reach out to me at: 
srivastavaavichal007@gmail.com
LinkedIn: www.linkedin.com/in/avichal-srivastava-186865187

## 🚀 About Me
I'm a Mechanical Engineer by education, and love to work with data, eventually started my coding journey for one of my Drone project, where I realized that it is something which makes me feel happy in doing.

Hope! You liked it, and it is just a beginning, many more to come, till then Happy Analysing!!

