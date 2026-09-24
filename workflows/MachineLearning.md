# ** I/ Data**:
## **1/ Load Data & EDA (Khám phá dữ liệu)**
- libraries: pandas, matplotlib, seaborn
- commonly used functions:
```
read data: df = pd.read_csv('data.csv')

overview: df.head(), df.info(), df.describe()

missing values: df.isnull().sum()
```
## **2/ Data Preprocessing & Cleaning**
- libraries: sklearn.preprocessing, sklearn.impute
- common used functions:
```
missing values: SimpleImputer(strategy='mean')

encode categorical data into numerical formats: LabelEncoder(), OneHotEncoder()

normalize/standardize data scales (crucial for models like SVM, KNN, or Neural Networks): StandardScaler() or MinMaxScaler()
```
