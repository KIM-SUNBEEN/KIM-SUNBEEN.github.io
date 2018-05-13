---
title: 시계열 분석(Time Series Analysis)
date: 2018-05-13 23:29:08
categories:
- R
tags: timeSeries
---

안녕하세요. 시계열분석을 공부해보려 합니다.

## 참고문헌
> [시계열 분석 강의](https://www.youtube.com/watch?v=U_CHoMjaOSE&list=PLvCgf6iu6Pq2qKK1YgMUgzpnkmrKcLd7O)

> [시계열분석 평활법](https://vmfhxor1234.wordpress.com/2017/08/10/aa/)


## 시계열 분석

### 시계열 분석의 정의

- `시계열` : 일반적으로 어떤 양의 관측경ㄹ과를 일정한 기준에 따라 계열로 정리 한 것을 통계계열이라고 한다. 어떤 관측치 또는 통계량의 변화를 시간의 움직임에 따라서 포착하고 이것을 계열화 한것을 시계열이라 한다.
- `시계열 분석` : 시계열 데이터는 여러 원인에 기인한 변동이 포한되어 있다. 이 변동들을 우연변동(불규칙변동), 계절변동, 구조변동, 순환변동 등이라고 부른다. 이런 변동 부분들을 분리하고 분석하는 것을 시계열 분석이라고 한다.
- `정상성` : 정상성은 시점에 상관없이 시계열 특성이 일정하다는 것을 의미하며, 다음을 만족해야한다.
  1. 평균이 일정하다.
  2. 분산이 시점에 의존하지 않는다.
  3. 공분산은 단지 시차에만 의존하고 시점 자체에는 의존하지 않는다.

위의 3가지 항목 중 하나라도 만족하지 못하면 비정상 시계열이라 부릅니다. 그래서 대부분의 시계열 자료는 비정상이죠. 때문에 시계열 자료를 분석하기에 앞서서 시계열 자료가 정상성을 만족하는지 판단해야한다.

### 추세분석(Trend Analysis)

추세(Trend) 어떤 현상이 일정한 방향으로 나아가는 경향이다. 일정한 방향이란 것은 `증가` 또는 `하락`으로 나뉜다.

추세는 선형(Linear Model), 2차(Quadratic Model), 지수 성장(Exponential Growth Model), S-곡선(S-Curve Model)로 4가지 종류가 있다. 추세는 미래를 예측할 수 있는데 도움이 된다.  

| 유형 | 모형 |
| 선형(Linear Model) | Y<sub>t</sub> = B<sub>0</sub> + B<sub>1</sub>t + e<sub>t</sub> |
| 2차(Quadratic Model) | Y<sub>t</sub> = B<sub>0</sub> + B<sub>1</sub>t + B<sub>2</sub>t<sup>2</sup> + e<sub>t</sub>|
| 지수 성장(Exponential Growth Model) |Y<sub>t</sub> = B<sub>0</sub>B<sub>1</sub><sup>t</sup> + e<sub>t</sub> |
| S-곡선(S-Curve Model) | Y<sub>t</sub> = 10<sup>a</sup> /(B<sub>0</sub> + B<sub>1</sub>B<sub>2</sub><sup>t</sup>) + e<sub>t</sub> |


예측을 얼마나 잘 예측했는지 확인하는 척도 3가지!
- MSD : 실제값과 예측값의 차이의 제곱을 개수로 나눔
- MAD : 실제값과 예측값 차이의 평균
- MAPE : MAD의 백분율

### 분해(Decomposition)

시계열에 영향을 주는 일반적인 요인을 시계열에서 분리해 분석하는 방법이며, 회귀분석적인 방법을 주로 사용합니다. 시계열을 구성하는 요소는 다음과 같이 4가지로 분류합니다.

- 추세요인 : 자료가 특정한 형태를 취할 때, 추세요인이라 한다.
- 계절요인 : 고정된 주기에 따라 자료가 변화할 경우 계절요인이라 한다.
- 순환요인 : 알려지지 않을 주기를 가지고 자료가 변화할 때 순환요인이라 한다.
- 불규칙요인 : 3가지 요인으로 설명할 수 없는 회귀분석에서 오차에 해당하는 요인을 불규칙 요인이라 한다.

분해라는 분석법을 진행하려면 승법모델과 가법모델이라는 것이 있습니다. `승법모델`이란 시간에 따라 진폭이 점점 증가하는 경우입니다. `가법모델`은 계절변동의 진폭 추세의 증가 또는 감소레 따라 일정한 경우입니다.

#### 승법모델(Multiplicative Model)

 **(단계1)** 최소제곱법을 이용한 추세선 적합(직선 식을 만듦)

  오차가 최소가 되는 선형식을 만든다.

 **(단계2)** 계절성분 얻기1 : 추세 제거(Detrend)

  계절성분을 얻는 다는 것을 주기의 진폭을 예측할 수 있다는 것이다. 계절성분과 추세선을 안다면 추세선으로 예측한 값에서 계절성의 진폭을 더해 좀 더 예측을 정확하게 할 수 있다.추세선을 제거하는 방법으로는 단계1에서 그린 추세선을 1로 생각하고 추세선을 기준으로 실제값과 비교하여 추세를 제거할 수 있다.

 **(단계3)** 계정성분 얻기2 : 평활화(Smoothing)

  평활화는 평평하게 만든다라고 생각하면 되는데 여러가지 방법이 있습니다. 단일이동평균, 중심이동평균, 이중이동평균, 단일지수평활, 이중지수평활, Winters방법 등이 있다.

 **(단계4)** 계절변동지수 얻기

  평활화된 값에서 주기마다 중앙값을 추출한 후에 평균을 낸다. 그 후에 주기마다 상대적인 값을 내는데 한 주기 내에서 다른 주기들과의 상대적인 값을 계절변동지수라고 합니다.

 **(단계5)** 필요 시 Deseasoned Data 얻기

  계절변동지수를 제거해주고 싶다면 이 방법을 사용한다.

 **(단계6)** 예측

  예측값(Z) = 주세성분(T) * 계절성분(S) * 불규칙성분(I)

#### 가법모델(Additive Model)

**(단계1,2)**  추세 방정식(회귀방정식)을 통한 적합값과 Detreded Data

  승법모델과는 조금 다른 계산식이 적용되는데 상대적인 값이 아닌 실제값에서 적합값을 빼줌으로 추세를 제거한다.

**(단계3)** 계절성분 얻기 : 평활화(Smoothing)

  평활화 자료도 Detrend value에서 평균값을 빼줌으로 구한다.

**(단계4)** 계절변동지수 얻기, 필요시 Deseasoned Data 얻기

  계절별 중앙값에서 주기의 평균을 빼줌으로 계절변동지수를 구한다.

**(단계5)** 예측

 예측값(Z) = 주세성분(T) + 계절성분(S) + 불규칙성분(I)


== 진행중 ==




### 목차

 - 시계열 그림(Time Series Plot)
 - 추세분석(Trend Analysis)
 - 분해(Decomposition)
 - 이동평균(Moving Average)
 - 단일지수 평활(Single Exponential Smoothing)
 - 이중지수 평활(Double Exponential Smoothing)
 - Winters의 방법(Holt-Winters Method)
 - 자기상관이 있는 경우의 처리

### Linear Dependence and Span

참고영역
Lorem <sup>superscript</sup> dolor <sub>subscript</sub> amet, consectetuer adipiscing elit. Nullam dignissim convallis est. Quisque aliquam. <cite>cite</cite>. Nunc iaculis suscipit dui. Nam sit amet sem. Aliquam libero nisi, imperdiet at, tincidunt nec, gravida vehicula, nisl. Praesent mattis, massa quis luctus fermentum, turpis mi volutpat justo, eu volutpat enim diam eget metus. Maecenas ornare tortor. Donec sed tellus eget sapien fringilla nonummy. <acronym title="National Basketball Association">NBA</acronym> Mauris a ante. Suspendisse quam sem, consequat at, commodo vitae, feugiat in, nunc. Morbi imperdiet augue quis tellus.  <abbr title="Avenue">AVE</abbr>

<div id="---" class="section level1">
<h1>크기가 가장 큰 제목</h1>
<div id="-2--" class="section level2">
<h2>크기가 2번째로 큰 제목</h2>
<div id="-5--" class="section level5">
<h5>크기가 5번째로 큰 제목</h5>
<p>본문내용은 이런식으로 메모가 가능해. 궁극적으로 데이터분석 코딩이라는 것은 보고서를 작성하는 일이기 때문.</p>
</div>
<div id="-" class="section level3">
<h3>1. 패키지 설치</h3>
<pre class="r"><code>#1. dplyr
# install.packages(&quot;dplyr&quot;) #데이터 전처리 패키지 =&gt; upgarde 버젼 data.table 패키기 20배가 빠름
#
# #2. reshape2
# install.packages(&quot;reshape2&quot;) #데이터테이블 모양을 조직
#
# #3. stringr
# install.packages(&quot;stringr&quot;) #문자열을 다루는 패키지

# 패키지를 사용할 때,
require(dplyr)
library(reshape2)
require(stringr)

# 4. needs  = 패키지 인스톨 &amp; 사용을 동시에 할 수 있는 패키지
#install.packages(&quot;needs&quot;)
require(needs)

#needs(dplyr,reshape2,stringr)</code></pre>
</div>
<div id="-" class="section level3">
<h3>2. 데이터 인포트</h3>
<pre class="r"><code>#1. 상대주소
train &lt;- read.csv('train.csv') #train이라는 변수에 저장

#2. 절대주소
test  &lt;- read.csv('C:/Users/SUNBIN/public/Desktop/datastudy/data/test.csv')  #test라는 변수에 저장</code></pre>
</div>
<div id="r--class-----" class="section level3">
<h3>3. R의 제공 변수(class) - 데이터 타입을 확인하자</h3>
<pre class="r"><code>num &lt;- c(1,2,3) # num이라는 변수에 벡터형태로 1,2,3을 저장
num # print하는 방법</code></pre>
<pre><code>## [1] 1 2 3</code></pre>
<pre class="r"><code>#1. 숫자형 타입
num&lt;- c(1:10) # 1부터 10까지 저장

#2 문자형 타입
str&lt;- c(&quot;수호&quot;,&quot;명철&quot;,&quot;형준&quot;,&quot;선빈&quot;)

#3 논리형 타입
bool&lt;- c(T,F,FALSE,TRUE)

#4 Factor 타입
fac&lt;- as.factor(c(1,0,1));fac</code></pre>
<pre><code>## [1] 1 0 1
## Levels: 0 1</code></pre>
</div>
<div id="--" class="section level3">
<h3>4. 데이터프레임 생성 &amp; 형변환</h3>
<pre class="r"><code>#1. 형변환
# 1-1 문자로 변환
chageTochr &lt;- as.character(num)

# 1-2 숫자로 변환
chageTonum &lt;- as.integer(chageTochr)
chageTonum &lt;- as.numeric(chageTochr)

# 1-3 factor로 변환
num&lt;- c(1,3,5,7,9)
chageTofac &lt;- as.factor(num)
num &lt;- as.integer(as.character(chageTofac))

# 1-4 데이터프레임 형태로 변환
chageTodf&lt;- as.data.frame(str)</code></pre>
</div>
</div>
</div>
