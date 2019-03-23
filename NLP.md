---
layout: page
title: NLP
permalink: /NLP/
---


<h1> NLP Papers </h1>
<h3> Subject : Stronger baselines for trustable results in Neural machine translation </h3>
<h5> Abstract <h5> 
  NMT 모델에 대하여 정확한 성능 평가를 위한 제대로 된 기준이 필요할 것이고 우리가 제시해볼게 !!<br>

<h5> Intro & Experiment </h5>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/st1.png?raw=true" />
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-03-23%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.31.08.png?raw=true?raw=true" />
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
모두 성능 향상에 기여한다. 
  </p>
  <h5> Conclusion </h5>
<p> NMT 모델개발하고 성능 평가 할 때, 통상적으로는
우리가 제시해준 기준을 따르면 가장 강력한 무기가 될 거야.<br> </p>

<br>
<h3> Subject :  CHARAGRAM: Embedding Words and Sentences via Character n-grams </h3>

<h5> Abstract </h5> 
전통적으로 word 단위 임베딩을 많이하는데, 그건 트레이닝셋에서 없는 매우 희귀한 단어들은 학습시키기 어려워 또, 이전 character based 모델인 charRNN, charCNN 보다 우리꺼가 성능이 더 좋아. 우리모델은 간단한 n-gram counter vector 들을 non-linear transformation 해서 낮은 차원으로 임베딩해 <br>
<h5> Model </h5>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/스크린샷 2019-03-23 오전 12.24.47.png?raw=true" />
식 해석 : 전체 d개의 단어들에 대해 1~k gram 을 가지고 dictionary 에 있는 단어면 1, 아니면 0을 반환하고, weight 를 곱한 뒤, nonlinear function 적용 하여 임베딩 , 2,3,4 gram 으로 학습<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/20160802_7a29187b_charseq.jpeg?raw=true" />
charRNN : RNN 기반 character embedding 마지막 output vector 로 임베딩! <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/스크린샷 2019-03-23 오전 12.27.55.png?raw=true" />
charCNN : CNN 기반, 보통 3,4,5 size conv 돌린 후 , max pooling -> fc -> output (yoon kim model) <br>

<h5> Conclusion </h5>
sentence similarity
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-03-23%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.25.17.png?raw=true" />
pos tagging
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-03-23%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.25.32.png?raw=true" />
convergence
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-03-23%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.25.52.png?raw=true" />

<p> 우리모델은 기존 character based embedding sota 들 보다 빠른 학습이 가능하고 성능도 더 좋아</p>
<br>
<br>
<br>
### Contact me

[kmswin1@korea.ac.kr](kmswin1@korea.ac.kr)
