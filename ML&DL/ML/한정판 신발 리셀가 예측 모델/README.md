# Sneaker Resell Price Prediction Model (2022.01.07~12) 
Revised in November 2023
# Project Outline 

#### 1. Introduction 
 - 1.1. Problem Statement
 - 1.2. Description of the dataset 

#### 2. Steps 
- 2.1. EDA and Data Analysis 
- 2.2. Modeling & Selection   
- 2.3. Feature Importance 
- 2.4. Interpreting Coefficients (PDP Plot) 


#### 3. Reflection and Next Steps 

# 1. Introduction 
### 1.1. Problem Statement 
- Objective: To analyze the shoe resale market, which has been growing since the second half of 2010, and to predict resale prices using various features. 
- Chose this topic because it's a domain I've always been interested in ever since I was a kid, and I wanted to see if I could use real data to predict the resale prices of sneakers 

### 1.2. Description of the dataset  
- A total of 100,000 Real StockX transactions (2017.09 - 2019.04)
- A total of 53 shoes (consisting of limited edition shoes such as Adidas Yeezy and Nike Off-White)

![StockX Data](https://user-images.githubusercontent.com/90128775/184078928-c0470835-e453-448e-b325-7afa42aeeb9d.png)

# 2. Steps
### 2.1. EDA and Data Analysis 
- Overview of My Data Processing Pipeline
- In my project, I worked with a dataset of sneaker sales, focusing on enhancing the data to make it suitable for advanced analysis and machine learning. Below is an overview of the steps I took to preprocess and transform the data:

- Data Loading: I started by loading the sneaker sales data from a CSV file into a pandas DataFrame.
- Date Preprocessing: The dataset included date fields ('Order Date' and 'Release Date'), which I converted into a more standardized format (MM-DD-YYYY).
- Feature Engineering – Color and Sneaker Type: I added new features to the dataset based on the names of the sneakers. For instance, if a sneaker name contained a color like 'Black' or 'White', I created a corresponding feature (column) for it. Similarly, I identified different sneaker types (like 'Yeezy-Boost-350', 'Air-Jordan') from the sneaker names and created binary features for these as well.
- Region-Based Features: Recognizing the importance of geographical influence on sneaker sales, I created features based on the buyer's region, like 'California', 'New York', etc.
- Normalizing Shoe Size Data: I normalized the shoe sizes to understand their distribution in the dataset better. This helps in analyzing the popularity or rarity of certain shoe sizes.
- Converting Price Fields: The 'Sale Price' and 'Retail Price' fields were formatted as strings with currency symbols. I converted them into numerical values for analysis purposes.
- Additional Feature Computation: I computed a 'Colorful' feature, indicating the number of colors mentioned in each sneaker's name. I also calculated the 'Number of Sales' per order date to understand sales volume trends.
Cleaning the Data:
- Finally, I removed unnecessary columns like 'Brand' and 'Buyer Region', which were either redundant or not required for my analysis.

#### Q. Is there a premium on the price of shoes over time? 

<img width="778" alt="스크린샷 2022-07-21 오전 12 51 17" src="https://user-images.githubusercontent.com/90128775/180027876-3aa4f8e6-03b8-4135-8b16-79101c514fe1.png">

- December 2018 on the left, all data on the right 
 - Observe that the Floor price of resell premiums has been rising over time

#### Q. Does shoe size affect resale value?

<img width="413" alt="스크린샷 2022-07-21 오전 12 56 23" src="https://user-images.githubusercontent.com/90128775/180028084-83eed031-0aca-4f1d-a93a-9a0209ce9352.png">

- Confirming that shoe size has little to do with resale value

### 2.2. Modeling & Selection 

![스크린샷 2023-11-12 오후 11 58 40](https://github.com/hyunstar11/Portfolio/assets/90128775/b74de6d6-297d-4114-8a1f-671854fa879e)

- Results from the baseline model provided limited insights into the underlying data structure. The metrics suggested that the baseline model's predictive performance is poor, potentially no better than a model that would make random predictions or simply predict the average outcome without any input features.
- Given the possible limitations of simpler models, a progression to more complex models such as Linear Regression, Random Forest, XGBoost, LightGBM, and an Ensemble Model was considered. These models are known for their ability to handle complex datasets with sophisticated feature interactions.
- To mitigate the risk of overfitting, various feature selection methods were employed. A careful comparison between the MAE and cross-validation MAE (MAE CV) for each model was conducted, ensuring that the models not only fit the training data well but also generalize effectively to new data.
- Among the models tested, the Ensemble Model demonstrated superior performance. It achieved a lower MAE in cross-validation (20.25 for MAE CV compared to 31.90 for the Ensemble's standard MAE), which indicates that the model has strong generalization capabilities across different data subsets, an essential quality for robust predictive modeling.

### 2.3. Feature Importance 

[needs update] 

### 2.4. Interpreting Coefficients (PDP Plot)

[needs update] 

# 3. 회고 및 향후 발전방향  


__________________________________________________________________________________________________________________
Korean Version 
Originally Written in 2022 
#### 1. 서론
 - 1.1. 문제
 - 1.2. 데이터셋에 대한 설명 

#### 2. 프로젝트 진행 과정 
- 2.1. EDA 및 데이터 분석 
- 2.2. Modeling & Selection   
- 2.3. Feature Importance 
- 2.4. Interpreting Coefficients (PDP Plot) 
- 2.5. Prediction 

#### 3. 회고 및 향후 발전방향  

# 1. 서론 
### 1.1. 문제
- 목적: 2010년 후반기에 들어서 계속 커져가고 있는 신발 리셀 마켓을 분석하고 다양한 피쳐들을 통해 리셀가를 예측하기 위함 
- 평소에 관심 있어하는 도메인기도 해서 본 주제로 선정 

### 1.2. 데이터셋에 대한 설명 
- 총 10만개의 StockX 신 거래 데이터 (2017.09 ~ 2019.04)
- 총 53가지의 신발 (아디다스 이지, 나이키 오프화이트 등 한정판 신발들로 구성) 

![StockX Data](https://user-images.githubusercontent.com/90128775/184078928-c0470835-e453-448e-b325-7afa42aeeb9d.png)

# 2. 프로젝트 진행 과정 
### 2.1. EDA 및 데이터 분석 
- 결측치 확인 후 제거 
- Feature Engineering 
  - Sneaker Name: 기존의 53개에서 10개로 축소 (비슷한 신발들끼리 묶기) 
  - Color, Days_Since_Release (발매 후 기간), Buyer Region, Number of Sales 컬럼들 추가 
- 학습 시킬 데이터 선정 
  - 가장 신발이 많이 거래된 달을 기준으로 train (2018년 12월, 12,000개의 거래 데이터)  

#### Q. 시간이 지날수록 신발 가격에 프리미엄이 붙는가? 

<img width="778" alt="스크린샷 2022-07-21 오전 12 51 17" src="https://user-images.githubusercontent.com/90128775/180027876-3aa4f8e6-03b8-4135-8b16-79101c514fe1.png">

- 좌측은 2018년 12월, 우측은 전체 데이터 
 - 시간이 지날수록 리셀 프리미엄의 '바닥'/Floor Price는 오르는 추세라는 걸 확인 

#### Q. 신발 사이즈가 리셀가에 영향을 미치는가? 

<img width="413" alt="스크린샷 2022-07-21 오전 12 56 23" src="https://user-images.githubusercontent.com/90128775/180028084-83eed031-0aca-4f1d-a93a-9a0209ce9352.png">

- 신발 사이즈는 리셀가와 큰 상관이 없다라는 걸 확인 

### 2.2. Modeling & Selection 
- 리셀가를 예측하는 문제이기 때문에 Regression 문제로 접근 
- Linear Regression, Random Forest, XGBoost 세 가지 모델을 고려 

<img width="755" alt="스크린샷 2022-07-21 오전 12 59 30" src="https://user-images.githubusercontent.com/90128775/180028799-c5ebb709-1bc4-45c7-a746-28c6f95325e8.png">

- Linear Regression 모델이 가장 좋은 성능을 보였으며, Lasso Regresssion 모델과 비교 진행 
  - 미세하게나마 성능이 더 좋다는 걸 확인 
  
<img width="722" alt="스크린샷 2022-07-21 오전 1 00 47" src="https://user-images.githubusercontent.com/90128775/180029125-dfe4bba5-b61d-4d57-a304-c8a11893244e.png">

### 2.3. Feature Importance 

<img width="780" alt="스크린샷 2022-07-21 오전 1 01 01" src="https://user-images.githubusercontent.com/90128775/180029205-b32b781c-1160-494d-be1a-3f38ae9fc9d9.png">

- Coefficient 들을 기준으로 리셀가에 긍정적(파랑), 부정적(빨강) 영향을 끼치는 피쳐들을 구분하였음
  - 긍정: 에어조던, 에어맥스90, Tan/Brown, Red 색깔
  - 부정: Blue 색깔 

### 2.4. Interpreting Coefficients (PDP Plot)

<img width="795" alt="스크린샷 2022-07-21 오전 1 13 12" src="https://user-images.githubusercontent.com/90128775/180031356-e9ef7291-9166-41a4-bfd7-5e98033537ac.png">

- PDP Plot을 통해 확인해본 결과 피쳐 '에어조던' 의 경우에는 리셀가에 긍정적인 영향, 반대로 파란색의 경우에는 리셀가에 부정적인 영향(리셀가 하락)을 끼침 

### 2.5. Prediction

<img width="851" alt="스크린샷 2022-07-21 오전 1 15 55" src="https://user-images.githubusercontent.com/90128775/180031964-1f8ebab4-3012-45ad-9ad8-d44104880dbe.png">

- 실제로 모델을 사용하여 리셀가를 예측해본 결과 어느 정도 근접한 예측 값을 보여줌 

# 3. 회고 및 향후 발전방향  
- 서비스 개발?
- 모델을 좀 더 이용하게 쉽게 만들기 (현재 기준에서는 모델에 피쳐를 하나 하나 다 지정해서 넣어줘야 됨) 
