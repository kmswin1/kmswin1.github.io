---
layout: page
title: NLP
permalink: /NLP/
---


<h1> NLP Papers </h1>

<h3> Subject : Stronger baselines for trustable results in Neural machine translation </h3> <br>
<h5> Abstract <h5> <br>
  NMT 모델에 대하여 정확한 성능 평가를 위한 제대로 된 기준이 필요할 것이고 우리가 제시해볼게 !!<br>

<h5> Intro & Experiment </h5> <br>
<p>
i) Adam 과 Learning rate scheduling을 여러 번 시도! -> To find global minima fastly. <br>
ii) Byte-pair encoding 사용 -> To increase voca <br>
iii) Ensemble method 사용 -> 96% -> 98% (To remove bias) <br>
iv) 보통 기법 보다 BLUE score 5 넘게 증가!! <br>
  </p>

<h5> Further Trustable Evaluation </h5>
<p>
i) Dropout : standard 0.5 -> 0.2 : 성능 더 좋음<br>
ii) Lexicon bias : Sentiment analysis 같은 classification 문제는 lexicon 만들 때, 미리 실수 값 부여 (BAT 가 더 향상 된 모델) <br>
iii) Pre- translate : Phrase based machine translation
rare 한 voca 를 다룰 때 사용, input -> pbmt (concat) -> output -> nmt -> 최종 아웃풋
pipeline 말고 skip connection 사용하기도 함. <br>
iv) Data bootstrapping : pbmt output 다시 pbmt ... recursive 하게 해서 optimal 하게 만듦
모두 성능 향상에 기여한다. <br>
  </p>


<h3> Subject :  CHARAGRAM: Embedding Words and Sentences via Character n-grams </h3> <br>

<h5> Abstract </h5> <br>

<br>
<br>
<br>
[kmswin1@korea.ac.kr](kmswin1@korea.ac.kr)
