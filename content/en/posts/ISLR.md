---
title: "ISLR Note"
author: "Hoontaek Lee"
date: 2018-04-05T16:00:00+09:00
lastmod: 2020-05-16T19:02:31+09:00
description:
draft: false
hideToc: false
enableToc: true
enableTocContent: false
tocPosition: outer
tocLevels: ["h2", "h3", "h4"]
tags:
- 2020
- Book Review
- R
---

# 2. Statistical Learning
## 2.1. What Is Statistical Learning?
*Y* = *f*(*X*) + *e*  
여기서 함수 *f*는 *X*가 담고 있는 *Y*에 대한 **systematic information**이다.  
*e*는 *f*가 표현하지 못하는 **random error term**이다.  
*e*는 *X*에 독립이고 평균값은 0이다.  

**Statistical learning**은 위의 함수 *f*를 찾는 다양한 방법을 모두 일컫는다.

### 2.1.1. Why Estimate *f*?

- prediction
    - 측정값 *X*로 *Y* 값을 예측한다(*Y* = *f*(*X*)).
    - *f*는 *black box*로 남아도 상관 없다(*Y*만 잘 맞추면 된다).
    - 이 때 발생하는 에러는 두 가지: <u>reducible</u>, <u>irreducible</u>.
    - reducible: *f*를 더 잘 예측하면 줄일 수 있다.
    - irreducible: 측정 항목에서 어떤 중요한 변수를 놓치고 있거나,  
    혹은 측정 불가능한 요소(예: 약물 투여 때 환자의 심리)가 개입하기 때문에 발생한다.
    
- inference
    - *Y*와 각 *X*의 관계를 정확히 파악하고 싶다.
    - *f*는 *black box*로 남으면 안 된다.
    - 어떤 *X*가 *Y*와 더 관계가 강한지, 여러 *X*와 *Y*의 관계는 선형인지 비선형인지 등.

문제에 따라서  

- prediction과 inference 중 하나만, 혹은 둘 다 필요할 수 있다.  
- 간단한 선형 모형으로도 만족할 수도 있고, 복잡한 비선형 모형을 사용해야 할 수도 있다.

### 2.1.2. How Do We Estimate *f*?

*f*를 찾는 데는 여러 방법이 있는데, 이들이 공통으로 가지는 특징이 있다.

- training data: {(*x*~1~, *y*~1~), ..., (*x*_~n~_, *y*_~n~_)} 
- parametric or non-parametric method 중에 하나다.
- parametric methods
    - *f*의 형태(equation, distribution, ...)를 상정한 후(parameter가 정해진다)
    - parameter 값을 추정해서 *f*를 결정한다.
    - *f*를 찾는 문제가 몇개의 paraemters를 추정하는 문제로 바뀐다(쉬워진다).
    - *f*의 형태를 잘못 상정했다면 오차가 커질 수 있다.
    - 위의 경우를 방지하기 위해 *f*의 형태에 <u>flexibility</u>를 높이고자 한다면 더 많은 parameters가 필요하고,  
    따라서 <u>overfitting</u>이 발생할 확률도 높아진다. 
- non-parametric methods
    - *f*에 특정한 형태를 상정하지 않는다.
    - 때문에 *f*가 실제로 어떤 형태를 갖더라도 정확히 추정할 잠재력이 있는 방법이다.
    - 단, parameter estimation이라는 쉬운 문제로 바꾸지 않았기 때문에  
    parametric methods보다 훨씬 많은 관측 데이터가 필요하다. 

### 2.1.3. The Trade-Off Between Prediction Accuracy and Model Interpretability

restrictive --> interpertable (inference 목적에 적합)  
하지만, prediction 목적에서도 꼭 the most flexible approach를 사용하는 게 정답은 아니다(2.2에서 다룰 예정).

### 2.1.4. Supervised Versus Unsupervised Learning
supervised: *Y* 관측값 존재 <-> unsupervised

### 2.1.5. Regression Versus Classification Problems
**response variable**이  
연속형 --> regression  
범주형 --> classification

일반적으로 **predictor**는 연속형, 범주형 각각에 맞춰 코딩 가능하기 때문에 위의 판정에서는 덜 중요하다.

## 2.2. Assessing Model Accuracy

모든 상황에 만능인 모델은 없다.  
해결해야 할 문제에 따라, 주어진 데이터에 따라 가장 적합한 모델이 매번 달라진다.  

그래서 상황마다 매번 여러 모델을 비교해본다.

### 2.2.1. Measuring the Quality of Fit

Mean squared error(MSE): regression setting에서는 가장 많이 사용한다.  

> *MSE*   
> = $\frac{1}{n}$$\sum_{i=1}^{n}$(*y*~*i*~ - $\hat{f}$(*x*~*i*~))^2^  
> = Ave(*y*~*i*~ - $\hat{f}$(*x*~*i*~)^2^)

training MSE vs test MSE: 우리가 관심 있는 건 minimize(test MSE).

(Figure 2.9)  
1. training MSE는 flexibility가 증가할수록 단조 감소하는 패턴을 보이고,  
2. test MSE는 flexibility와 U자형 관계를 보인다.  
즉, training MSE를 낮추기 위해 flexibility를 마구 증가시키면  
정작 test MSE는 restrictive model보다 오히려 더 높아질 수 있다(**overfitting**).


2의 U자형 관계로부터 **test MSE에 최솟값이 존재**함을 확인했는데,  
<u>최소 MSE를 가지는 model을 찾는 방법</u>도 다루게 될 것이다(예: 5장의 cross-validation).  

### 2.2.2. The Bias-Variance Trade-Off

test MSE 기댓값 =  함숫값의 분산 + 함숫값의 bias 제곱 + 오차항 분산  
우변의 세 항 모두 0 이상이기 때문에 좌변의 최솟값은 오차항 분산(irreducible error)이 된다.  

flexible *f* --> high variance(데이터에 따라 *f* 형태가 쉽게 변한다), low bias(데이터를 잘 맞춘다)  

(Figure 2.12)  
flexibility가 증가하기 시작하면  

처음에는  
bias가 감소하는 속도 > variance가 증가하는 속도  --> test MSE 감소

일정 지점이 지나면
bias가 감소하는 속도 < variance가 증가하는 속도  --> test MSE 증가

### 2.2.3. The Classification Setting

MSE --> regression setting에서 사용한다.
classification setting에서는 **error rate**를 사용한다(minimize).  

> error rate = (*y* 범주를 잘못 예측한 데이터 개수) / (전체 데이터 개수)

# 5. Resampling Methods

Resampling Methods  
- 같은 training data에서 샘플 추출 -> model fitting 반복하는 과정이다.  
- 어떤 추가 정보(?)를 얻을 수 있다.  
- cross-validation: flexibility 결정하거나 test error 구할 때 사용한다.  
- bootstrap: parameter estimate accuracy 평가할 때 가장 많이 사용한다.  

model assessment: model performance 평가  
model selection: model flexibility 선택  

## 5.1. Cross-Validation


### 5.1.1. The Validation Set Approach

전체 데이터를 같은 크기의 두 subsets - *training set* + *validation set* (or *hold-out set*) - 으로 나눈다. **랜덤하게**.  
training set을 이용해 model fitting 후 validation set으로 test error (e.g. MSE) 계산한다.  

* 두 가지 단점
    * 데이터를 나눌 때마다 MSE가 달라진다.
    * model fitting에 수집한 데이터를 모두 활용할 수 없다 --> MSE가 과대평가된다.
    

위 단점을 해결한다 --> **cross-validation**

### 5.1.2. Leave-One-Out Cross-Validation

(*x*~1~, *y*~1) 제외한 *n*-1 개 데이터를 사용해 training한다.  
남겨둔 데이터로 test error rate(MSE~1~)를 계산한다.  
같은 방법으로 test 데이터를 (*x*~*n*~, *y*~*n*)까지 변경하며 n번 진행, MSE~*n*~까지 구한다.  

test error rate = CV~(*n*)~ = Ave(MSE~*i*~)

* LOOCV 장점(= validation set approach의 단점 해결)
    * 데이터를 충분히 사용하기 때문에 bias를 과대평가할 위험도가 validation set approach보다 낮다.
    * test error rate가 일정하다.

LOOCV는 대부분의 predictive modeling에 적용할 수 있다.  
least square linear (or polynomial) regression에서는 CV~(*n*)~을 더 간단하게 계산할 수 있다(식 5.2).   

### 5.1.3. k-Fold Cross-Validation

LOOCV와 비슷한데, test로 사용할 데이터를 한 개씩이 아니라 한 그룹씩 남기는 차이가 있다.

fold = group  
데이터를 같은 크기의 *k*개 그룹으로 랜덤하게 나눈다.  
1^st^ 그룹을 제외한 나머지로 training, 남겨둔 그룹으로 error rate 계산(MSE~1~)
*k*^th^ 그룹까지 진행(MSE~*k*~).

test error rate = CV~(*k*)~ = Ave(MSE~*i*~)

<u>LOOCV는 *k*=*n*인 *k*-Fold CV로 볼 수 있다.</u>  
보통 *k*는 5나 10을 사용한다.  
- 계산량이 줄어들기 때문  
- 5나 10을 사용해도 LOOCV와 flexiblility with minimum MSE 결과가 비슷하기 때문  

### 5.1.4. Bias-Variance Trade-Off for k-Fold Cross-Validation

*k*-fold CV에서 *k* 값에 따라 bias-variance trade-off가 발생한다.

*k*가 *n*에 가까울수록  
예측치의 bias는 감소하고() 분산은 증가한다.  

*k*로 5나 10을 많이 사용하는 이유 : test error rate가 가장 작기 때문

### 5.1.5. Cross-Validation on Classification Problems

CV 수식에서 MSE 대신 잘못 분류한 데이터 비율을 사용한다. 

## 5.2. The Bootstrap

관측 데이터로부터 새로운 데이터셋을 만드는 기법이다.  
랜덤하게, 원래 관측데이터와 같은 크기만큼 재추출한다.  
복원 혹은 비복원 추출 선택.  

예)  
데이터가 세 개 밖에 없어도
크기가 3인 데이터셋 B개를 새로 만들어서  
각 데이터셋마다 estimates 계산하고(총 B개), 이로부터 standard error 계산한다.

- can be used **to quantify the uncertainty** associated with a given estimatior or statistical learning method (예: 선형회귀에서 추정한 모수값의 표준오차).
- 선형회귀 외 많은 모형에도 쉽게 적용 가능!

```
(식 5.8에서)

왜 괄호 안이 alpha - alpha_hat이 아니지?  
    
alpha의 참값을 모른다고 가정하기 때문에  
alpha_hat을 참값 대신 사용하고, 각 alpha마다 bootstrap을 B번 실행해서 alpha의 SS를 계산하는 건가?
```

## 5.3. Lab: Cross-Validation and the Bootstrap

### 5.3.1. The Validation Set Approach


```r
library(ISLR)
set.seed(1) # set seed to get the same results at a later time
train = sample(x = 392, size = 196) # training subset

# fit a simple linear model
lm.fit = lm(mpg ~ horsepower, data = Auto, subset = train)
attach(Auto)
mean((mpg - predict(lm.fit, Auto))[-train] ^ 2) # compute MSE
```

```
## [1] 23.26601
```

```r
# fit a quadratic linear model 
lm.fit2 = lm(mpg ~ poly(horsepower, 2), data = Auto, subset = train)
mean((mpg - predict(lm.fit2, Auto))[-train] ^ 2) # compute MSE
```

```
## [1] 18.71646
```

```r
# fit a cubic linear model 
lm.fit3 = lm(mpg ~ poly(horsepower, 3), data = Auto, subset = train)
mean((mpg - predict(lm.fit3, Auto))[-train] ^ 2) # compute MSE
```

```
## [1] 18.79401
```

```r
plot(horsepower, mpg) # looks like a curve fit is better than a straight line
```

![](ISLR_files/figure-html/5.3.1.-1.png)<!-- -->

### 5.3.2. Leave-One-Out Cross-Validation


```r
lm.fit = lm(mpg ~ horsepower, data = Auto)
glm.fit = glm(mpg ~ horsepower, data = Auto)

coef(lm.fit)
```

```
## (Intercept)  horsepower 
##  39.9358610  -0.1578447
```

```r
coef(glm.fit) # glm() w/o family argument --> lm()
```

```
## (Intercept)  horsepower 
##  39.9358610  -0.1578447
```

```r
## cv for a simple linear fit
library(boot)
glm.fit = glm(mpg ~ horsepower, data = Auto)
cv.err = cv.glm(Auto, glm.fit)
cv.err$delta # CV(n) results: standard one, bias-corrected one
```

```
## [1] 24.23151 24.23114
```

```r
## cv iteration for polynomial fit of order 1 to 5 
cv.error = rep(0, 5)
for(i in 1:5){
  glm.fit = glm(mpg ~ poly(horsepower, i), data = Auto)
  cv.error[i] = cv.glm(data = Auto, glmfit = glm.fit)$delta[1]
}
cv.error
```

```
## [1] 24.23151 19.24821 19.33498 19.42443 19.03321
```

### 5.3.3. k-Fold Cross-Validation


```r
set.seed(17)
cv.error.10 = rep(0, 10)
for(i in 1:10){
  glm.fit = glm(mpg ~ poly(horsepower, i), data = Auto)
  cv.error.10[i] = cv.glm(data = Auto, glmfit = glm.fit, K = 10)$delta[1]
  # much shorter running time than that of LOOCV
}

# still cubic or higher order terms don't seem superior
plot(cv.error.10, type = "b")
```

![](ISLR_files/figure-html/5.3.3.-1.png)<!-- -->

### 5.3.4. The Bootstrap


```r
## accuracy of regression model --> standard error of parameter estimated
## bootstrap can be applied to compute the se

library(boot)

## 1. create a function to compute statistics of interest
alpha.fn = function(data, index){
  X = data$X[index]
  Y = data$Y[index]
  return((var(Y) - cov(X, Y)) / (var(X) + var(Y) - 2 * cov(X, Y)))
}

## 2. boot()


## compute an alpha value (a kind of statistics)
set.seed(1)
alpha.fn(Portfolio, sample(100, 100, replace = TRUE)) 
```

```
## [1] 0.7368375
```

```r
## repeat 1000 times with bootstrap
boot(Portfolio, alpha.fn, R = 1000) 
```

```
## 
## ORDINARY NONPARAMETRIC BOOTSTRAP
## 
## 
## Call:
## boot(data = Portfolio, statistic = alpha.fn, R = 1000)
## 
## 
## Bootstrap Statistics :
##      original       bias    std. error
## t1* 0.5758321 -0.001695873  0.09366347
```

```r
# se(alpha_hat) = 0.5758321 +- 0.08861826


## linear regression coef. estimates
boot.fn = function(data, index){
  return(coef(lm(mpg ~ horsepower, data = data, subset = index)))
}

boot.fn(data = Auto, index = 1:392)
```

```
## (Intercept)  horsepower 
##  39.9358610  -0.1578447
```

```r
set.seed(1)
boot.fn(data = Auto, index = sample(392, 392, replace = TRUE))
```

```
## (Intercept)  horsepower 
##  40.3404517  -0.1634868
```

```r
boot.fn(data = Auto, index = sample(392, 392, replace = TRUE))
```

```
## (Intercept)  horsepower 
##  40.1186906  -0.1577063
```

```r
# with replacement --> the result can vary

boot(Auto, boot.fn, 1000)
```

```
## 
## ORDINARY NONPARAMETRIC BOOTSTRAP
## 
## 
## Call:
## boot(data = Auto, statistic = boot.fn, R = 1000)
## 
## 
## Bootstrap Statistics :
##       original        bias    std. error
## t1* 39.9358610  0.0544513229 0.841289790
## t2* -0.1578447 -0.0006170901 0.007343073
```

```r
# compare to
summary(lm(mpg ~ horsepower, data = Auto))$coef
```

```
##               Estimate  Std. Error   t value      Pr(>|t|)
## (Intercept) 39.9358610 0.717498656  55.65984 1.220362e-187
## horsepower  -0.1578447 0.006445501 -24.48914  7.031989e-81
```

```r
# se estimates are more accurate in boot() than in lm() (see ISLR 196p)

## better fit --> more similar se between boot() and summary()
boot.fn = function(data, index){
  coefficients(lm(mpg ~ horsepower + I(horsepower ^ 2), 
                  data = data, 
                  subset = index))
}

set.seed(1)
boot(Auto, boot.fn, 1000)
```

```
## 
## ORDINARY NONPARAMETRIC BOOTSTRAP
## 
## 
## Call:
## boot(data = Auto, statistic = boot.fn, R = 1000)
## 
## 
## Bootstrap Statistics :
##         original        bias     std. error
## t1* 56.900099702  3.511640e-02 2.0300222526
## t2* -0.466189630 -7.080834e-04 0.0324241984
## t3*  0.001230536  2.840324e-06 0.0001172164
```

```r
summary(lm(mpg ~ horsepower + I(horsepower ^ 2), 
                  data = Auto))$coef
```

```
##                     Estimate   Std. Error   t value      Pr(>|t|)
## (Intercept)     56.900099702 1.8004268063  31.60367 1.740911e-109
## horsepower      -0.466189630 0.0311246171 -14.97816  2.289429e-40
## I(horsepower^2)  0.001230536 0.0001220759  10.08009  2.196340e-21
```


# 7. Moving Beyond Linearity
## 7.4. Regression Splines
### 7.4.1. Piecewise Polynomials

knot라고 부르는 위치를 기준으로 구간을 나눠서 polynomial regression fitting을 수행한다.  
knot에서 각 곡선이 툭툭 끊어질 수 있다.

### 7.4.2. Constraints and Splines

툭툭 끊기지 않고 부드럽게 이어지는 spline curve를 만들기 위해 아래의 constraints를 추가 (삼차식일 경우)

- knot에서 함숫값
- knot에서 미분계수
- knot에서 이차미분계수

일차식이라면 첫 번째 조건만으로도 충분하다.

# 8. Tree-Based Methods

* *tree-based* methods = *decision tree* methods : 설명변수를 여러 구간으로 나눈다
* regression, classification 모두 가능하다
* 해석이 (그나마) 용이하다
* 단순한 tree 구조만으로는 다른 머신러닝 기법에 비해 예측 정확도가 낮다
* *bagging*, *random forests*, *boosting* 이용 --> 모형이 복잡해진다 -->  예측 정확도 <-> 해석 용이성 trade-off

## 8.1. The Basics of Decision Trees

### 8.1.1. Regression Trees

decision tree의 형태와 관련된 용어는 거꾸로 꽂아 놓은 나무를 떠올리면 이해하기 쉽다.    

* terminal nodes (leaves): 가장 아래 적혀있는 구역별 y값
* internal node: 분기점
* branch: 각 node를 잇는 선

나무 상단에 위치할 수록 예측에 영향이 큰 조건(분기점)이다.  
조건에 따라 그릴 수 있고 위와 같이 해석이 가능하기 때문에 regression tree는 시각화, 해석이 모두 용이하다.

\ 

#### **Recursive Binary Splitting**


regression tree를 만드는 방법: 1. predictor의 구간을 나눈다, 2. 각 구간별로 예측값(평균, ...)을 구한다.  
그렇다면 구간은 어떻게 나눌까? --> 목적함수를 둔다.  

* 구간별 RSS를 구해서 그 합계가 최소가 되도록 구역을 나눈다

하지만 가능한 모든 경우의 수에서 위의 계산을 하려면 양이 너무 많다.  
그래서 *top-down*, *greedy* approach 혹은 *recursive binary splitting* 알고리즘을 사용한다.

* top-down: 상위 노드(구역 갯수가 1개인 상태)에서 시작하기 때문
* greedy: 구간을 나눌 때마다 지금보다 나은 방법이 아닌 최상의 방법(best split)을 찾기 때문

다음과 같이 작동한다.

1. 먼저 어떤 *X*~*j*~를 어느 값(*s*)을 기준으로 나눠야 두 구역의 RSS 합이 최소가 될지 결정한다.
2. 두 구역으로 나눠진다.
3. 두 구역 중 어느 구역을 어떤 *j*, *s*로 나눠야 세 구역의 RSS 합이 최소가 될지 결정한다.
4. 세 구역이 된다.
5. 세 구역 중 어느 구역을 어떤 *j*, *s*로 나눠야 네 구역의 RSS 합이 최소가 될지 결정한다.
6. 네 구역이 된다.
7. ...
8. <u>특정 조건</u>을 충족할 때까지 계속 구역을 나눈다.
    * 특정 조건의 예: 모든 구역의 관측값이 5개 미만이다
    

\ 

#### **Tree Pruning**  

*recursive binary splitting* 알고리즘은 overffing이 발생하여 정작 test data에서는 성능이 안 좋을 수 있다.  
이를 방지하기 위해 RSS가 일정값 이상 감소하지 않으면 구역을 나누지 않는다!는 규칙을 넣을 수도 있지만,  
그 이후에 RSS가 확 감소하는 구획이 가능했었다면 이를 놓치게 된다.  
따라서 *recursive binary splitting*으로 아주 큰 나무를 만든 후 **가지치기(pruning)**하는 방법을 택한다.  
그렇다면 <u>어떤 기준</u>으로 가지를 쳐낼까?  
우리가 원하는 건 test error rate를 줄이는 건데, 그렇다면 모든 가능한 subtree에서 이를 계산한 후 비교해야 할까?


--> <u>*Cost complexity pruning* (or *weakest link pruning*)</u>을 사용한다!  
원래 목적함수(RSS)에 terminal node 갯수에 패널티를 주는 항($\alpha$|T|)을 추가했다.  
|T|은 subtree의 terminal node 갯수를 의미한다.  
$\alpha$마다 대응하는 subtree가 존재한다.  
$\alpha$가 0이라면 subtree는 원래 가장 커다란 나무와 같겠고,  
$\alpha$가 0보다 클 수록 |T|에 목적함수값이 영향을 많이 받게 되는데(증가),  
이 영향을 없애려면 RSS가 꽤 감소하는 구획이 아닌 한 |T|를 줄여야 할 것이다.  

1. *recursive binary splitting*으로 커다란 나무를 만든다.
2. K-fold CV 방법으로 test error rate를 최소화하는 $\alpha$를 결정한 후, 
3. 이 $\alpha$에 대응하는 subtree를 최종 모형으로 결정한다.

### 8.1.2. Classification Trees

Regression tree와 다른 점

* 반응변수가 범주형(<u>설명변수도 범주형일 수 있다</u>)
* terminal node에는 그 구역의 평균값이 아니라 가장 빈도가 높은 범주
* 구역마다 계산할 criteron은 RSS 대신 다른 것
    * 가장 빈도가 높은 범주에 속하지 않는 데이터의 비율
    * 위 비율 보다는 *Gini index*나 *Entropy*(Shannon index)를 더 많이 쓴다.
    * 위 두 지수는 모두 **impurity**를 나타낸다. 그 구역이 다양한 범주의 데이터로 이루어져 있으면 값이
    커진다.
* predicted classification이 나눠지지 않는 node가 생길 수 있다(나눠도 두 구역 모두 같은 범주)   
    * Gini index나 Entropy를 구획의 목적함수로 사용한다.
    * 위와 같이 구역을 나누면 목적함수값이 줄어들기 때문에(error rate는 같지만) 알고리즘상 node가 추가된다.

### 8.1.3. Trees Versus Linear Models

무엇이 더 나은지는 상황에 따라 다르다.

test error rate가 한쪽이 더 나을 수 있고,  
interpretability가 한쪽이 더 나을 수 있다.

### 8.1.4. Advantages and Disadvantages of Trees
~~(8.1.3이랑 뭐가 달라)~~

(vs classical regression methods)  
(tree methods 입장에서)  

장점  

* 비전문가에게도 설명하기 쉽다
* 인간의 의사결정과정을 더 비슷하게 모사한 방법이다
* 범주형 변수를 다루기 더 쉽다(더미변수 다루는 것보다 훨씬 쉽다)

단점

* 예측 정확도가 낮은 편이다(*bagging*, *random forests*, *boosting*으로 해결)
* non-robust. 데이터에 따라 tree 구조가 변하기 쉽다

## 8.2. Bagging, Random Forests, Boosting

### 8.2.1. Bagging
Bagging = Bootstrap aggregation  
statistical learning method의 variance를 줄이기 위해 사용되는 general-purpose procecure이지만  
decision tree 관련해서 자주 쓰이기 때문에 여기서 소개한다.  

원리

* 평균의 분산은 분산을 n으로 나눈 것 --> 평균을 구하면 분산이 낮아진다!
* resampling 여러번 해서 training set 여러개 생성 --> 각 set마다 tree 생성 --> tree 예측값 평균
* (training set 생성에 bootstrap이 사용된다)
* 범주형일 경우 가장 빈도가 높은 예측 범주로 결정(나무한테 투표권 부여!)
* 생성할 training set 갯수는 크게 중요치 x. 매우 커도 overfitting 없다. 충분히 큰 값으로 고르자.

~~(bootstrap이랑 뭐가 달라)~~

\ 

#### **Out-of-Bag Error Estimation**

bagged model의 test error 구하는 방법: 각 모델에 CV 수행해서 결과 비교할 필요 없다!  
각 bagged tree는 전체 데이터 중 약 2/3를 사용하게 된다.  
이 2/3에 들지 못한 데이터를 out-of-bag(OOB) observation이라 부른다.  
전체 bagged tree가 *B*개 있다면, OOB obs. 한 개당 약 3/B개의 prediction을 구할 수 있다.  
이 3/B개 값을 평균(for regression)하거나 투표(for classification)하면 OOB MSE나 classification error를 구할 수 있다.  
이는 모델을 만들 때 사용하지 않은 데이터(OOB)를 이용해 모델 성능을 평가했으므로 유효한 방법이다.  

~~이게 bootstrap + 3-fold CV랑 다를 게 뭐야~~

\ 

#### **Variable Importance Measures**

bagging을 수행하면 이제 더 이상 해석하기 수월한 모델이 아니게 된다.  
대신 bagged tree를 이용해 어떤 변수가 예측력이 높았는지 알 수 있다.  

* 각 predictor마다 구획 후 감소한 RSS(or Gini index)를 더해서 비교한다.
* 한 predictor가 여러 node에서 사용되었다면 각 node에서 발생한 RSS(or Gini index) 감소량을 모두 더해서 비교한다.



### 8.2.2. Random Forests

Bagging < Random Forests  

만약 어떤 predictor가 특히 영향력이 높다면,  
bagging에서는 이 predictor만 주로 사용하여 구역을 나누게 될 것이다.  
그 결과 bagged tree는 서로 거의 차이가 없을 것이고 예측 결과도 비슷할 것이다.  
이러한 highly correlated quantities를 평균해도 variance reduction 양은 별로 되지 않는다.  

때문에 **Randomforest**는

* decorrelating으로 variance reduction을 높인다.
    * 매 구획마다 몇 개의 predictor를 랜덤하게 뽑아서 이것만 고려한다.
    * 즉 모든 predictor를 공평하게 경쟁시키는 게 아니다.
    * 때문에 영향력 낮은 predictor도 node에 참여할 기회가 많아지고
    * resulted tree도 더욱 다양해진다(decorrelated).
    * 보통 *m*=sqrt(*p*) 만큼 샘플링한다.
    * 평균적으로 (*p*-*m*)/*p* 만큼의 node가 최강 predictor를 고려하지 않게 된다.
    * bagging과 마찬가지로 나무 갯수는 크게 중요x. 충분히 많이 만들자.

```
왜 영향력이 높지 않은 변수를 사용하지? 왜 RF 결과가 더 좋아지지?

Averaging many highly correlated data does not lead to as large of a reduction in variance as averaging many uncorrelated quantities. In particular, this means that bagging will not lead to a substantial reduction in variance over a single tree in this setting

correlated quantities면 평균해도 variance가 별로 줄어들지 않는다?  
근데 
bagging은 highly correlated & highly accurate인 반면
RF는 less correlated & less accurate가 아닐까?  
그래서 variance reduction은 RF가 크지만 accuracy는 bagging이 더 크다? (근데 현실은 RF가 더 정확)

there by making the average of the resulting trees less variable and hence more reliable

decorrelated values를 평균하는 게 왜 less variable?
```

### 8.2.3. Boosting

Bagging과 마찬가지로 decision tree 외 다른 기법에도 두루 쓰일 수 있다.  

작동 원리

* NULL 모델(fx=0), NULL residual(r~i~=y~i~) 생성
* 작은 나무 한 그루 생성, NULL 모델에 더하기, residual 계산
* 작은 나무 한 그루 생성, 기존 나무에 더하기, residual 계산
* 작은 나무 한 그루 생성, 기존 나무에 더하기, residual 계산
* ...

나무 여러개를 만들어서 합치는 게 아니라,  
한 그루를 계속 키우는 방식. *learn slowly*.

관련 모수 3개

* *B*: 만들 총 나무 수. **너무 크면 overffiting 될 수 있다**. CV 사용해서 B 결정한다.
* *$\lambda$*: shrinkage parameter. 새로 만든 작은 나무를 기존 나무에 더하기 전에 이 숫자를 곱해준다.  
즉 나무가 자라는(learning) 속도를 결정한다.
    * 보통 천천히 배울 수록 최종 성능은 좋아진다.
    * 0.01이나 0.001을 주로 사용한다.
* *d*: 새로 만들 작은 나무의 나뭇잎 개수. 
    * 보통 1로 두는데, 이러면 각 나무는 가지가 1개 뿐이니 *stump*가 된다. (stump는 어울리는 용어가 아닌듯)



```
bagging, RF, Boosting이 대략 어떻게 모델을 만든다는 느낌은 온다만
그 과정을 뚜렷하게 그리지는 못 하겠다.

bagging, RF에서 최종 모형은 평균값을 쓴다는 데, 이게 무슨 말이지?
Boosting에서 각 중간 모델(나무)를 기존 것에 더한다는데 이 '더한다'는 게 무슨 말이지?
Boosting에서 residual update는 왜 하지? 어떤 판정 기준으로 사용되는 것도 아니고.
```

## 8.3. Lab: Decision Trees

### 8.3.1. Fitting Classification Trees


```r
library(tree)
library(ISLR)
attach(Carseats)

## create a "High" column
High = ifelse(Sales <= 8, "No", "Yes")
Carseats = data.frame(Carseats, High)
str(Carseats)
```

```
## 'data.frame':	400 obs. of  12 variables:
##  $ Sales      : num  9.5 11.22 10.06 7.4 4.15 ...
##  $ CompPrice  : num  138 111 113 117 141 124 115 136 132 132 ...
##  $ Income     : num  73 48 35 100 64 113 105 81 110 113 ...
##  $ Advertising: num  11 16 10 4 3 13 0 15 0 0 ...
##  $ Population : num  276 260 269 466 340 501 45 425 108 131 ...
##  $ Price      : num  120 83 80 97 128 72 108 120 124 124 ...
##  $ ShelveLoc  : Factor w/ 3 levels "Bad","Good","Medium": 1 2 3 3 1 1 3 2 3 3 ...
##  $ Age        : num  42 65 59 55 38 78 71 67 76 76 ...
##  $ Education  : num  17 10 12 14 13 16 15 10 10 17 ...
##  $ Urban      : Factor w/ 2 levels "No","Yes": 2 2 2 2 2 1 2 2 1 1 ...
##  $ US         : Factor w/ 2 levels "No","Yes": 2 2 2 2 1 2 1 2 1 2 ...
##  $ High       : Factor w/ 2 levels "No","Yes": 2 2 2 1 1 2 1 2 1 1 ...
```

```r
## try to fit a classification tree
tree.carseats = tree(High ~ . -Sales, Carseats)
summary(tree.carseats) 
```

```
## 
## Classification tree:
## tree(formula = High ~ . - Sales, data = Carseats)
## Variables actually used in tree construction:
## [1] "ShelveLoc"   "Price"       "Income"      "CompPrice"   "Population" 
## [6] "Advertising" "Age"         "US"         
## Number of terminal nodes:  27 
## Residual mean deviance:  0.4575 = 170.7 / 373 
## Misclassification error rate: 0.09 = 36 / 400
```

```r
# training error rate = 9%
# deviance: smaller is good
# residual mean deviance: deviance / (n - |T|)

plot(tree.carseats) # plot tree
text(tree.carseats, pretty = 0) # add text
```

![](ISLR_files/figure-html/8.3.1-1.png)<!-- -->

```r
## test error rate
set.seed(2)
train = sample(1:nrow(Carseats), 200)
Carseats.test = Carseats[-train, ]
High.test = High[-train]
tree.carseats = tree(High ~ . -Sales, Carseats, subset = train)
tree.pred = predict(object = tree.carseats, 
                    newdata = Carseats.test,
                    type = "class") # specifying the tree is for classification

# test error rate = diagonal / whole
sum(diag(table(tree.pred, High.test))) / sum(table(tree.pred, High.test))
```

```
## [1] 0.77
```

```r
## pruninig (cost complexity pruning)
set.seed(3)
cv.carseats = cv.tree(tree.carseats, 
                      FUN = prune.misclass) # for classification problem
names(cv.carseats) 
```

```
## [1] "size"   "dev"    "k"      "method"
```

```r
# size: # of leaf
# k: alpha in eq 8.4 (cost for tree complexity)
# dev: cv error rate
cv.carseats
```

```
## $size
## [1] 21 19 14  9  8  5  3  2  1
## 
## $dev
## [1] 74 76 81 81 75 77 78 85 81
## 
## $k
## [1] -Inf  0.0  1.0  1.4  2.0  3.0  4.0  9.0 18.0
## 
## $method
## [1] "misclass"
## 
## attr(,"class")
## [1] "prune"         "tree.sequence"
```

```r
par(mfrow = c(1, 2))
plot(cv.carseats$size, cv.carseats$dev, type = "b")
plot(cv.carseats$k, cv.carseats$dev, type = "b")
```

![](ISLR_files/figure-html/8.3.1-2.png)<!-- -->

```r
# tree with 9 leaves is turned out to be the best tree
# fit the tree explicitly
prune.carseats = prune.misclass(tree.carseats, best = 9) 
# best: # of leaves. result of cost-complexity 

plot(prune.carseats)
text(prune.carseats, pretty = 0)

tree.pred = predict(prune.carseats, Carseats.test, type = "class")
sum(diag(table(tree.pred, High.test))) / sum(table(tree.pred, High.test))
```

```
## [1] 0.775
```

```r
# pruned tree has simpler structure and more accurate prediction
```

![](ISLR_files/figure-html/8.3.1-3.png)<!-- -->

### 8.3.2. Fitting Regression Trees


```r
## fit a regreession tree
library(MASS)
set.seed(1)
train = sample(1:nrow(Boston), nrow(Boston) / 2)
tree.boston = tree(medv ~ ., Boston, subset = train)

summary(tree.boston)
```

```
## 
## Regression tree:
## tree(formula = medv ~ ., data = Boston, subset = train)
## Variables actually used in tree construction:
## [1] "rm"    "lstat" "crim"  "age"  
## Number of terminal nodes:  7 
## Residual mean deviance:  10.38 = 2555 / 246 
## Distribution of residuals:
##     Min.  1st Qu.   Median     Mean  3rd Qu.     Max. 
## -10.1800  -1.7770  -0.1775   0.0000   1.9230  16.5800
```

```r
plot(tree.boston)
text(tree.boston)
```

![](ISLR_files/figure-html/8.3.2-1.png)<!-- -->

```r
## prune
cv.boston = cv.tree(tree.boston)
plot(cv.boston$size, cv.boston$dev, type = "b")
```

![](ISLR_files/figure-html/8.3.2-2.png)<!-- -->

```r
prune.boston = prune.tree(tree.boston, best = 5)
summary(prune.boston)
```

```
## 
## Regression tree:
## snip.tree(tree = tree.boston, nodes = 5L)
## Variables actually used in tree construction:
## [1] "rm"    "lstat"
## Number of terminal nodes:  5 
## Residual mean deviance:  13.69 = 3396 / 248 
## Distribution of residuals:
##     Min.  1st Qu.   Median     Mean  3rd Qu.     Max. 
## -10.1800  -1.9770  -0.1775   0.0000   2.4230  16.5800
```

```r
plot(prune.boston)
text(prune.boston, pretty = 0)
```

![](ISLR_files/figure-html/8.3.2-3.png)<!-- -->

```r
yhat = predict(tree.boston, newdata = Boston[-train, ])
boston.test = Boston[-train, "medv"]
plot(yhat, boston.test)
abline(0, 1)
```

![](ISLR_files/figure-html/8.3.2-4.png)<!-- -->

```r
mean((yhat - boston.test) ^ 2) # MSE
```

```
## [1] 35.28688
```

```r
# here, pruned tree has simpler structure but it has larger MSE
```

### 8.3.3. Bagging and Random Forests

* (8.3.2의 decision tree 결과와 비교해보기)  
* ```randomForest``` 패키지 하나로 충분하다(Bagging은 random forest 중 *m*=*p*인 a special case).


```r
## perform bagging
library(randomForest)
```

```
## randomForest 4.6-14
```

```
## Type rfNews() to see new features/changes/bug fixes.
```

```r
set.seed(1)
bag.boston = randomForest(medv ~ . , data = Boston, 
                          subset = train,
                          mtry = 13, # 구획할 때 샘플수링할 설명변수 개수
                          importance = TRUE)
bag.boston
```

```
## 
## Call:
##  randomForest(formula = medv ~ ., data = Boston, mtry = 13, importance = TRUE,      subset = train) 
##                Type of random forest: regression
##                      Number of trees: 500
## No. of variables tried at each split: 13
## 
##           Mean of squared residuals: 11.39601
##                     % Var explained: 85.17
```

```r
## get test error rate
yhat.bag = predict(bag.boston, newdata = Boston[-train, ])
plot(yhat.bag, boston.test)
abline(0, 1)
```

![](ISLR_files/figure-html/8.3.3-1.png)<!-- -->

```r
mean((yhat.bag - boston.test) ^ 2) 
```

```
## [1] 23.59273
```

```r
# 13.50808 (bagging) vs 26.83413 (a regression tree)

## change the number of tree to grow
bag.boston = randomForest(medv ~ ., 
                          data = Boston,
                          subset = train,
                          mtry = 13,
                          ntree = 25)
yhat.bag = predict(bag.boston, 
                   newdata = Boston[-train, ])
mean((yhat.bag - boston.test) ^ 2) 
```

```
## [1] 23.66716
```

```r
## random forests
set.seed(1)
rf.boston = randomForest(medv ~., 
                         data = Boston,
                         subset = train,
                         mtry = 6,
                         importance = TRUE)

yhat.rf = predict(rf.boston,
                  newdata = Boston[-train, ])
mean((yhat.rf - boston.test) ^ 2)
```

```
## [1] 19.62021
```

```r
# 11.40256 (rf) vs 13.50808 (bagging) vs 26.83413 (a regression tree)

importance(rf.boston)
```

```
##           %IncMSE IncNodePurity
## crim    16.697017    1076.08786
## zn       3.625784      88.35342
## indus    4.968621     609.53356
## chas     1.061432      52.21793
## nox     13.518179     709.87339
## rm      32.343305    7857.65451
## age     13.272498     612.21424
## dis      9.032477     714.94674
## rad      2.878434      95.80598
## tax      9.118801     364.92479
## ptratio  8.467062     823.93341
## black    7.579482     275.62272
## lstat   27.129817    6027.63740
```

```r
# %IncMSE: 그 변수가 없을 때 모델 정확도가 줄어드는 정도(MSE가 증가하는 정도?)
# IncNodePurity: 그 변수가 없을 때 Gini index가 줄어드는 정도(purity가 증가하는 정도)
# node impurity: regression은 RSS로, classification은 deviance로 계산
varImpPlot(rf.boston)
```

![](ISLR_files/figure-html/8.3.3-2.png)<!-- -->

```r
# rm and lstat의 영향이 가장 크더라
```

### 8.3.4. Boosting


```r
## fit a boosted model
library(gbm)
```

```
## Loaded gbm 2.1.5
```

```r
set.seed(1)
boost.boston = gbm(medv ~ ., 
                   data = Boston[train, ],
                   distribution = "gaussian", # binary classification --> "bernoulli"
                   n.trees = 5000, # # of tree to grow
                   interaction.depth = 4) # depth (= # of node layer) of each tree

summary(boost.boston)
```

![](ISLR_files/figure-html/8.3.4-1.png)<!-- -->

```
##             var    rel.inf
## rm           rm 43.9919329
## lstat     lstat 33.1216941
## crim       crim  4.2604167
## dis         dis  4.0111090
## nox         nox  3.4353017
## black     black  2.8267554
## age         age  2.6113938
## ptratio ptratio  2.5403035
## tax         tax  1.4565654
## indus     indus  0.8008740
## rad         rad  0.6546400
## zn           zn  0.1446149
## chas       chas  0.1443986
```

```r
# rel.inf: relative influence

par(mfrow = c(1, 2))
plot(boost.boston, i = "rm")
```

![](ISLR_files/figure-html/8.3.4-2.png)<!-- -->

```r
plot(boost.boston, i = "lstat")
```

![](ISLR_files/figure-html/8.3.4-3.png)<!-- -->

```r
## predict
yhat.boost = predict(boost.boston,
                     newdata = Boston[-train, ],
                     n.trees = 5000)
mean((yhat.boost - boston.test) ^ 2)
```

```
## [1] 18.84709
```

```r
# 10.81479 (boost) vs 11.40256 (rf) vs 13.50808 (bagging) vs 26.83413 (a regression tree)

## manipulate shrinkage parameter
boost.boston = gbm(medv ~ ., 
                   data = Boston[train, ],
                   distribution = "gaussian",
                   n.trees = 5000,
                   interaction.depth = 4,
                   shrinkage = 0.2, # default = 0.001
                   verbose = FALSE)

yhat.boost = predict(boost.boston,
                     newdata = Boston[-train, ],
                     n.trees = 5000)
mean((yhat.boost - boston.test) ^ 2) # vs 10.81479 (wih lambda = 0.001)
```

```
## [1] 18.33455
```

# 9. Support Vector Machines

*Support vector machine* (SVM)

* 1990년대에 컴싸 분야에서 개발했다.
* one of the best "out of the box" classifier. 
    * "out of box": 완제품? 특별한 작업 없이 바로 써먹을 수 있는 classifier.
* *maximal margin classifier*의 일반화 버전
    * *maximal margin classifier*: linear boundary 있을 때만 사용 가능
    * *support vector classifier*: extension
    * *support vector machine*: further extension
* class가 2개인 classification 문제 해결을 위해 만들었다.
* 하지만 2개보다 더 많은 class를 가지는 문제, 심지어 regression에도 적용할 수 있다.

## 9.1. Maximal Margin Classifier

### 9.1.1. What Is a Hyperplane?

* *Hyperplane*: *p*차원 공간에서는 (*p-1*) 차원의 **flat** affine subspace가 된다.
    * affine space: 벡터공간에 점(point)의 개념을 추가한 것. 원점은 따로 존재하지 않음.
    * 예로, 2차원 공간에서는 직선이 되고, 3차원 공간에서는 2차원 평면이 된다.
    * 4차원 이상이면 시각화가 곤란하지만 개념은 똑같다.
* 수식으로는, *$\beta$*~0~+*$\beta$*~1~*X*~*1*~+*$\beta$*~2~*X*~*2*~+...+*$\beta$*~*p*~*X*~*p*~=0을 만족하는 모든 *X*=(*X*~1~, ..., *X*~p~)^*T*^로 쓸 수 있다.
    * Hyperplane은 *p*차원 공간을 두 영역으로 나누게 된다(좌변이 0보다 큰 곳, 작은 곳)
    
### 9.1.2. Classification Using a Separating Hyperplane

* Hyperplane이 만드는 두 구역의 class를 각각 1, -1로 indexing.
* *separating hyperplane*: 한 구역에 한 class만 있게 만드는 hyperplane.
    * *y*~*i*~(*$\beta$*~0~+*$\beta$*~1~*X*~1~+*$\beta$*~2~*X*~2~+...+*$\beta$*~*p*~*X*~*p*~)>0을 만족한다(*y*~*i*는 해당 class의 index).
    * 왜냐햐면 좌변>0인 class는 1로 indexing, 좌변<0인 class는 -1로 indexing하기 때문.
* 좌변 절댓값이 0보다 클수록 hyperplane에서 멀어진다 --> 어느 구역에 속할지 더 쉽게 구분할 수 있다.    

### 9.1.3. The Maximal Margin Classifier

*Maximal margin classifier* (or *optimal separating hyperplane*)

* hyperplane을 하나 찾았다면, 이를 살짝살짝 움직이면서 무수히 많은 놈들을 더 만들 수 있다.
* 이 중 어떤 놈을 선택해야 할까?
* 두 그룹 사이를 아슬아슬하게 스쳐가듯 나누기보다는 최대한 멀찌감치 나누고 싶다.
* hyperplane에서 각 point의 거리를 계산했을 때, 이 거리의 최솟값을 **margin**이라 한다.
* **margin**이 최대인 hyperplane = *maximal margin classifier*
* *p*가 커지면 overfitting하는 경향이 있다.

여기서 *support vector*는 maximal margin에 위치하는 points를 의미한다.

* support: maximal margin hyperplane 선택에 도움을 주기 때문
* vector:  각 point는 *p*차원 공간의 벡터이기 때문


이에 따라 maximual margin hyperplane은 support vector에만 영향을 받게 된다.  
반대로 말하면 support vector 외 다른 점들이 maximal margin 밖 어디를 뛰어댕겨도 hyperplane은 움직이지 않는다.

### 9.1.4. Construction of the Maximal Margin Classifier

the Maximal Margin Classifier를 구할 때 사용하는 세 목적함수

1. maximize *M*
    * margin을 최대화한다. the Maximal Margin Classifier의 정의.
2. 모든 점에서 *y*~*i*~(*$\beta$*~0~+*$\beta$*~1~*X*~*1*~+*$\beta$*~1~*X*~*2*~+...+*$\beta$*~1~*X*~*p*~)>=*M*
3. $\sum_{j = 1}^{p}$$\beta$~*j*~^2^=1
    * 2와 3이 합쳐져서 --> 모든 관측값은 그에 맞는 구역에 위치하고 margin은 *M*이상이어야 한다. 
    * *p*차원 공간의 한 점에서 hyperplane까지 거리를 구하면 분자는 2의 좌변(*y*~*i*~ 제외한), 분모는 sqrt($\sum_{j = 1}^{p}$$\beta$~*j*~^2^)가 된다.
    * 조건 3이 있기 때문에 2의 우변이 *M*일 수 있다(없다면 저 분모 값을 고려해서 우변을 바꿔야겠지?) 

위 세 목적함수를 두고 어찌어찌 최적화 문제를 풀어 hyperplane을 구한다(자세한 건 생략)

### 9.1.5. The Non-separable Case

위 최적화 문제의 해답(=maximal margin classifier)은 커녕   
separating hyperplane 조차 구할 수 없는 경우가 많다.  
\

--> 두 구역을 딱딱 구분하는 것이 아닌 얼추 구분해내는 soft margin을 적용한다.  
--> support vector classifier(m.m.c.를 non-separatable case로 확장) 등을 사용한다.

## 9.2. Support Vector Classifiers

### 9.2.1. Overview of the Support Vector Classifier

Maximal Margin Classifier는 **모든 관측값을 정확하게 분류** 해내려고 한다.  
이런 hyperplane은 존재하기도 힘들뿐더러,  
존재한다고 해도 아래와 같은 특징을 가지는 매우 예민한 놈일 것이다.  

* 관측값 하나하나에 민감하게 반응한다(완벽주의)
* maximal margin이 매우 작아질 수 있다(아슬아슬) --> 불-편
* overfitting 가능성(완벽주의)

따라서  

* **대부분**의 관측값을 잘 분류해내면서 Margin도 일정 값 이상을 유지하는
* 때문에 관측값 하나하나에 쉽게 변하지 않는(덜 민감한, robust)

놈이 필요하다.  
--> *support vector classifier* (or *soft margin classifier*)

### 9.2.2. Details of the Support Vector Classifier

the Support Vector Classifier를 구할 때 사용하는 목적함수

1. maximize *M*
    * margin을 최대화한다.
2. $\sum_{j = 1}^{p}$$\beta$~*j*~^2^ = 1
3. 모든 점에서 *y*~*i*~(*$\beta$*~0~ + *$\beta$*~1~*X*~*1*~ + *$\beta$*~1~*X*~*2*~ + ... + *$\beta$*~1~*X*~*p*~) >= *M*(1-$\epsilon$~*i*~)
4. $\epsilon$~*i*~ >= 0, $\sum_{i=1}^{n}$$\epsilon$~*i*~ <= *C*

Maximal Margin Classifier의 목적함수와 비교

* 1, 2번 조건은 같다.
    * 1번은 margin을 최대화하기 위한 것
    * 2번은 조건 3의 우변을 *M*으로 두기 위한 보조 장치
* 3번 조건은 우변이 M(1-$\epsilon$~*i*~)로 바뀌었고, 4번 조건은 새로 추가됐다.
    * 3번의 $\epsilon$~*i*~은 **slack variable**
    * 4번의 *C*는 **tolerance**

Maximal Margin Classifier 보다 느슨한 classifier를 만들기 위해 tuning parameter *C*(tolerance)를 추가했다.    
hyperplane과 margin을 그어서 데이터를 분류했을 때,

* slack이 0이면 margin 이상의 거리에서 잘 분류한 것 (남방한계선 침범하지 않고 남한에 위치)
* slack이 0보다 크면 margin 미만의 거리에서 잘 분류한 것 (남한측 DMZ에 위치)
* slack이 1보다 크면 잘못 분류한 것 (탈남. 북한 DMZ or 북한 영토 침범)

으로 볼 수 있다.  

*C*는 slack의 budget으로 생각할 수 있다. *C*만큼의 포인트가 있고 slack 값에 따라 포인트가 차감되는 형식이다. 포인트가 0이라면 slack은 모두 0이어야 하고(= Maximal Margin Classifier) 포인트가 많을 수록 더 많은, 혹은 더 값이 큰 slack이 발생할 수 있다. 이런 의미에서 *C*를 SVC의 tolerance라 부르는 것이다.  

Support Vector Classifier에서도 hyperplane을 결정할 때 영향을 미치는 값들을 *support vector*라 하는데 Maximal margin classifier 때와는 대상이 조금 다르다.

* Maximal Margin Classifier: maximal margin에 위치하는 points($\epsilon$ = 0)
* Support Vector Classifier: maximal margin에 혹은 그보다 더 반대 영역에 가까이 위치하는 points ($\epsilon$ >= 0)

*C*가 클 수록 support vector가 더 많아지기 때문에 hyperplane의 variance가 작아지고 bias는 커진다.    
*C*가 작을 수록 support vector가 더 많아지기 때문에 hyperplane의 variance가 커지고,  bias는 작아진다.  
즉, *C*를 이용해 Classifier의 bias-variance trade-off를 조절할 수 있다.  
*C*는 다른 classifier에서 사용한 것처럼 cross-validation으로 추정한다.  

Support vecotr classifier는 전체 관측값 중 일부(support vector)만 사용해 분류하기 때문에 관측치를 모두 사용하는 방법(e.g. linear discriminant analysis)보다는 관측값(또는 이상값)에 덜 민감하다.  

## 9.3. Support Vector Machines

* 9.3.1: non-linear boundary일 때 사용하는 메커니즘 소개
* 9.3.2: 위 메커니즘을 자동화한 방법 소개(SVM)

### 9.3.1. Classification with Non-liinear Decision Boundaries

key = Enlarging the feature space  

* 직선으로 부족하면 곡선을 만든다(2차항, 3차항, ... 추가).
* 목적함수는 변하지 않는다(predictor+계수만 늘어날 뿐)

항을 늘리면 계산량도 부쩍부쩍 는다.

SVM를 이용하면 효율적으로 문제를 해결할 수 있도록 feature space를 결정할 수 있다.

### 9.3.2. The Support Vector Machine

SVM은 feature space를 확장할 때 *kernel*을 이용한다(자세한 계산은 복잡하다. 지금은 feature space를 확장한다는 아이디어를 수행하다고 생각하자).  

Support vector classfier의 목적 함수에는 관측치의 *inner product*외 다른 계산은 포함하지 않았다.  


* inner product = <*x*~*i*~, *x*~*i'*~> = $\sum_{j=1}^{p}$x~*ij*~x~*i'j*~

이는 inner product만으로도 support vector classifier의 목적함수를 표현할 수 있다는 뜻이다.

* *f*(*x*) = $\beta$~0~ + $\sum_{i=1}^{n}$$\alpha$~i~<*x*~*i*~, *x*~*i'*~>

여기서 $\alpha$~i~는 각 관측치마다 부여하는 weighting factor 정도의 의미가 된다.  
<u>support vector가 아니라면</u> hyperplane 결정에 영향이 없으므로 $\alpha$~i~ = 0이 되고,  
<u>support vector에서는</u> 일정 값이 정해진다(원래 식에서는 이 값이 $\beta$ 계수들이 된다).  

$\alpha$~i~를 추정하기 위해서는$\binom{n}{2}$개의 <*x*~*i*~, *x*~*i'*~>를 계산하게 된다.

* margin을 결정하려면 가능한 모든 한 쌍의 관측치 조합마다 거리를 계산해서 비교해야 하기 때문

위의 inner product 관련 항을 **일반화(generalization)**하여 아래와 같이 표현해보자.

* *K*(*x*~*i*~, *x*~*i'*~)

위의 *K*가 바로 *kernel*이다. kernel은 두 관측치가 얼마나 비슷한지(혹은 다른지)를 정량적으로 표현해준다(거리).  
kernel이 inner product 항을 **일반화(generalization)**했다고 표현한 이유는 여러 종류의 inner product 표현이 존재하기 때문이다.  
즉, SVM에 다양한 종류의 kernel을 사용할 수 있다는 의미다.  

* *K*(*x*~*i*~, *x*~*i'*~) = $\sum_{j=1}^{p}$x~*ij*~x~*i'j*~ (linear kernel)
* *K*(*x*~*i*~, *x*~*i'*~) = (1 + $\sum_{j=1}^{p}$x~*ij*~x~*i'j*~)^*d*^ (polynomial kernel)
* *K*(*x*~*i*~, *x*~*i'*~) = exp(-$\gamma$$\sum_{j=1}^{p}$(*x*~*ij*~ - *x*~*i'j*~)^2^) (radial kernel)
    * $\gamma$가 클수록 non-linear

polynomial kernel에서 d가 1이면 linear kernel이 된다(1은 상수항이기 때문에 $\beta$~0~에 흡수된다).  

위와 같이 다양한 kernel을 모두 가질 수 있는 것이 **support vector machine**이고,  
SVM 중 linear kernel을 사용하는 경우(혹은 *d*=1인 polynomial kernel)가 **support vector classifier**인 것이다.

```
SVC와 SVM을 다른 관점에서 설명하는 것 같아 헷갈린다.

support vector classifier에서는 hyperplane에서 support vector까지의 "거리" 개념으로 목적함수가 내포하는 의미를 설명해줬다.

반면 support vector machine에서는 inner product를 이용해 목적함수의 꼴을 설명해줬다.

게다가 
SVC에서는 한 점과 hyperplane까지의 거리를 이용했는데,
SVM에서는 두 점사이의 거리를 다룬다. 하지만 두 점의 거리만 다루지는 않는 것 같다.
xi와 xi'는 두 관측값의 거리였고, x와 xi는 새로운 관측값과 training points 간의 거리였다.
(여기서 training points는 hyperplane(혹은 margin?)을 의미하는 것 같다)

SVM에서도 SVC와 같은 개념(거리와 margin을 비교)이 적용될 수 있다면
SVM의 kernel을 
"두 점 사이의 거리를 표현하는 다양한 종류의 함수"라고 이해하는 게 편할 것 같다.
SVC에서 직선꼴의 hyperplane과 한 점까지의 거리를 계산하는 kernel을 사용한 것처럼
SVM에서는 곡선꼴의 hyperplane과 한 점까지의 거리를 계산하는 (복잡하게 생긴) kernel을 사용한 것이다.
```

### 9.3.3. An Application to the Heart Disease Data

## 9.4. SVMs with More than Two Classes

SVM을 K-class case로 확장하는 방법엔 대표적으로 두 가지가 있다.

* *One-versus-one* (or *all-pairs*) approach
* *One-versus-all* approach

### 9.4.1. One-Versus-One Classification

*K* classes 중 두 개 classes를 선택해서 binary classification한다.

* $\binom{k}{2}$개 SVM을 만든다
* 각 SVM은 *K* classes 중 *k*th, *k'*th class에 대한 two-class setting 문제를 풀게 된다
* $\binom{k}{2}$개 SVM을 가지고 각 관측치를 어느 class로 분류헀는지 투표한다
* 가장 많은 표를 얻은 class가 각 관측치의 최종 분류 결과가 된다

### 9.4.2. One-Versus-All Classification

*K* classes 중 *k*th class를 선택해서 (*k*th class) vs (나머지 *k*-1 classes)에 대해 binary classification한다.

관측치 x를 분류하려 한다면,

* *K*개 SVM을 만든다
* 각 SVM의 kernel에서 계산한 값(=거리) 중 가장 큰 값을 가진 SVM의 class *K*로 분류한다
    * 값이 클 수록 더 안정적으로 해당 class에 속하기 때문

```
본문에서는 linear kernel 수식으로만 서술했는데 그냥 예를 든 거겠지?
```

## 9.5. Relationship to Logistic Regression

SVM이 처음 나온 1990년대에는 hyperplane과 kernel 이용한다는 점이 참신하게 느껴졌다고 한다.  
하지만 SVM은 기존 classical classification approaches와 궤를 같이한다는 점이 밝혀졌다.

support vector classifier의 목적함수는 아래처럼 쓸 수 있다(또?).

* $\beta$~p~에 대해 minimize{ $\sum_{i=1}^{n}$ max[0, 1 - *y*~*i*~*f*(*x*~*i*~)] + $\lambda$$\sum_{j=1}^{p}$$\beta$^2^~j~ }
    * $\lambda$는 variance-bias trade-off를 조절하는 tuning parameter다(SVC의 *C*)

위에서 minimize 안은 **Loss + Penalty** 형태로 이루어져 있다.  
SVM에서 loss는 한 점에서 hyperplane까지의 거리, penalty는 tolerance이다.  
SVM와 같은 loss function을 *hinge loss*라 한다. 여기서 support vector가 아닌 관측값은 loss값이 0이 된다.  

logistic regression, linear discriminant analysis, lasso regression, ridge regression 역시 **Loss + Penalty** 형태로 이루어져 있었다.  
또한 이들 방법에서도 non-linear kernel을 사용할 수 있다. 단지 historical reasons 때문에 non-linear kernel은 SVM에서 더 자주 사용할 뿐이다.  

Logistic regression과 SVC는 비슷한 결과를 보이는 경우가 많은데,  
이들의 *y*~*i*~(*$\beta$*~0~+*$\beta$*~1~*X*~1~+*$\beta$*~2~*X*~2~+...+*$\beta$*~*p*~*X*~*p*~)에 따른 Loss function 값이 비슷하기 때문이다.

* loss가 비슷하다 = 비슷한 범주로 분류한다
* 다만 SVC에서는 support vector가 아니면 loss가 0인 반면,  
logistic regressioin에서는 loss가 0인 경우는 없다).

#### **Support vector regression vs least squares regression**

Loss function이 다르다.

* least squares regression: residual sum of squares를 최소로하는 $\beta$~0~, ..., $\beta$~*p*~
* support vector regression: 특정 값 이상의 절댓값을 가지는 관측치만 loss function에 영향을 미친다(svc와 비슷)

```
support vector regression 좀 자세히 설명해주지 --> 9.6.3에 조금 나온ㄷ
```

## 9.6. Lab: Support Vector Machines

여기서는 ```e1071``` 패키지를 사용한다.    
```LiblineaR``` 패키지도 있는데, predictor가 꽤 많은 상황에서 사용하면 좋다.

### 9.6.1. Support Vector Classifier

svc: ```e1071::svm()```

 * kernel: "linear"일 때는 svm 중에서도 svc가 된다(책에서 소개한 것과는 조금 다른 목적함수를 푼다).
 * cost: tolerance 조절 모수. cost가 작으면 slack이 커지고 support vector가 많아진다.


```r
# make a two-dimensional example data
set.seed(1)
x = matrix(rnorm(20 * 2), ncol = 2)
y = c(rep(-1, 10), rep(1, 10))
x[y == 1, ] = x[y == 1, ] + 1 # add 1 for last 10 data
plot(x, 
     col = (3 - y)) # non-linear boundary 
```

![](ISLR_files/figure-html/unnamed-chunk-1-1.png)<!-- -->

For classification problem,  
class variable should be in **factor type**.


```r
dat = data.frame(x = x, 
                 y = as.factor(y))
library(e1071)
svmfit = svm(y ~ ., 
             data = dat,
             kernel = "linear",
             cost = 10, 
             scale = FALSE) # don't do normalization
plot(svmfit, dat)
```

![](ISLR_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

```r
# cross: support vector
# circle: !(support vector)

# return index of support vector
svmfit$index
```

```
## [1]  1  2  5  7 14 16 17
```

```r
summary(svmfit)
```

```
## 
## Call:
## svm(formula = y ~ ., data = dat, kernel = "linear", cost = 10, scale = FALSE)
## 
## 
## Parameters:
##    SVM-Type:  C-classification 
##  SVM-Kernel:  linear 
##        cost:  10 
## 
## Number of Support Vectors:  7
## 
##  ( 4 3 )
## 
## 
## Number of Classes:  2 
## 
## Levels: 
##  -1 1
```

```r
# cost = 10
# # of support vector = 7 (4 in class "-1")
```

SVC with a smaller cost.  
tolerance가 더 높아지고 margin이 넓어지고 support vector가 더 많아질 것이다.


```r
svmfit = svm(y ~ .,
             data = dat,
             kernel = "linear",
             cost = 0.1,
             scale = FALSE)

plot(svmfit, dat)
```

![](ISLR_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

```r
svmfit$index
```

```
##  [1]  1  2  3  4  5  7  9 10 12 13 14 15 16 17 18 20
```

```r
summary(svmfit)
```

```
## 
## Call:
## svm(formula = y ~ ., data = dat, kernel = "linear", cost = 0.1, scale = FALSE)
## 
## 
## Parameters:
##    SVM-Type:  C-classification 
##  SVM-Kernel:  linear 
##        cost:  0.1 
## 
## Number of Support Vectors:  16
## 
##  ( 8 8 )
## 
## 
## Number of Classes:  2 
## 
## Levels: 
##  -1 1
```

```tune()```: 원하는 모수 값 범위에서 10-fold CV를 수행해준다.

* error: ```tune.control()``` **error.fun**에서 지정한 함수로 에러를 구한다. 이렇게 구한 에러를 **sampling.aggregate**에서 지정한 함수로 요약한다
    * **error.fun** 기본값: classification은 misclassification rate가, regression에서는 MSE가 사용된다
    * **sampling.aggregate** 기본값: mean
* dispersion: ```tune.control()``` **error.fun**에서 지정한 함수로 에러를 구한다. 이렇게 구한 에러를 **sampling.dispersion**에서 지정한 함수로 요약한다
    * **sampling.dispersion** 기본값: sd



```r
set.seed(1)
tune.out = tune(svm, 
                y ~ .,
                data = dat,
                kernel = "linear",
                ranges = list(cost = c(0.001, 0.01, 0.1, 1, 5, 10, 100)))
summary(tune.out)
```

```
## 
## Parameter tuning of 'svm':
## 
## - sampling method: 10-fold cross validation 
## 
## - best parameters:
##  cost
##   0.1
## 
## - best performance: 0.05 
## 
## - Detailed performance results:
##    cost error dispersion
## 1 1e-03  0.55  0.4377975
## 2 1e-02  0.55  0.4377975
## 3 1e-01  0.05  0.1581139
## 4 1e+00  0.15  0.2415229
## 5 5e+00  0.15  0.2415229
## 6 1e+01  0.15  0.2415229
## 7 1e+02  0.15  0.2415229
```

```r
# extract information of the best model 
bestmod = tune.out$best.model
summary(bestmod)
```

```
## 
## Call:
## best.tune(method = svm, train.x = y ~ ., data = dat, ranges = list(cost = c(0.001, 
##     0.01, 0.1, 1, 5, 10, 100)), kernel = "linear")
## 
## 
## Parameters:
##    SVM-Type:  C-classification 
##  SVM-Kernel:  linear 
##        cost:  0.1 
## 
## Number of Support Vectors:  16
## 
##  ( 8 8 )
## 
## 
## Number of Classes:  2 
## 
## Levels: 
##  -1 1
```

```predict()```: 만들어놓은 svm으로 새로운 데이터의 class를 예측(regression에서는 값을 예측)한다.  


```r
set.seed(1)
xtest = matrix(rnorm(20 * 2),
               ncol = 2)
ytest = sample(c(-1, 1), 20, rep = TRUE)
xtest[ytest == 1, ] = xtest[ytest == 1, ] + 1
testdat = data.frame(x = xtest,
                     y = as.factor(ytest))

ypred = predict(bestmod,
                testdat)
table(predict = ypred,
      truth = testdat$y)
```

```
##        truth
## predict -1 1
##      -1  9 3
##      1   2 6
```

```r
# with another cost (0.01)

svmfit = svm(y ~ .,
             data = dat,
             kernel = "linear",
             cost = 0.01,
             scale = FALSE)
ypred = predict(svmfit, testdat)
table(predict = ypred,
      truth = testdat$y)
```

```
##        truth
## predict -1  1
##      -1 10  4
##      1   1  5
```

Linearly separable한 경우


```r
x[y == 1, ] = x[y == 1, ] + 0.5
plot(x, 
     col = (y + 5) / 2,
     pch = 19)
```

![](ISLR_files/figure-html/unnamed-chunk-6-1.png)<!-- -->

이제 linearly separable한 경우가 됐다.  
cost를 높여서(= tolerance를 아주 낮춰서) 아주 철저하게 분류해보자.  


```r
dat = data.frame(x = x,
                 y = as.factor(y))
svmfit = svm(y ~ .,
             data = dat,
             kernel = "linear",
             cost = 1e5)
summary(svmfit)
```

```
## 
## Call:
## svm(formula = y ~ ., data = dat, kernel = "linear", cost = 1e+05)
## 
## 
## Parameters:
##    SVM-Type:  C-classification 
##  SVM-Kernel:  linear 
##        cost:  1e+05 
## 
## Number of Support Vectors:  3
## 
##  ( 1 2 )
## 
## 
## Number of Classes:  2 
## 
## Levels: 
##  -1 1
```

```r
plot(svmfit, dat)
```

![](ISLR_files/figure-html/unnamed-chunk-7-1.png)<!-- -->


training 데이터를 완벽히 분류해냈지만,  
margin이 매우 작다(파란색 support vector와 가장 가까운 동그라미 사이 거리가 매우 가깝다).  
때문에 test error는 높을 수 있다.  
cost를 낮춰보자.


```r
svmfit = svm(y ~ ., 
             data = dat,
             kernel = "linear",
             cost = 1)
summary(svmfit)
```

```
## 
## Call:
## svm(formula = y ~ ., data = dat, kernel = "linear", cost = 1)
## 
## 
## Parameters:
##    SVM-Type:  C-classification 
##  SVM-Kernel:  linear 
##        cost:  1 
## 
## Number of Support Vectors:  7
## 
##  ( 4 3 )
## 
## 
## Number of Classes:  2 
## 
## Levels: 
##  -1 1
```

```r
plot(svmfit,
     dat)
```

![](ISLR_files/figure-html/unnamed-chunk-8-1.png)<!-- -->

분홍색 한 개가 하늘색으로 잘못 분류됐지만, 그 대신 margin이 더 커졌다.  
cost가 매우 높은 경우보다 test error는 더 낮을 것이다!

### 9.6.2. Support Vector Machine

Non-linear kernel을 사용하려면  
```svm()``` 함수의 ```kernel```인자로 "linear"대신 다른 것을 사용한다.  

* "polynomial": ```d```인자를 이용해 다항의 차수를 조절한다
* "radial": ```gamma``인자를 이용해 **$\lambda$**를 조절한다(**$\lambda$**가 작을 수록 선형에 가깝다)


```r
library(e1071)

set.seed(1)
x = matrix(rnorm(200 * 2), ncol = 2)
x[1:100, ] = x[1:100, ] + 2
x[101:150, ] = x[101:150, ] - 2
y = c(rep(1, 150), rep(2, 50))
dat = data.frame(x = x, 
                 y = as.factor(y))
plot(x, col = y) # non-linear boundary
```

![](ISLR_files/figure-html/unnamed-chunk-9-1.png)<!-- -->

```r
train = sample(200, 100)
svmfit = svm(y ~ .,
             data = dat[train, ],
             kernel = "radial",
             gamma = 1,
             cost = 1)
plot(svmfit, dat[train, ])
```

![](ISLR_files/figure-html/unnamed-chunk-9-2.png)<!-- -->

```r
summary(svmfit)
```

```
## 
## Call:
## svm(formula = y ~ ., data = dat[train, ], kernel = "radial", gamma = 1, 
##     cost = 1)
## 
## 
## Parameters:
##    SVM-Type:  C-classification 
##  SVM-Kernel:  radial 
##        cost:  1 
## 
## Number of Support Vectors:  31
## 
##  ( 16 15 )
## 
## 
## Number of Classes:  2 
## 
## Levels: 
##  1 2
```

Cost를 높여보자.

* 더욱 구불구불해지고
* overfitting 가능성이 높아진다


```r
svmfit = svm(y ~ .,
             data = dat[train, ],
             kernel = "radial",
             gamma = 1,
             cost = 1e5)
plot(svmfit, dat[train, ])
```

![](ISLR_files/figure-html/unnamed-chunk-10-1.png)<!-- -->

SVC에서 헀던 것처럼,  
```tune()``` 함수(10-fold cross validation 수행해준다)를 이용해  
최적의 $\lambda$와 cost값을 찾아보자.


```r
set.seed(1)
tune.out = tune(svm,
                y ~ .,
                data = dat[train, ],
                kernel = "radial",
                ranges = list(cost = c(0.1, 1, 10, 100, 1000),
                              gamma = c(0.5, 1, 2, 3, 4)))

help(tune)
```

```
## starting httpd help server ... done
```

```r
summary(tune.out)
```

```
## 
## Parameter tuning of 'svm':
## 
## - sampling method: 10-fold cross validation 
## 
## - best parameters:
##  cost gamma
##     1   0.5
## 
## - best performance: 0.07 
## 
## - Detailed performance results:
##     cost gamma error dispersion
## 1  1e-01   0.5  0.26 0.15776213
## 2  1e+00   0.5  0.07 0.08232726
## 3  1e+01   0.5  0.07 0.08232726
## 4  1e+02   0.5  0.14 0.15055453
## 5  1e+03   0.5  0.11 0.07378648
## 6  1e-01   1.0  0.22 0.16193277
## 7  1e+00   1.0  0.07 0.08232726
## 8  1e+01   1.0  0.09 0.07378648
## 9  1e+02   1.0  0.12 0.12292726
## 10 1e+03   1.0  0.11 0.11005049
## 11 1e-01   2.0  0.27 0.15670212
## 12 1e+00   2.0  0.07 0.08232726
## 13 1e+01   2.0  0.11 0.07378648
## 14 1e+02   2.0  0.12 0.13165612
## 15 1e+03   2.0  0.16 0.13498971
## 16 1e-01   3.0  0.27 0.15670212
## 17 1e+00   3.0  0.07 0.08232726
## 18 1e+01   3.0  0.08 0.07888106
## 19 1e+02   3.0  0.13 0.14181365
## 20 1e+03   3.0  0.15 0.13540064
## 21 1e-01   4.0  0.27 0.15670212
## 22 1e+00   4.0  0.07 0.08232726
## 23 1e+01   4.0  0.09 0.07378648
## 24 1e+02   4.0  0.13 0.14181365
## 25 1e+03   4.0  0.15 0.13540064
```

### 9.6.3. ROC Curves

```ROCR``` 패키지 사용


```r
library(ROCR)

# numerical score (pred)와 class label (truth)를 입력받아
# ROC 커브를 그리는 함수
rocplot = function(pred, truth, ...){
  predob = prediction(pred, truth)
  perf = performance(predob, "tpr", "fpr")
  plot(perf, ...)
}
```

**Support vector regressor와 support vector machine**

* support vector regressor는 *$\beta$*~0~ + *$\beta$*~1~*X*~*1*~ + *$\beta$*~1~*X*~*2*~ + ... + *$\beta$*~1~*X*~*p*~를 predicted value로 사용한다.
* support vector machine은 위 값의 부호를 이용해 class label을 부여한다.
* ```svm()```에 입력하는 response variable이 numeric이면 svr, factor면 svm

```svm()```에서는...  

* decision.values = TRUE로 두면, class가 아닌 fitted value를 얻을 수 있다
* ```predict()``` 결과 중 decision.values 속성에 fitted value가 나타나 있다


```r
svmfit.opt = svm(y ~ .,
                 data = dat[train, ],
                 kernel = "radial",
                 gamma = 2,
                 cost = 1,
                 decision.values = TRUE)
fitted = attributes(predict(svmfit.opt, 
                            dat[train, ], 
                            decision.values = TRUE))$decision.values

rocplot(fitted, dat[train , "y"],
        main = "Training Data")
```

![](ISLR_files/figure-html/unnamed-chunk-13-1.png)<!-- -->

꽤 잘 맞추는 듯하다. 여기서 $\lambda$를 높이면(more non-linear) training fitness를 더 높일 수 있다.  


```r
svmfit.flex = svm(y ~ .,
                  data = dat[train, ],
                  kernel = "radial",
                  gamma = 50,
                  cost = 1,
                  decision.values = TRUE)
fitted.flex = attributes(predict(svmfit.flex,
                                 dat[train, ],
                                 decision.values = TRUE))$decision.values

par(mfrow = c(1, 1))
rocplot(fitted, dat[train , "y"],
        main = "Training Data")
rocplot(fitted.flex, dat[train, "y"],
        add = TRUE, col = "red")
```

![](ISLR_files/figure-html/unnamed-chunk-14-1.png)<!-- -->

$\lambda$를 높였을 때 훨씬 정확한 것처럼 보인다.  
그러나 test error는...


```r
fitted.test = attributes(predict(svmfit.opt,
                                 dat[-train, ],
                                 decision.values = TRUE))$decision.values
fitted.flex.test = attributes(predict(svmfit.flex,
                                      dat[-train, ], 
                                      decision.values = TRUE))$decision.values
rocplot(fitted.test, dat[-train, "y"],
        main = "Test Data")
rocplot(fitted.flex.test, dat[-train, "y"],
        add = TRUE, col = "red")
```

![](ISLR_files/figure-html/unnamed-chunk-15-1.png)<!-- -->

### 9.6.4. SVM with Multiple Classes

Class가 세 개 이상이면 ```svm()```은 기본값으로 one-versus-one approach를 사용한다.


```r
set.seed(1)
x = rbind(x, 
          matrix(rnorm(50 * 2), ncol = 2))
y = c(y, rep(0, 50))
x[y == 0, 2] = x[y == 0, 2] + 2
dat = data.frame(x = x , y = as.factor(y))
par(mfrow = c(1, 1))
plot(x, col = (y + 1))
```

![](ISLR_files/figure-html/unnamed-chunk-16-1.png)<!-- -->

```r
svmfit = svm(y ~ .,
             data = dat,
             kernel = "radial",
             cost = 10,
             gamma = 1)
plot(svmfit, dat)
```

![](ISLR_files/figure-html/unnamed-chunk-16-2.png)<!-- -->

### 9.6.5. Application to Gene Expression Data


```r
library(ISLR)
names(Khan)
```

```
## [1] "xtrain" "xtest"  "ytrain" "ytest"
```

```r
str(Khan)
```

```
## List of 4
##  $ xtrain: num [1:63, 1:2308] 0.7733 -0.0782 -0.0845 0.9656 0.0757 ...
##   ..- attr(*, "dimnames")=List of 2
##   .. ..$ : chr [1:63] "V1" "V2" "V3" "V4" ...
##   .. ..$ : NULL
##  $ xtest : num [1:20, 1:2308] 0.14 1.164 0.841 0.685 -1.956 ...
##   ..- attr(*, "dimnames")=List of 2
##   .. ..$ : chr [1:20] "V1" "V2" "V4" "V6" ...
##   .. ..$ : NULL
##  $ ytrain: num [1:63] 2 2 2 2 2 2 2 2 2 2 ...
##  $ ytest : num [1:20] 3 2 4 2 1 3 4 2 3 1 ...
```

```r
table(Khan$ytrain)
```

```
## 
##  1  2  3  4 
##  8 23 12 20
```

feature 개수(2308)가 train 데이터 개수(63)에 비해 훨씬 많다.  
이런 경우 굳이 non-linear kernel을 사용할 필요 없다.  

* 데이터가 적고 feature가 많으면 hyperplane을 찾기 쉽다(고 한다...).


```r
dat = data.frame(x = Khan$xtrain,
                 y = as.factor(Khan$ytrain))
out = svm(y ~ .,
          data = dat,
          kernel = "linear",
          cost = 10)
summary(out)
```

```
## 
## Call:
## svm(formula = y ~ ., data = dat, kernel = "linear", cost = 10)
## 
## 
## Parameters:
##    SVM-Type:  C-classification 
##  SVM-Kernel:  linear 
##        cost:  10 
## 
## Number of Support Vectors:  58
## 
##  ( 20 20 11 7 )
## 
## 
## Number of Classes:  4 
## 
## Levels: 
##  1 2 3 4
```

```r
table(out$fitted, dat$y) # no training error
```

```
##    
##      1  2  3  4
##   1  8  0  0  0
##   2  0 23  0  0
##   3  0  0 12  0
##   4  0  0  0 20
```

```r
dat.te = data.frame(x = Khan$xtest,
                    y = as.factor(Khan$ytest))
pred.te = predict(out, newdata = dat.te)
table(pred.te, dat.te$y) # test error: 20개 중 2개 틀렸다
```

```
##        
## pred.te 1 2 3 4
##       1 3 0 0 0
##       2 0 6 2 0
##       3 0 0 4 0
##       4 0 0 0 5
```
