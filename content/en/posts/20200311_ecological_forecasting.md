---
title: "Ecological Forecasting"
author: "HoonTaek Lee"
date: 2020-03-11T20:35:43+09:00
lastmod: 2020-03-11T21:39:43+09:00
description:
draft: false
hideToc: false
enableToc: true
enableTocContent: false
tocPosition: inner
tocLevels: ["h2", "h3", "h4"]
tags:
- Book Review
- 2020
---

<img src="https://image.aladin.co.kr/product/9669/22/cover500/0691160570_2.jpg" style="zoom:100%;" />



# Intro

[Near-term Ecological Forecasting Initiative (NEFI) Summer Course 2020](https://ecoforecast.org). 

책 저자이자 보스턴 대학교(Boston University)에 재직중인 Dietze 교수가는 매년 summer course를 진행하고 있다. NEFI 2019에는 선발되지 못했지만, 올해는 고맙게도 나를 초대해줬다.

이 책을 교재로 사용하는데, 가서 잘 배우려면 한 번 예습은 해야 하지 않을까...해서 구입했다.

내 toolbox에 담을 수 있을만한 주제이니 잘 공부해두면 도움이 많이 되겠다. 첫 챕터를 읽어본 결과, 챕터마다 요약도 잘 돼 있고, [Github](https://github.com/EcoForecast/EF_Activities)에 exercise 코드도 정리돼있고, 중간중간 기억해둘만한 표현도 꽤 있다.

이런 책을 쓸 날이 올까.



# 1. Introduction

## 1.1. Why forecast?

> 기후변화와 더불어 생태계 역시 급격히 변하고 있다. 정책 관련 의사결정을 돕고 생태계 변화 이면을 더 잘 이해하기 위한 도구로서 EF가 필요



Decision making & Understanding ecological processes

- We live in an era of rapid and interacting **changes in the natural world**
- Ecological questions about the future status are being asked by **policymakers**
- How do we, as ecologist, provide the best available **scientific predictions**?
- Quantitative tests are at the heart of the scientific method for advancing our knowledge



Capture uncertainties

- Coarse understanding, noisy data, and site-specific dynamics defy our understanding
- Ecological forecasts need to capture these undertainties to be more predictive science



## 1.2. The informatics challenge in forecasting

> EF는 결국 관측 자료를 다루는 일일 것인데, 이는 대부분 생태학자가 미흡한 부분이기에(교육과정) 이 책을 통해 다루려 한다.



- Ecological forecasts may end up being devoted to data management and processing
- The informatics will be leveraged when performing syntheses and making forecasts



## 1.3. The model-data loop

> 데이터로 모델을 맞추고, 
>
> 그렇게 맞춘 모델의 uncertainty 분석을 통해 어떤 데이터가 필요한지 찾고,
>
> 새로 얻은 데이터를 추가해서 새로운 모델을 맞추고
>
> ...



- Forecasting the future status of real systems **requires data** about thos systems
- The model-data loop refers to the idea of **iteratively using data to constrain models and  then using models to determine what new data is most needed**
- The model-data loop applies **regardless of the complexity** of the model



## 1.4. Why Bayes?

> Bayes는 사전확률 설정 -> 데이터 추가 -> 사전확률 조정(=사후확률)의 과정을 거치는데,
>
> 이것이 the model-data loop idea와 흡사하다



The Bayesian approach

- allows us to treat **all the terms** in a forecast as probability distributions
- is able to **update predictions** as new data becomes available
- tends to be flexible and robust, **allowing us to deal with the complexity of real-world data** and to forecast with relatively complex models.



## 1.5. Models as scaffolds

> 여기저기서 데이터가 쏟아지고 있는데 서로 측정 방법, 측정 스케일, 방법, 가정, 목표하는 process (증발산 vs 증발), 등 같은 분야에서도 서로 다른 점이 너무 많다.
>
> 이 데이터들을 통합하는 데 model이 가교(scaffold) 역할을 할 수 있다.
>
> Model을 이용해 여러 data를 통합하면서 model-data loop idea를 실현 --> models as scaffold approach



Three modeling approaches:

1. Forward modeling: use observed inputs to generate output sets
2. Inverst modeling: use observations of model outputs to infer the most likely inputs
3. Model as scaffold: use models and data together to constrain estimates of different ecosystem variables
   - Different data sets may not be directly comparable to one another (scales, assumptions, target processes, ...), **but may all be comparable to the model**
   - Combining data and models is a fundamentally data-driven exercise



## 1.6. Case studies and decision support

> 연구용 EF와 Decision support는 다른 문제.
>
> Decision support는 
>
> 생태계에 대한 이해가 선행되야 하고
>
> value, trade-offs 등 가치판단이 추가된다.
>
> 때문에, 책 후반부에 다룰 예정



Prediction vs. Projection

- Prediction: probabilistic forecasts **based on current** trends and conditions
- Projection: probabilistic forecasts driven **by explicit scenarios**



# 2. From models to forecasts

