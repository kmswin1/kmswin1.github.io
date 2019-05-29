---
layout: page
title: NLP
permalink: /NLP/
---


<h1> NLP Papers </h1>
<h1> topics: predict next word, word embedding, cnn for text, rnn for language modeling, efficiency tricks for nlp, conditioned generation, attention </h1>

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

<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/스크린샷 2019-03-23 오전 12.24.47.png?raw=true" />
식 해석 : 전체 d개의 단어들에 대해 1~k gram 을 가지고 dictionary 에 있는 단어면 1, 아니면 0을 반환하고, weight 를 곱한 뒤, nonlinear function 적용 하여 임베딩 , 2,3,4 gram 으로 학습<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/20160802_7a29187b_charseq.jpeg?raw=true" />
charRNN : RNN 기반 character embedding 마지막 output vector 로 임베딩! <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/스크린샷 2019-03-23 오전 12.27.55.png?raw=true" />
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
LSTM 보다 간단하고, Gradient vanishing 을 해결하지만 성능은 더 좋지 못한 한계가 있다.<br>
<br>

<br>
<h3> Subject :  Simple, Fast Noise-Contrastive Estimation for Large RNN Vocabularies </h3>

<h5> Abstract </h5> 
1. 기존 language model 의 효율적인 학습방법 : NCE <br>
2. 기존 NCE 는 gpu 스럽게 병렬계산 하는것이 어려워 비효율적 <br>
3. ourmodel : 기존 NCE 보다 향상 된 병렬처리 가능 모델 개발 <br>

<h5> Model </h5>
1. what is the NCE? <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/NCE0.png?raw=true" /> <br>
기존 language model 은 모든 voca 의 word 들을 모두 고려 후, 확률 계산하여 불필요한 중복 계산이 많음 <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/NCE1.png?raw=true" /> <br>
그래서 NCE 에서는 voca 내에서 고려하려는 true training data 와 uniform 분포를 가진 voca 내의 k개의 data set (우리는 이것을 noise 라고 부를 것) 을 섞어서 학습하여 중복학습 제거 <br>
진짜 데이터의 확률 -> (1+k) 개중 1개 (prior) * language model 확률 (likelihood)( <br>
가짜 데이터의 확률 -> (1+k) 개중 k개 (prior) * noise languge model 확률 (Assumed likelihood)( <br>
language 모델과 데이터샘플링은 독립이므로 just product <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/NCE2.png?raw=true" /> <br>
Binary classification model 로 재정리 <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/NCE3.png?raw=true" /> <br>
language model 은 latent variable 이므로 θ 도입 후, MLE <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/NCE4.png?raw=true" /> <br>
정리 된 최종 MLE equation <br><br>
Our model<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/NCE5.png?raw=true" /> <br>
hyper parameter Z(u) 도입하여 1에 가까운 값으로 유지 N(1,ε) <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/NCE6.png?raw=true" /> <br>
p 를 구한 후, 1-p 로 바로 구하여, 불필요한 계산 최소화 <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/NCE7.png?raw=true" /> <br>
학습 시 계산해야 하는 language model softmax <br>
noise q(w) 가 batch 마다 다르므로 모든 batch 마다 따로 학습해주어야 함 (병렬처리 최적화 x), language model -> sparse matrix <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/NCE8.png?raw=true" /> <br>
noise q(w) 를 통일시켜서, hidden layer 를 vector 가 아닌 matrix 로 합침 (병렬처리 최적화 o), language model -> dense matrix <br>
<h5> Conclusion </h5>
간단한 방법으로 NCE 를 GPU 계산에 최적화 하였다.<br>
오리지널 NCE 보다 학습속도는 4배정도 빨랐다.<br>
성능또한 근소하게나마 좋았다.<br>

<br>
<h3> Subject :  Sequence to Sequence Learning with Neural Networks </h3>

<h5> Abstract </h5> 
1. Encoder Decoder 구조 LSTM (pretrained transfer learning 의 기반) <br>
2. language model -> 다양한 length 를 고정된 벡터 하나로 표현하여 딥러닝에 최적화(길이에 상관없이 모델에 적용가능) <br>
3. 최초의 bidirectional encoding <br>

<h5> Model </h5>
1. Encoder-Decoder <br>
Encoder Decoder 를 분리하여 학습하면, 학습 된 Encoder 를 가지고 다양한 task 의 Decoder 를 가지고 활용 가능 (미래의 탄생할 pretrained model 의 기틀) <br>
다양한 길이에 대해 적용이 가능하므로, 효율적인 디코딩을 위해서는 sequence to sequence language model 에서 고정 된 벡터 하나로 표현이 되어야 함(supervised backprop 위해서)<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/LSTM_3.png?raw=true" /> <br>
sentence length 는 인코딩 후 벡터 하나로 나타내기 쉬움 <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/LSTM_2.png?raw=true" /> <br>
또한, 그 벡터를 기반으로 output length 를 결정 할 수 있다. <br>
이러한 LSTM encoder 와 decoder 를 Layer 를 여러개 쌓는 것이 좀 더 높은 성능을 보였음 <br><br>

2. Bidirectional <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/LSTM_4.jpg?raw=true" /> <br>
기존 LSTM 모델에서는, sequence 길이가 길어지면 <br>
첫째, gradient vanishing 가능성이 생기거나, 앞 단어의 정보는 거의 고려하지 못한다. <br>
둘째, 문장 속에서 붙어있는 단어간 의존도에 의한 bias 가 생길 수 있다.<br>
명확한 답을 주기는 어렵지만, 아마도 위 두개의 이유로 인할 것이라고 예상이 되고, <br>
그래서 우리는 src sentence 를 순서를 뒤집어서 한번 더 인코딩 시켰다. <br>
그 결과, LSTM 성능이 BLUE score 5 이상 증가하였다.<br>
필자의 생각으로는, 위 두가지 이외에 LSTM hidden layer 의 뉴런 중 어떤 한 뉴런이 아마, sentence 의 위치에 따른 impact 에 대한 dimension 이 존재 할 것이고, 그것이 decoding 단에서 강한 bias 로 작용했을 것이다. to reverse the order of sentence 는 그것을 해결해 주지 않았을까? <br>
<h5> Conclusion </h5>
이후에 나오는 ELMo, GPT, BERT 등의 pretrained transfer learning 의 기반이 된 논문<br>
bidirectional LSTM 모델의 기반이 된 개념을 제시<br>
Language model 및 NMT 쪽의 큰 공헌을 한 것 같다.<br>

<br>
<h3> Subject :  Long Short-Term Memory-Networks for Machine Reading </h3>

<h5> Abstract </h5> 
1. 기존의 language model 은 문장의 내재된 구조 (주어 동사 목적어 등 관계) 나 먼 거리의 단어 간 영향력은 고려하기 힘들었음 (difficult to represent sentence by one vector) <br>
2. 그 문제를 해결하기 위해 Attention 개념이 도입 되었음 <br>
3. LSTM 은 이전 hidden state 만 저장 가능한 불완전한 memory cell <br>
4. External Memory network 이용하여 attention 구함 -> 인간과 같이 이전 단어들의 의미를 기억해 놓음 <br>

<h5> Model </h5>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/selfattention_2.png?raw=true" /> <br>
LSTM + 외부 메모리를 사용, 한 단어가 추가될 때 마다 attention 도 값을 업데이트 해줌<br>
매 스텝시 self attention memory 가짐<br>
다음 단어 생성시 현재까지의 attention weighted dot product <br>
이 과정은, 이전 Language model 과 다르게, non-markov state 임의 동시에 contextual representation 기능 함<br>
call additional memory to memory tape <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/selfattention_3.png?raw=true" /> <br>
h tilde 는 attention 적용 된 hidden vector, memory vector 라고 부름<br>
t step 에서의 i 번째 단어의 attention vector 는 t 번째 input, hidden vector and t-1 번째의 memory vector
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/selfattention_4.png?raw=true" /> <br>
t step 에서 h tilde, c tilde 는 t-1 step 까지의 attention 적용 안된 vector 들의 attention softmax score weighted sum
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/selfattention_5.png?raw=true" /> <br>
결국 self attention 적용 된 h,c tilde vector 가지고 LSTM 적용!!<br>
우리가 구하려는 query vector 는 v,h tilde 임
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/selfattention_6.png?raw=true" /> <br>
모델의 문장생성에 따른 attention 강도
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/selfattention_1.png?raw=true" /> <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/selfattention_7.png?raw=true" /> <br>
shallow & deep attention
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/selfattention_8.png?raw=true" /> <br>

<h5> Conclusion </h5>
기존 sequence to sequence model 은 문장의 구조, gradient vanishing or gradient exploding, long distance word relationship 문제를 가지고 있었다. 매 스텝마다 추가적인 메모리 장치를 이용하여 그 단어에 대한 self attention 개념을 도입하여 더 정확한 language model 도입 <br>

<br>
<br>
<br>
<br>
### Contact me

[kmswin1@korea.ac.kr](kmswin1@korea.ac.kr)
