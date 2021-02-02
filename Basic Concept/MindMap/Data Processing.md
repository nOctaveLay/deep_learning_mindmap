# Machine Learning Data Processing

## Data Types

Nominal

>is for mutual exclusive, but not ordered, categories
>
>= 서로가 서로에게 어떠한 영향도 미치지 않는 것, 순서, 카테고리 x
>
> ex : genotype, blood type, zip code, gender, race, eye color, political party

Ordinal

> is one where the order matters but not the difference between values
>
> = 순서는 중요하지만 value 사이에 차이 x
>
> ex : socio economic status (“low income”,”middle income”,”high income”),
> education level (“high school”,”BS”,”MS”,”PhD”),
> income level (“less than 50K”, “50K-100K”, “over 100K”),
> satisfaction rating (“extremely dislike”, “dislike”, “neutral”, “like”, “extremely like”).

Interval

>is a measurement where the difference between two values is meaningful
>
>= 두 개의 value의 차이가 의미있는 값
> ex : emperature (Farenheit), temperature (Celcius), pH, SAT score (200-800), credit score (300-850).

Ratio

>has all the properties of an interval variable, and also has a clear definition of 0.0.
>
>= interval variable 의 모든 property를 가지고 있고, 0.0.의 명확한 정의
>
> ex : enzyme activity, dose amount, reaction rate, flow rate, concentration, pulse, weight, length, temperature in Kelvin (0.0 Kelvin really does mean “no heat”), survival time.

|    | Nominal | Ordinal| Interval | Ratio
|:----|:----:|:----:|:----:|:----:
Mode|O|O|O|O
Median||O|O|O
Mean|||O|O

|    |Norminal|Ordinal|Interval|Ratio
|:----|:----:|:----:|:----:|:----:
Counts / Distribution| O | O | O | O
Minimum, Maximum|    | O | O | O |
Range|    | O | O | O |
Percentiles|    | O | O | O |
Standard deviation, Variable|  |   | O | O |

|    | Nominal | Ordinal| Interval | Ratio
|:----|:----:|:----:|:----:|:----:
Countable|O|O|O|O
Order defined||O|O|O
Difference defined (addition, subtraction) |||O|O
Zero defined (multiplication, division) ||||O

## Data Exploration

### Variable Identification

- Predictor (Input) 과 Target(output) 변수들을 정의
- 그 다음, 변수들의 Data type과 카테고리 정의

### Univariate Analysis

- Continuous Features (연속된 특징)
  - Mean, Median, Mode, Min, Max, Range, Quartile, IQR, Variance, Standard, Deviation, Skewness, Histogram, Box Plot

- Categorical Features (분류된 특징)
  - Frequency, Histogram

### Bi-variate Analysis

- 두개의 variable 사이에서 관계를 찾음

#### Numerical & Numerical

- Scatter Plot
  - linear correlation을 하기 전에 혹은 regression line을 맞추기 전에 그리는 것
- Correlation Plot - Heatmap
  - 2개의 numerical variable 사이에서 linear relationship의 강점을 수량화한다.

#### Categorical & Categorical

- Two-way table(=contigency table)
  - count와 count%에 대한 두가지 방법의 table을 생성함으로서 관계를 분석하는 것을 시작할 수 있다.
- Stacked Column Chart
  - 하나의 variable에서 나온 각각의 카테고리가 2번째 variable의 카테고리 전체에게 영향을 주는 비율을 비교
- Combination Chart
  - 차트가 다른 종류의 정보를 포함하고 있는 것을 강조하기 위한 2개 이상의 chart type
- Chi-Square Test
  - categorical variable들 사이에서의 결합을 결정하기 위해 사용된다.
  - 이 test는 변수들 사이에서 관계의 통계학적인 중요성을 얻기 위해서 사용된다.

#### Categorical & Numerical

- Line Chart with Error Bars
- Z-Test / T-Test
- ANOVA

## Feature Cleaning

### Missing values

One may choose to either omit elements from a dataset that contain missing values or to impute a value
= missing value를 포함하고 있는 dataset에서 수정할 element를 선택 하거나 value를 삽입하는 것<br><br>

### Special Values
<br>
Numeric variables are endowed with several formalized special values including +-Inf, NA and NAN.<br>
Calculations involving special values often result in special values, and need to be handled/cleaned <br>
= Numerica variable들은 +-Inf, Na, NAN을 포함한 특별한 value로 여러번 formalize될 수 있다.
= 특별한 value들을 포함한 계산은 특별한 value로 나온다. 그리고 다뤄지거나 삭제될 필요가 있다.

### Outliers
<br>
They should be detected, but not necessarily removed.
Their inclusion in the analysis is a statistical decision.
이들은 발견될 수는 있지만, 필수적으로 삭제되지는 않는다.
분석에서 이들의 포함은 통계적인 결정이다.

### Obvious inconsistencies
A person's age cannot be negative, a man cannot be pregnant and under-aged person cannot possess a drivers license.
= 절대로 될 수 없는 명제 ex) 사람의 나이가 음수

## Feature Imputation
특징 삽입
### Hot-Deck
The technique then finds the first missing value and uses the cell value immediately prior to the data that are missing to impute the missing value<br>
= first missing value를 찾음, missing value를 imput하는 것을 잃어버리는 데이터 이전에 cell value를 즉각적으로 찾음. <br><br>

### Cold-Deck
Selects donors from another dataset to complete missing data<br>
= missing data를 완성시키기 위해서 다른 dataset에서 donor를 선택<br><br>

### Mean-substitution
Another imputation technique involves replacing any missing value with the mean of that variable for all other cases, which has the benefit of not changing the sample mean for that variable.<br>
= 다른 삽입 기술은 그 varibale을 위한 샘플 평균을 변화시키는 것이 아닌 것으로 산출되는 이득을 가지는 모든 cases를 위해 있는 그 variable 의 평균으로 어떤 missing value를 대체하는 것을 포함한다.<br><br>

### Regression
A regression model is estimated to predict observed values of a variable based on other variables, and that model is then used to impute values in cases where that variable is missing <br>
= 다른 variable에 기반한 variable의 observed value를 예측하도록 추정되는 모델.<br>
= 이 모델은 variable이 사라진 곳에 value를 넣는데 사용한다.<br><br>

## Feature Engineering

### Decompose
Converting 2014-09-20T20:45:40Z into categorical attributes like hour_of_the_day, part_of_day, etc. <br>
= 2014-09-20T20:45:40Z를 카테고리 속성으로 바꿈 : hour_of_the_day, part_of_day 같은 식으로<br><br>

### Discretization
**Continuous Features**<br>
Typically data is discretized into partitions of K equal lengths/width (equal intervals) or K% of the total data (equal frequencies)<br>
= 일반적으로 data는 K개의 같은 길이/넓이 (같은 구간)의 조각 혹은 모든 데이터 (주파수가 동등한)의 K%로 나눠진다.<br><br>

**Categorical Features**<br>
Values for categorical features may be combined, particularly when there’s few samples for some categories<br>
= 특히 어떤 카테고리에 매우 적은량의 sample만 있을 때 카테고리로 만들 수있는 특징들은 결합된다. <br><br>

### Reframe Numerical Quantities
Changing from grams to kg, and losing detail might be both wanted and efficient for calculation<br>
= gram을 kg으로 바꾸면서, detail을 잃는 것은 원해서 그러거나 계산을 효율적으로 하기 위함이다.<br><br>

### Crossing

Creating new features as a combination of existing features. <br>
Could be multiplying numerical features, or combining categorical variables.<br> 
This is a great way to add domain expertise knowledge to the dataset.<br><br>

= 현재 있는 특징들을 결합함으로서 새로운 특징들을 만든다.<br>
= 셀 수 있는 특징들을 곱하거나 카테고리 변수들을 결합할 수 있다 <br>
= 데이터 셋에 전문적인 지식의 domain을 추가하는 아주 좋은 방법이다. <br><br>

## Feature Selection
### Correlation
Features should be uncorrelated with each other and highly correlated to the feature we’re trying to predict.
[correlation 1]<br><br>
**Convariance** :  A measure of how much two random variables change together. <br> 
Math: dot(de_mean(x), de_mean(y)) / (n - 1)<br><br>

### Dimensionality Reduction
**Principal Component Analysis(PCA)**
Principal component analysis (PCA) is a statistical procedure that uses an orthogonal transformation to convert a set of observations of possibly correlated variables into a set of values of linearly uncorrelated variables called principal components.<br><br>

This transformation is defined in such a way that the first principal component has the largest possible variance (that is, accounts for as much of the variability in the data as possible), and each succeeding component in turn has the highest variance possible under the constraint that it is orthogonal to the preceding components.<br><br>

= PCA는 가능한 상호 연관된 변수(possibly correlated variables)들의 관찰 집합을 principal component라고 불리는 선형 비상호 연관 변수(linearly uncorrelated variables)들의 값의 집합으로 변환하는 직교 변환을 사용하는 통계적인 과정이다.<br>
이런 변형은 first principal component가 가장 큰 가능한 변수를 갖는것이다. <br>
(이 말은, data에서 가능한 한 variability를 많이 설명한다.) <br>
그리고, 각각의 연속적인 component는 앞서 가는 component들에게 직교해야 한다는 제한 아래에서 차례로 가능한 가장 높은 variance를 가진다.<br>
<br>
Plot the variance per feature and select the features with the largest variance.<br><br>
= feature별로 변수를 plot해라, 그리고 가장 큰 변수로 feature를 골라라.<br><br>

**Singular Value Decomposition(SVD)**
SVD is a factorization of a real or complex matrix.<br> 
It is the generalization of the eigendecomposition of a positive semidefinite normal matrix (for example, a symmetric matrix with positive eigenvalues) to any m×n matrix via an extension of the polar decomposition.<br> 
It has many useful applications in signal processing and statistics.<br><br>

= SVD는 real or complex 행렬의 인수분해이다.<br>
= 양극 분해(polar decomposition)의 확장을 통해 모든 mxn 행렬에 대한 positive semidefinite normal matrix(0이 포함되고, 모든 행렬이 양수인 정규행렬 예를 들어, positive 고유벡터를 가지고 있는 sysmmetric matrix 다) 의 고유값분해(eigendecomposition)의 일반화이다.<br>
= 시그널 프로세싱과 통계학에 많이 적용된다. <br><br>


### Importance
#### Filter Methods 
Filter type methods select features based only on general metrics like the correlation with the variable to predict.<br> 
Filter methods suppress the least interesting variables. <br>
The other variables will be part of a classification or a regression model used to classify or to predict data.<br>
These methods are particularly effective in computation time and robust to overfitting.<br><br>

Filter type method는 예측하기 위한 variable으로 하는 correlation 처럼 일반적인 행렬에 기본을 두고 특징을 선택한다. <br>
Filter method는 덜 흥미로운 변수들을 압도한다.<br>
다른 variable들은 classification의 부분이거나 데이터를 분류하거나 예측하기 위해 사용되는 regression model의 부분이 된다.<br>
이러한 방법은 계산 시간에서 특히 효과적이다. 그리고 overfitting에 robust하다.<br><br>
* Correlation
* Linear Discriminant Analysis
* ANOVA: Analysis of Variance
* Chi Square

#### Wrapper Methods
Wrapper methods evaluate subsets of variables which allows, unlike filter approaches, to detect the possible interactions
between variables. <br>
The two main disadvantages of these methods are : The increasing overfitting risk when the number of observations is insufficient.<br> 
AND. The significant computation time when the number of variables is large.<br><br>

Wrapper methods는 filter 접근과는 다르게 variable 사이에서 가능한 상호작용을 탐지하는 것을 허락하는 variable의 subset을 평가하는 것이다.<br>
이러한 방법들에서 안 좋은 2가지 점이 있다.<br>
첫 번째는, observation의 수가 불충분할 때 overfitting risk가 증가<br>
두 번째는, variable의 수가 많을 때 중요한 계산 시간이다.<br><br>

* Forward Selection
* Backward Elimination
* Recursive Feature Ellimination
* Genetic Algorithms

#### Embedded Methods
Embedded methods try to combine the advantages of both previous methods.<br>
A learning algorithm takes advantage of its own variable selection process and performs feature selection and classification simultaneously.<br><br>

Embedded method는 과거의 method들의 장점들을 결합하려고 한다.<br>
학습 알고리즘은 변수 선택 과정의 이점을 취한다. 그리고 특징 선택과 분류를 동시에 한다.<br><br>

* Lasso regression performs L1 regularization which adds penalty equivalent to absolute value of the magnitude of coefficients.<br>
    = Lasso regression은 coefficient의 크기의 절댓값과 동일하게 페널티를 더하는 L1 정규화를 한다. <br>
* Ridge regression performs L2 regularization which adds penalty equivalent to square of the magnitude of coefficients.<br>
    = Ridge regression은 coefficient의 크기의 제곱과 동등하게 페널티를 더하는 L2 정규화를 한다.<br>

## Feature Encoding
Machine Learning algorithms perform Linear Algebra on Matrices, which means all features must be numeric. 
Encoding helps us do this.<br><br>

= 머신 러닝 알고리즘은 모든 feature가 numeric 한 행렬에 작용하는 선형 대수를 수행한다.<br><br>

* Label Encoding<br>
* One Hot Encoding<br>

In One Hot Encoding, make sure the encodings are done in a way that all features are linearly independent.<br>
One Hot Encoding에서 모든 feature들이 선형 독립적인 방법으로 encoding이 된다는 것을 확신해라.

## Feature Normalisation or Scaling
Since the range of values of raw data varies widely, in some machine learning algorithms, objective functions will not work properly without normalization. 
Another reason why feature scaling is applied is that gradient descent converges much faster with feature scaling than without it.

= raw data의 값의 범위가 넓기 때문에, machine learning algorithm에서, objective function(목적 함수)은 normalization(정규화)없이는 적절하게 작동하지 않을 것이다.
= 왜 feature scaling이 적용되는 지에 대한 또 다른 이유는, gradient descent가 feature scaling과 함께 하면 더 빠르게 수렴되기 때문이다.

* Method
    * Rescaling <br> 
    The simplest method is rescaling the range of features to scale the range in [0, 1] or [-1, 1].<br>
    가장 일반적인 방법은 [0,1] [-1,1] 범위 안으로 들이기 위해서 feature의 범위를 리스케일링하는 것이다.<br>
    * Standardization <br>
    Feature standardization makes the values of each feature in the data have zero-mean (when subtracting the mean in the numerator) and unitvariance.<br>
    Feature standardization은 zero-mean (numerator에서 평균을 빼는 것)과 unitvariance를 가지는 data 안에서 각각의 feature의 value를 만드는 것이다.<br>
    * Scaling to unit length - To scale the components of a feature vector such that the complete vector has length one.
    Feature vector의 컴포넌트를 증가시키기 위함. 그래서 complete vector는 length one을 가진다.<br>
    
## Dataset Construction 
### Training Dataset
A set examples used for learning <br>
학습을 위해 사용되는 예제.<br>

To fit the parameters of the classifier in the Multilayer Perceptron, for instance, we would use the training set to find the "optimal" weights when using back-progapation.<br>
Multilayer Perceptron에서 classifier의 parameter를 맞추기 위함, 예를 들어, back propagation을 할 때 "최적의" weight를 찾기 위해서 training set을 사용한다.<br><br>
### Test Dataset
A set of examples used only to assess the performance of a fully-trained classifier<br>
완전히 훈련된 classifier의 performance을 측정할 때 사용되는 예제.<br>

In the Multilayer Perceptron case, we would use the test to estimate the error rate after we have chosen the final model (MLP size and actual weights) <br>
Multilayer Perceptron case에서, 최종 모델을 고른 후에 error rate를 추정하기 위해서 test를 사용한다. <br>
After assessing the final model on the test set, YOU MUST NOT tune the model any further<br>
test set에서의 최종 모델에 접근한 후, 더 이상 모델을 조정하면 안된다.<br>

### Validation Dataset
A set of examples used to tune the parameters of a classifier<br>
= classifier의 parameter를 조정하는데 사용되는 예제.<br><br>

In the Multilayer Perceptron case, we would use the validation set to find the “optimal” number of hidden units or determine a stopping point for the back-propagation algorithm<br>
= Multilayer Perceptron case에서, hidden unit의 최적의 갯수를 찾고 싶거나, back-propagation algorithm에서 stopping point를 결정하기 위해 validation set을 사용한다.<br><br>

### Cross Validation
One round of cross-validation involves partitioning a sample of data into complementary subsets, performing the analysis on one subset (called the training set), and validating the analysis on the other subset (called the validation set or testing set). <br>
= cross-validation의 첫번째 라운드는 하나의 subset에 대한 분석을 수행하는 동안 데이터 샘플을 complementary subset으로 분리하는 것을 포함한다. (이를 training set이라고 부른다.)<br>
그리고 다른 subset에 대한 유효성 분석을 한다. (이를 validation set 혹은 testing set이라고 부른다)<br><br>

To reduce variability, multiple rounds of cross-validation are performed using different partitions, and the validation results are averaged over the rounds.<br>
= variability를 줄이기 위해서, cross-validation의 여러 번의 round는 다른 partition을 사용해서 수행된다. 그리고 validation result는 round마다 평균을 낸다.<br><br>




[correlation1] 

출처 :
https://github.com/dformoso/machine-learning-mindmap 
https://www.graphpad.com/support/faq/what-is-the-difference-between-ordinal-interval-and-ratio-variables-why-should-i-care/
https://www.saedsayad.com/bivariate_analysis.htm
