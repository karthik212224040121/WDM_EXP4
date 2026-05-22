### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 22/05/2026
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program 1:
```
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt

df=pd.read_csv('/content/clustervisitor.csv')

cluster={'Young':(df['Age']<=30),'Middle':((df['Age'])>30 & (df['Age']<=50)),'Old':(df['Age']>50)}
count=[]
for group,condition in cluster.items():
  visitors=df[condition]
  count.append(len(visitors))
  print(f"The Visitors on {group} are")
  print(visitors)
  print("count =",len(visitors))


```
### Output:
<img width="960" height="930" alt="image" src="https://github.com/user-attachments/assets/8a10c136-d032-4149-9759-5dac2456d668" />

### Visualization:
```
plt.figure(figsize=(8, 6))
plt.bar(['Young','Middle','Old'], count, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:
<img width="1052" height="580" alt="image" src="https://github.com/user-attachments/assets/d3578674-eaff-46c2-984a-2b0c4fb29eed" />

### Program 2:
```
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt

df=pd.read_csv('/content/clustervisitor.csv')

cluster={'Young':(df['Age']<=30),'Middle':((df['Age'])>30 & (df['Age']<=50)),'Old':(df['Age']>50)}

df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
K=KMeans(n_clusters=4,random_state=23)
df3['cluster']=K.fit_predict(newdf)
df3

```
### Output:
<img width="764" height="919" alt="image" src="https://github.com/user-attachments/assets/5b2fc2ea-026c-4b7f-9789-570416b7db9d" />

### Visualization:
```
plt.figure(figsize=(8,6))
plt.scatter(x=df3['Age'],y=df3['Income'],c= df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title('Kmeans Cluster')
plt.show()
```
### Output:
<img width="1034" height="634" alt="Screenshot 2026-05-22 111754" src="https://github.com/user-attachments/assets/4b4dd153-61bd-4354-97d2-60d6df58faee" />

### Result:
Cluster and Visitor Segmentation is used to group website visitors based on navigation patterns and age groups to better understand user behavior and improve services.
