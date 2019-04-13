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
convergence
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-03-23%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.25.52.png?raw=true" />

<p> 우리모델은 기존 character based embedding sota 들 보다 빠른 학습이 가능하고 성능도 더 좋아</p> <br>
<h3> Subject :  Convolutional Neural Network for Sentence classification </h3>

<h5> Abstract </h5> 
1. 요즘에 NLP 문제 CNN 으로 많이 풀더라 나도 CNN 으로 Sentence classification 실험 해 봄 -> 적은 패러미터로 매우높은 성능! <br>
2. Static vs Non-static model <br>
3. 사전에 학습 된 word2vec 사용 <br>

<h5> Model </h5>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-03-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.50.16.png?raw=true" />
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-03-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.51.33.png?raw=true" />
학습을 cnn 레이어까지만! <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-03-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.51.40.png?raw=true" />
학습을 word embdding 까지! <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-03-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.51.48.png?raw=true" />
multi-channel : 섞어서! (본 의도는 overfitting 을 방지하기 위함이지만 잘 안됌) <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-03-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.52.01.png?raw=true" />
non-static vs static : word embedding 의 변화가 보임.
<h5>Conclusion</h5>
요즘 NLP 문제 CNN 으로 많이 풀더라<br>
그래서 나도 해봤는데 기존 sota 보다 잘돼 ᄏᄏ 그리고 내 모델은 고작 conv layer 1개임<br>
그래서 Hyperparameter tuning 수 비교도 안되게 적음<br>
word embedding 까지 학습시키면 특정 task 에 더 잘돼 <br>
문장 길이를 고려하여 맞출 필요가 없는 max pooling 구조 !!<br>

<h3> Subject : Dependency-based Convolutional Neural Networks for Sentence Embedding </h3>

<h5> Abstract <h5> 
  이전의 CNN 기반 sentence embedding 모델들은 spatial information 을 이용하지만, 그 문장길이가 길어지면
  window size 에 모두 담지 못하므로, 거리가 먼 word 들간의 관계는 임베딩에 반영할 수가 없었어. 그래서 우리는 그
  한계를 극복하고자, non-local based model 인 Tree-based n-grams embedding 을 구현했고, 이전 sota 들
  보다 좋은 성능을 보였어. <br>
  
<h5> Intro </h5>
이전에도 Tree based model 은 있었지만, syntactic parse tree 이기 때문에, data sparsity 문제가 있어서 잘 쓰이지 않았어. 
yoon kim 의 CNN 모델은 이것을 해결했어. 그래서 이걸 합쳐서 해결 하려고해.
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/tree%20cnn_12.png?raw=true" /><br>
우리 모델은 yoon kim 의 (바로 위의 글) cnn based embedding 을 따라했지만, sequential 하지 않고, hierarchical 한 구조로
임베딩을 구현했어. <br>
(yoonkim 모델은 sequential 하기 때문에, 멀리 떨어진 단어끼리 임베딩 하려면 window 사이즈가 그만큼 커져야하고, 커질수록 data sparse
problem 은 심각해진다.)

<h5> Model </h5>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/Tree%20cnn_1.png?raw=true" /><br>
우리 모델의 기본적인 구조야. ROOT 를 dummy node 로 (padding) 지정 후, 계층 구조로 concat 하여 임베딩해<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/Tree%20cnn_2.png?raw=true" /><br>
기존 CNN embedding (i 번째 word 부터 j+1 개의 word concat)<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/Tree%20cnn_3.png?raw=true" /><br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/Tree%20cnn_4.png?raw=true" /><br>
우리 모델 embedding (i 번째 word 부터 ROOT node 까지 모든 ancestor word concat)<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/Tree%20cnn_5.png?raw=true" /><br>
그 후 conv 돌려서 relu 적용<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/Tree%20cnn_6.png?raw=true" /><br>
그러면 sentence 의 l 개의 단어들마다 모두 c 값이 나옴! -> data sparsity 해결 <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/Tree%20cnn_10.png?raw=true" /><br>
간단한 기존 CNN concat 된 모습<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/Tree%20cnn_9.png?raw=true" /><br>
우리 모델의 concat 된 모습<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/Tree%20cnn_7.png?raw=true" /><br>
하지만 위의 모델은 한계가 있으므로, 더 정확하게 학습시키기 위해 ancestor 뿐만 아니라 특정 단어의 sibling 까지 동시에 찾도록 학습<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/Tree%20cnn_8.png?raw=true" /><br>
즉, 가장 최종적으로 가장 advanced 된 모델은, ancestor, sibling, sequential 을 모두 진행 한 후, concat -> Fully connected layer<br>
각각 task 마다 100 개의 필터들을 사용<br>
결론적으로 기존의 CNN(300 dim) 보다 약 4배정도 커진 dimension 의 임베딩 (1,100 dim) 매우 heavy 해지긴 함!<br>
하지만 성능은 좋음!!<br>

특이점 : Dropout 은 0.5 확률로 노멀하지만, learning rate 를 0.95 로 높게 책정하여, 수렴보다는 빠른 학습을 택한 것으로 예상됩니다.
(recursive 한 tree 구조라서, 매우 많은 학습량이 요구될 non-convex 함수 일 것으로 예상됨)
<h5> Conclusion </h5>
우리는 recursive 한 트리 구조의 모델을 고안하여, 단어들의 위치에 상관없이 embedding 이 가능하게 했어. 근데, 매우 heavy 하긴 한 문제점을 
가지고 있긴 하지만, 좀 더 정밀한 임베딩이 가능하다고 볼 수 있어.
Self Attention 나온 이후 모든 것이 해결 되어 버렸다.
<br>
<h3> Subject :  Learning Phrase Representations using RNN Encoder–Decoder
for Statistical Machine Translation </h3>

<h5> Abstract </h5> 
1. 기계번역에서 새로운 접근법 : Endcoder-Decoder model <br>
2. RNN based model : GRU -> LSTM 보다 간단 & 계산 복잡도 ↓ <br>
3. update gate & reset gate 를 활용 <br>

<h5> Model </h5>
1. Encoder-Decoder approach <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/gru1.PNG?raw=true" /> <br>
word 들은 500 dim, encoder-decoder 각 hidden state 1000 개씩, weight 는 독립적 <br>
Encoder RNN 마지막 hidden state vector c -> latent vector <br>
Decoder RNN -> y_t =  y_t-1 ,c, h_t-1 고려 후 Decode <br>
X,Y 의 sequence 는 다를 수 있음 <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/gru2.PNG?raw=true" /> <br>
input, output sequence 의 pair 쌍의 maximum likelihood estimation 로 학습 <br><br>
After Training<br>
i) input vector(input sequece) 가지고, output sequence 생성가능 <br>
ii) input, output sequence pair probability scoring 가능<br><br>

2. Gated Recurrent Unit <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/gru7.PNG?raw=true" /> <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/gru3.PNG?raw=true" /> <br>
reset gate : 이전 hidden state 정보를 얼마나 버릴 것인지? (닫히면 아예 모두 0, 새로운 input x 만 고려) <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/gru4.PNG?raw=true" /> <br>
update gate : 이전 hidden state 정보를 얼마나 가져 올 것인지?<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/gru6.PNG?raw=true" /> <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/gru5.PNG?raw=true" /> <br>
z 값은 0<=z<=1 이므로, h_j 는 h_j 와 h'_j-1 vector 중 내분점에 위치 <br>
<h5> Conclusion </h5>
우리는 RNN Encoder-Decoder 접근을 통하여 length 를 고려하지 않고 문장들을 번역할 수 있게 되었다.<br>
그리고 source, target 문장 간 scoring 도 쉽게 가능 하게 되었다.<br>
LSTM 보다 효율적이고, Gradient vanishing 을  성능은 더 좋지 못한 한계가 있다.<br>
<br>
<br>
<br>
### Contact me

[kmswin1@korea.ac.kr](kmswin1@korea.ac.kr)
