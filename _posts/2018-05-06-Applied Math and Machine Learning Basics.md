---
title: (2) Part1 : Linear Algebra 진행중..
date: 2018-05-05 23:29:08
categories:
- deep learning book
tags: deeplearning
---

안녕하세요. 데이터를 공부하고 있는 BEENSUN입니다.
이번 포스트 부터 `Part1 : Applied Math and Machine Learning Basics` 에 대해서 자세하게 다루어 보겠습니다. Part1에서는 딥러닝을 이해하는데 필요한 기본 수학 개념과 기본적인 머신러닝 개념을 소개합니다.

오늘은 Part1의 첫 번째 주제인 `Linear Algebra`입니다.
*포스트를 하면서 제 나름대로 정리하기 때문에 본문과 내용이 다를 수 있습니다. 컴퓨터로 포스팅하기 어려운 부분은 부분적으로 스킵하고 있습니다*

## Chapter 2 : Linear Algebra (선형대수학)

 선형대수학은 과학과 공학 전반에 걸쳐 널리 사용되는 수학의 한 분야합니다. 선형대수학에 대한 올바른 이해는 많은 기계학습 알고리즘, 특히 딥러닝 알고리즘을 이해하고 작동시키는데 필수적입니다. 선형대수학에 대한 개념을 알고계시다면 스킵하셔도 됩니다.

> 선형대수학은 벡터 공간, 벡터, 선형 변환, 행렬, 연립 선형 방정식 등을 연구하는 대수학의 한 분야이다.

### Scalars, Vectors, Matrices and Tensors

- Scalars : 스칼라는 단일 숫자입니다. 벡터 공간에서 벡터를 곱할 수 있는 양.
- Vectors : 벡터는 숫자의 배열입니다. 크기가 n×1(열벡터) 과 1×n(행벡터)인 행렬을 말합니다. 벡터는 공간에서 점을 식별하는 것으로 생각할 수 있습니다.
- Matrices : 행렬은 2 차원 숫자 배열이므로 각 요소는 단 하나가 아닌 두 개의 인덱스로 식별됩니다. 행은 세로, 열을 가로를 나타냅니다.
- `Tensors` : 텐서는 쌍대 공간의 개념을 일반화한 것이라고 할 수 있습니다. 쌍대공간이란 선형범함수들의 모임인데 일반적인 경우, 가변 수의 축이있는 일반 그리드에 배열 된 숫자 배열을 텐서라고합니다.
*간단히 말하면 다중선형함수라는데 아직 저는 이해하기는 어려운 단계인 것 같습니다.*
- transposed matrix : 전치행렬은 행과 열을 교환하여 얻는 행렬입니다. 주 대각선을 툭으로 하는 반사 대칭을 가하여 얻는 행렬입니다. 기호로는 A<sup>T</sup> 입니다.

### Multiplying Matrices and Vectors

 선형대수학의 곱과 전치행렬의 연산과정을 다루고 있습니다.(스킵)

### Indentity and Inverse Matrices

- 단위행렬 : 행렬의 대각 원소는 모두 1, 대각 원소가 아닌 원소들은 모두 0으로 이루어진 행렬입니다. 단위행렬은 어떠한 행렬에 곱하더라고 자기 자신이 나온다는 성질을 가지고 있습니다.
- 역행렬 : 임의의 행렬 A에 대하여 A<sup>-1</sup>로 표현하며, 곱하면 단위행렬이 나오는 행렬입니다. 교환법칙이 성립합니다.

### Linear Dependence and Span

참고영역
Lorem <sup>superscript</sup> dolor <sub>subscript</sub> amet, consectetuer adipiscing elit. Nullam dignissim convallis est. Quisque aliquam. <cite>cite</cite>. Nunc iaculis suscipit dui. Nam sit amet sem. Aliquam libero nisi, imperdiet at, tincidunt nec, gravida vehicula, nisl. Praesent mattis, massa quis luctus fermentum, turpis mi volutpat justo, eu volutpat enim diam eget metus. Maecenas ornare tortor. Donec sed tellus eget sapien fringilla nonummy. <acronym title="National Basketball Association">NBA</acronym> Mauris a ante. Suspendisse quam sem, consequat at, commodo vitae, feugiat in, nunc. Morbi imperdiet augue quis tellus.  <abbr title="Avenue">AVE</abbr>
