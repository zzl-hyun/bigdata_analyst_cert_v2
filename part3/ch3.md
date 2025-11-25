# Part3 

## Ch1. 가설검정
### 단일 표본 검정
- t-test(t검정) ttest_1samp()
  - 양측검정
  - 단측검정(greater)
  - 단측검정(less)
### 대응 표본 검정
- ttest_rel()
  - 양측
  - 단즉(greater)
  - 단측(less)
### 독립 표본 검정
- ttest_ind

## Ch2. 분산분석
### 일원 분산 분석
- f_oneway()
- ols
### 이원 분산 분석
- ols
- anova_lm
- 
## Ch3. 카이제곱 검정
### 적합도 검정
- chisquare
### 독립성 검정
- chi2_contingency
### 동질성 검정
- chi2_contingency

## Ch4. 회귀 분석
### 상관 계수
- df.corr()
### 단순 선형 회귀 분석
- ols
### 다중 선형 회귀 분석
- ols
### 범주형 변수
- ols

## Ch5. 로지스틱 회구 분석
### 로지스틱 회귀 분석
- logit
### 오즈와 오즈비
- Odds: P(A) / 1-P(A)
- Odds Ratio: Odds(A) / Odds(B)