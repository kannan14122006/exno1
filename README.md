# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import numpy as np
import pandas as pd
data=pd.read_csv("SAMPLEIDS.csv")
data
```
#output
<img width="1471" height="851" alt="Screenshot 2025-09-17 153655" src="https://github.com/user-attachments/assets/94dad474-99b9-48ae-8c71-e61566a30d2c" />

#code
```
data.head(4)
```
#output
<img width="1402" height="333" alt="Screenshot 2025-09-17 155422" src="https://github.com/user-attachments/assets/8984547b-1413-4f2c-8108-ae82033a5336" />
#code
```
data.tail(7 )
```
#output
<img width="1371" height="569" alt="Screenshot 2025-09-17 155444" src="https://github.com/user-attachments/assets/26291d87-0985-46df-8786-90307c5ce495" />

#code
```
data.isnull()
```
#output
<img width="1384" height="559" alt="Screenshot 2025-09-17 155459" src="https://github.com/user-attachments/assets/c4012262-7061-48cc-9f0e-f9c475f6fd41" />

#code
```
data.isnull().sum()
```
#output
<img width="1463" height="501" alt="Screenshot 2025-09-17 155510" src="https://github.com/user-attachments/assets/1bee5be9-e642-45a1-ac02-4d5245f7fef0" />

#code
```
data.isnull().any()
```
#output
<img width="1449" height="500" alt="Screenshot 2025-09-17 155522" src="https://github.com/user-attachments/assets/642bd529-878f-47fc-b8df-ff6b21f37bdc" />

#code
```
data.dropna(axis=1)
```
#output
<img width="754" height="554" alt="Screenshot 2025-09-17 155533" src="https://github.com/user-attachments/assets/528bf784-6a2d-46f0-a714-c492392cce10" />

#code
```
data.fillna(method="ffill")
```
#output
<img width="1458" height="793" alt="Screenshot 2025-09-17 155549" src="https://github.com/user-attachments/assets/c5293e67-948a-4b98-9970-8bda4702607c" />

#code
```
data.fillna({'RENGO':0, 'NAME':'KANNAN'})
```
#output
<img width="1188" height="744" alt="Screenshot 2025-09-17 155659" src="https://github.com/user-attachments/assets/9a8a960a-994a-41f9-b0d2-9a42870f1621" />

#code
```
ir=pd.read_csv("iris.csv")
ir
```
#output
<img width="1021" height="672" alt="Screenshot 2025-09-17 155716" src="https://github.com/user-attachments/assets/436c3965-7a69-479b-aba2-66b2dbf8722d" />

#code
```
ir.describe()
```
#output
<img width="755" height="436" alt="Screenshot 2025-09-17 155725" src="https://github.com/user-attachments/assets/aba5d22e-60b3-450e-bccf-82d46d0fc23b" />

#code
```
import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)
```
#output
<img width="836" height="657" alt="Screenshot 2025-09-17 155732" src="https://github.com/user-attachments/assets/b578bd6a-e5f4-42c2-ab17-a1749dd61fbf" />

#code
```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)

```

#output
<img width="505" height="160" alt="Screenshot 2025-09-17 155741" src="https://github.com/user-attachments/assets/df60f447-3d8d-4dbd-8c30-64e34b17819a" />

#code
```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
#output
<img width="839" height="324" alt="Screenshot 2025-09-17 155747" src="https://github.com/user-attachments/assets/3c1b8b33-f21d-410e-9b54-287a8dd731b7" />

#code
```
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid
```
#output
<img width="856" height="576" alt="Screenshot 2025-09-17 155754" src="https://github.com/user-attachments/assets/0b7713c7-2a07-4f63-81cb-026e1b27f1ed" />

#code
```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
```

#output
<img width="865" height="634" alt="Screenshot 2025-09-17 155803" src="https://github.com/user-attachments/assets/69407a6b-b97d-40b2-abd6-564a17737cf3" />

#code
```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir.sepal_width))
z
```
#output
<img width="849" height="795" alt="Screenshot 2025-09-17 155812" src="https://github.com/user-attachments/assets/f86ddbca-2526-45ee-baa1-ada66621d0d7" />
      <<include your coding and its corressponding output screen shots here>>
# Result
        Thus the programs are executed successfully.
