# Precise marketing prediction based on big data user portrait analysis

### Name: Anyi Liu 
### Student ID: 1801212888


## Background

### 1. Introduction to User Portrait Analysis

User portrait is user information labeling. User information includes user's basic information, social attribute information, demographic information, and behavior information on the APP. According to the user's real data, by building a user model, the user's various attributes and characteristics are abstracted into individual labels for other upstream systems to use. The original user portrait contains not only tags but also weights.

Without user portraits, daily operation activities, advertising, product function optimization, etc. are either carried out in full or estimated based on experience. Users in need may not receive pushes, and users who are not in need may be interrupted for no reason. At the same time as damage, costs are also wasted, and the lack of user portraits will make it impossible to evaluate the effects in detail. With user portraits, these daily tasks will be more effective.

### 2. Feasibility

The huge amount of data generated by users' daily consuming can be used to discover the users' consuming pattern. Based on these patterns, the label on each consumers could be more and more precise.

A specific case is used in Huawei Marketing Group. They use the consumers' historical purchasing data which has 50 million instances including around 300 features to generate the user portrait. Then they can target customers with precise marketing advertising for new products.

## Data

### 3. Data Format

The data are well structured. Every instance has only one main key which is the order ID. There are several important information in the following columns like user's ID, product type, payment amount and so on. Also, there are some columns recording timestamp and more detailed information about user and product. 

Features can be divided into three types:

- User's information
- Product's information
- Transaction's information

The data should be formed as follows:

| Order_ID  | User_Information_1     |  User_Information_2     | ...  | Product_Information_1      | ...| Transaction_Information_1 | ...| Transaction_Information_N |
| :----------------: |:-------------:| :------------:| :---:| :------------:| :---: | :---: | :---:| :---:|
| 00002                  | X<sub>1</sub> | X<sub>2</sub> | ...  | A<sub>1</sub> | ... | C<sub>1</sub> | ... | C<sub>N</sub> |
| 00001                  | Y<sub>1</sub> | Y<sub>2</sub> | ...  | B<sub>1</sub> | ... | D<sub>1</sub> | ... | D<sub>N</sub> |

### 4. Big Data Properties

- `Volume`: The user's order data system stores billions of data. For Huawei's case, there are at least 50 million instances and over 300 features.
- `Velocity`: Transaction happens every seconds. Once transaction happens, one new instance is generated and stored in the user's system.
- `Variety`: The feature are divided into three main types, and the detailed information could be much different from each other. 

### 5. Database Selection

Hadoop / MapReduce is the most efficient database. There are two reasons:

- First, Hadoop can provide an efficient way to store, transport and calculate huge amount of data.
- Second, Hadoop has the Hive application. SQL can be directly used in Hive. For this case, because the data are well structured, using SQL is the most efficient way to do analysis.

## Workflow

### 6. Methodology

The whole data are stored in HDFS, so there are two methods to get access to them.

- `Local Access`: Use Hadoop to download the sample data and then use local machine to analysis the sampled data. For the data are not so large, we can use Python or Matlab to do data analysis. Although this method might be quicker and more convenient, the accuracy of user portrait might be weaker.
- `Online Access`: Directly use Hive application to handle the whole data. The process is more complex because not only SQL is used but also Yarn is used to manage the computing resources. The data are not local and might consume a huge amount of computing power. This method requires advanced hardware on server.
