# Part3 

## Ch1. 가설검정
### 단일 표본 검정
단일 모집단 - 어떤 집단의 평균이 특정 갓과 유의미하게 다른지를 검정하는 통계 방법이다!
평균이 이거라고 알려졌는데 내가볼땐 아닐 때 
- t-test(t검정) ttest_1samp()
  - 양측검정
  - 단측검정(greater)
  - 단측검정(less)

- 정규성을 만족하는가 scipy.stats.shapiro(data)
  - 정규성 만족(p_value > 0.05) -> 단일 표본 t검정(평균)
    - scipy.stats.ttest_1samp(data, H0 기대값, alternative)
  - 정규성 불만족(p_value < 0.05) -> Wilcoxon의 부호 순위 검정(중앙값)
    - scipy.stats.wilcoxon(data - H0 기대값, alternative)
  
### 대응 표본 검정
단일 모집단 - 사전,사후 표본을 추출 -> 시간차를 뒀을 때 평균 차이가 있는가?
교육, 신약 등의 효과가 유의미한지 확인할 때
- ttest_rel()
  - 양측
  - 단즉(greater)
  - 단측(less)
  - 
- 정규성을 만족하는가 scipy.stats.shapiro(diff)
  - 정규성 만족(p_value > 0.05) -> 단일 표본 t검정(평균)
    - scipy.stats.ttest_rel(a, b, alternative)
  - 정규성 불만족(p_value < 0.05) -> Wilcoxon의 부호 순위 검정(중앙값)
    - scipy.stats.wilcoxon(a, b, alternative)

### 독립 표본 검정
단일 모집단 - 독립적인 표본 2개 추출 -> 두 표본간 평균이 서로 다름을 판단하는 방법!
A반 성적이  B반 성적보다 높다?낮다?다르다?
- ttest_ind
- 정규성 만족? stats.shapiro(data1), stats.shapiro(data2)
  - 정규성 만족 (p_value > 0.05)
    - 등분산성 만족? stats.levene(a, b)
      - 등분산성 만족 (p_value > 0.05) -> 독립 표본 검정 ttest_ind(a, b, equal_val=True)
      - 등분산성 불만족 (p_value < 0.05) -> welch의 t 검정 ttest_ind(a, b, equal_val=False)
    - 정규성 불만족 
      - mannwhitenyu(a, b, alt)

## Ch2. 분산분석
### 일원 분산 분석
집단을 나누는 요인이 1개고 집단이 3개 이상일 때 집단간 평균이 다른지 봄
기본 가정 1. 독립성, 2. 정규성(shapiro), 3. 등분산성(levene) 
- f_oneway()
shapiro(df['A']), shapiro(df['B'])
levene(df['A'], df['B'])
stats.f_oneway()


- ols
statsmodels.formula.api ols
statsmodels.stats.anova anova_lm
ols('종속 ~ C(독립)', df)
### 이원 분산 분석
- ols, anova_lm
- ols('종속 ~ C(A) + C(B) + C(A):C(B)', df).fit()

## Ch3. 카이제곱 검정
### 적합도 검정
관찰빈도가 기대빈도 분포를 따르고 있는지
- chisquare(observed, expected)

### 독립성 검정
두 변수가 서로 연관있는지 연관 없는지(독립)
1. 교차표 생성 -> pd.crosstab(df['X'], df['Y'])
- chi2_contingency(교차표)

### 동질성 검정
서로다른 2개 이상의 집단들의 분산&비율이 동일한지
- chi2_contingency(교차표)
1. 교차표 생성 -> pd.crosstab(df['X'], df['Y'])

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