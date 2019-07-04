# Instant-Gratification
kaggle Top6% (95th of 1836) 🥉
![캡처](https://user-images.githubusercontent.com/30254394/60252574-6df26880-9905-11e9-852e-4378182cbc27.PNG)
# Summary of Instant Gratification
## useful
>[BaseLine](https://github.com/ph1545/Instant-Gratification/blob/master/useful/BaseLine%20%20%5Bcv%20scores%20%3D%200.537%5D.ipynb)  [cv scores = 0.537]

- LGBoost 피쳐중요도 그린 결과 'wheezy-copper-turtle-magic'변수의 중요도가 매우높아 탐색결과 'wheezy-copper-turtle-magic'변수만 정수값을 가지고 있었음. EDA를 통해 'wheezy-copper-turtle-magic' 변수와 다른 변수간의 상호작용을 [탐색](https://github.com/ph1545/Instant-Gratification/blob/master/EDA/wheezy-copper-turtle-magic%20EDA.ipynb)해봄
>[LogisticRegression](https://github.com/ph1545/Instant-Gratification/blob/master/useful/LogisticRegression%5Bcv%20scores%20%3D%200.803%5D.ipynb) [cv scores = 0.803]

- eda 를 통하여 발견한 'wheezy-copper-turtle-magic'변수를 독립적으로 모델을 만들어
다른 변수들과 상호작용, 스코어가 향상.

>[Feature Selection](https://github.com/ph1545/Instant-Gratification/blob/master/useful/Feature%20Selection%20%5Bcv%20scores%20%3D%200.804%5D.ipynb) [cv scores = 0.804]

- 독립모델을 만들경우 약 500개의 로우와 255개의 피처가 있어  [차원의저주](https://www.kaggle.com/c/instant-gratification/discussion/93379) 즉 과적합에 빠질 수 있습니다. 적은 피처로도 비슷한 성능을 내는 방법을 찾아야 했고 분산이 1.5 이상인 피처들이 예측력이 있음을 [찾았습니다](https://www.kaggle.com/fchmiel/low-variance-features-useless).

>[Nonliear Model(NuSVC)](https://github.com/ph1545/Instant-Gratification/blob/master/useful/nonliear%20model(NuSVC)%20%5Bcv%20scores%20%3D%200.943%5D.ipynb) [cv scores = 0.943]

- 다양한 모델시도(비선형 모델이 높은점수를 얻음)
1. LR [cv scores = 0.804]
2. KNN [cv scores = 0.907]
3. SVC [cv scores = 0.919]
4. NuSVC [cv scores = 0.943]
5. MLP [cv scores = 0.910]

>[StandardScaler](https://github.com/ph1545/Instant-Gratification/blob/master/useful/StandardScaler%20%20%5Bcv%20scores%20%3D%200.953%5D.ipynb)  [cv scores = 0.953]

- 비선형 모델NuSVC에 StandardScaler 적용

>[QDA](https://github.com/ph1545/Instant-Gratification/blob/master/useful/QDA%20%5Bcv%20scores%20%3D%200.964%5D.ipynb) [cv scores = 0.964]

- 높은 스코어를 기록하는 Quadratic Discriminant Analysis모델을 Vladislav가 [공개](https://www.kaggle.com/speedwagon/quadratic-discriminant-analysis) Chris Deotte가 QDA를 [설명](https://www.kaggle.com/c/instant-gratification/discussion/93843#latest-555637)
- QDA가 높은스코어를 얻은 이유는 데이터가 다변량 가우스분포를 따르며 이러한 가정에서 매우 효과적인 모델이기 때문
>[Ensemble Models_XGBoost](https://github.com/ph1545/Instant-Gratification/blob/master/useful/Ensemble%20Models_xgboost%20%5Bcv%20scores%20%3D%200.967%5D.ipynb) [cv scores = 0.967]

- 앙상블 구성모델
1. KNN [cv scores = 0.902]
2. SVC [cv scores = 0.950]
3. NuSVC [cv scores = 0.960]
4. MLP [cv scores = 0.908]
5. QDA [cv scores = 0.965]

>[Pseudo Labeling](https://github.com/ph1545/Instant-Gratification/blob/master/useful/Pseudo%20Labeling%20%20%5Bcv%20scores%20%3D%200.970%5D.ipynb)  [cv scores = 0.970]

- Pseudo Labeling 이란 확실하게 예측된 test데이터를 train데이터에 포함시켜 훈련하는것을 말합니다.
- Pseudo Labeling결과 AUC 0.003상승

>[Ensemble Models_XGBoost](https://github.com/ph1545/Instant-Gratification/blob/master/useful/%5BEnsemble%20Models_XGBoost%5D%5Bcv%20scores%20%3D%200.9717%5D%5Bprivate%20%3D%200.972%5D.ipynb)[cv scores = 0.9717][private = 0.972]

>[1% solution](https://github.com/ph1545/Instant-Gratification/blob/master/useful/top%201%25%20solutions%5Bprivate%20%3D%200.9744%5D.ipynb) 

-이번 comp의 핵심모델은 GMM이었습니다. 데이터가 make_classification을 통해 생성되었고 n_clusters_per_class=3이라는 것을 알아야만 했습니다.


- 앙상블 구성모델
1. SVC [cv scores = 0.950]
2. NuSVC [cv scores = 0.960]
3. GMM [cv scores = 0.968]
4. QDA + Pseudo [cv scores = 0.970]
## try
- 반올림 
- unique_value_count 변수 생성 
- catergorial + NN, Lgboost, xgboost
- VarianceThreshold
- RobustScaler + VarianceThreshold + model(NuSVC, QDA, LR, MLP, KNN, SVC, LDA, GPC)
- StandardScaler + VarianceThreshold + model(NuSVC, QDA, LR, MLP, KNN, SVC, LDA, GPC)
- StandardScaler + PCA + model(NuSVC, QDA, LR, MLP, KNN, SVC, LDA, GPC)
- RobustScaler + PCA + model(NuSVC, QDA, LR, MLP, KNN, SVC, LDA, GPC)
- PolynomialFeatures + StandardScaler + VarianceThreshold + model(NuSVC, QDA, LR, MLP, KNN, SVC, LDA, GPC)
- PolynomialFeatures + RobustScaler+ VarianceThreshold + model(NuSVC, QDA, LR, MLP, KNN, SVC, LDA, GPC)
- StandardScaler + PolynomialFeatures + VarianceThreshold + model(NuSVC, QDA, LR, MLP, KNN, SVC, LDA, GPC)
- RobustScaler + PolynomialFeatures + VarianceThreshold + model(NuSVC, QDA, LR, MLP, KNN, SVC, LDA, GPC)

## Learning
- [Data Structure](https://www.kaggle.com/cdeotte/support-vector-machine-0-925) : Chris Deotte discover Variables are not Gaussian

- [Adversarial Validation](https://github.com/ph1545/Instant-Gratification/blob/master/Adversarial%20validation/Adversarial%20validation.ipynb) : test데이터와 train데이터는 같은 분포에서 나온데이터 확인. [참고](https://github.com/ph1545/concept-study/blob/master/Adversarial%20validation%20part1.ipynb)

- make_classification : mhviraf가 make_classification통해 Synthetic data생성 real데이터와 비슷한 AUC를 얻음

- [QDA](https://www.kaggle.com/c/instant-gratification/discussion/93843#latest-555637)

- VarianceThreshold : 분산에 의해 특성을 선택한다.

- GMM : Gaussian Mixture Model의 약자로 이번 우승 솔루션의 핵심 개념이다.

- QLR(Quadratic logistic regression) : 이 모델은 QDA와 같은 quadratic boundary를 가지게 하는 변수와 logistic regression이 합쳐진것을 의미한다 예) PolynomialFeatures + LR


## top10 kernel 
please upvote after click
- [1th](https://www.kaggle.com/infinite/v2-all-gmm)
- [2th](https://www.kaggle.com/qiaoshiji/asdfghjkl)
- [3th](https://www.kaggle.com/zaharch/instant-success-gmm)
- [4th](https://www.kaggle.com/rsakata/gmm-with-target-perfect-pred-random-shuffle)
- [5th](https://www.kaggle.com/waylongo/5th-solution)
- [6th](https://www.kaggle.com/c/instant-gratification/discussion/96496)
- [7th](https://www.kaggle.com/cdeotte/3-clusters-per-class-0-975)
- [8th](https://www.kaggle.com/merkylove/10th-public-8th-private-solution)
- [9th](https://www.kaggle.com/yassertabandeh/ingr09)
- [10th](https://www.kaggle.com/raghaw/my-gratification-v2-10th-place-on-public-lb)
