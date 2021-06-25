---
layout: page
title: LanguageModel
permalink: /LanguageModel/
---
<h1> NLP Papers </h1>
<h2> topics : Contextualized embedding(BERT,ULM Fit), Semantic vs Syntactic embedding</h2>

<h3> Subject : BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding </h3>

<h5> Abstract <h5> 
현 NLP 계의 끝판왕. pretrained contextualized LM model<br>
1.semi-supervised learning (masked LM)<br>
2.transfer learning (pretrained-encoder)<br>
3.task-specific fine-tuning<br>
4.next sentence prediction<br>

<h5> model </h5>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_0.png?raw=true" /><br>
BERT 는 기본적으로 context 기반 embedding 임<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_2.png?raw=true" /><br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_3.png?raw=true" /><br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_4.png?raw=true" /><br>
semi-supervised learning 을 통해서, 부족한 data set 을 보충하고, unsupervised 보다 더욱 효율적인 학습<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_5.png?raw=true" /><br>
이전 sota 모델들과의 비교, BERT 는 bidirectional 이고, 12개의 transformer 를 쌓음<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_6.png?raw=true" /><br>
token embedding, segment embedding, positional embedding 세개로 이루어짐<br>
token 은 word 단위, segment 는 문장이 두개일 시 문장 구분, positional 은 단어의 문장내 위치 고려<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_1.png?raw=true" /><br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_7.png?raw=true" /><br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_8.png?raw=true" /><br>
general-domain pretrain encoder 를 가지고 특정 task 에 fine-tuning 후 사용<br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_10.png?raw=true" /><br>
Masked LM 으로 semi-supervised learning 구현 <br>
전체 중 15% 를 masking<br>
그 중 80% 는 그대로 masking <br>
10% 는 랜덤으로 다른 단어 (de-noising auto-encoder) <br>
10% 는 원래 단어 (label) <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_9.png?raw=true" /><br>
문장이 두개 일 시, Next sentence prediction 기법을 통해 문맥 정보를 더 고려한다.<br>
확실히 성능 향상에 기여 함<br>


<h5> Conclusion </h5>
NLP 분야에서 끝판왕일만큼 여러기법들을 제시했다. (masked LM, sentence prediction, bidirectional LM, pretrained encoder, task-specific fine tuninh)<br>
BERT 이후에 각종 NLP task 들은 정복 된 것만 같다. 과연 이후에 BERT 를 능가 할 모델이 나올 수 있을까?<br>
<br>

<h3> Subject : Does BERT really care about a semantic information ? </h3>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/analysis_0.png?raw=true" /><br>


<h5> Abstract <h5> 
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/analysis_1.png?raw=true" /><br>

<h5> model </h5>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/analysis_2.png?raw=true" /><br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/analysis_3.png?raw=true" /><br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/analysis_4.png?raw=true" /><br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/analysis_5.png?raw=true" /><br>

<h5> Experiments and Results </h5>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/analysis_6.png?raw=true" /><br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/analysis_7.png?raw=true" /><br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/analysis_8.png?raw=true" /><br>

<h5> Conclusion </h5>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/analysis_9.png?raw=true" /><br>

<br>

<h3> Subject : Universal Language Model Fine-tuning for Text Classification </h3>

<h5> Abstract <h5> 
최근 imageNet, resNet 등 vision 분야에서 pre-train 된 모델이 state of the art 로 떠올랐다. <br>
그러나 NLP 분야에서는 pretrained model 도입에 관한 여러 시도가 있었지만 결과가 별로 좋지 않았다. <br>
그 이유가 이전까지 vision 과 똑같은 방식의 프로세스로 train 및 fine tuning 했었지만, 나는 NLP 에서는 다른 fine tuning 기법등이 필요하다는 것을 생각했다. <br>
그래서 이 논문에서 새로운 state of the art 성능을 내는 NLP 맞춤 pretrained 모델 및 fine tuning 기법들을 소개하려 한다.<br>

<h5> model </h5>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/ULMFit_0.png?raw=true" /><br>
우리는 우선, general domaion Language model Space H 를 pretrain 시켜서 학습 시켜놓는다. <br>
<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/BERT_2.png?raw=true" /><br>

<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/ULMFit_1.png?raw=true" /><br>
후에, 특정 domain data set 에 맞도록 fine tuning 한다. <br>

<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/ULMFit_3.png?raw=true" /><br>
이때, learning rate 를 layer 별로 다르게 준다. <br>

<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/ULMFit_4.png?raw=true" /> <br>
다음 layer의 learning rate 는 이전 layer 의 learning rate 2.6배 : later 마다 고려하는 정보가 다르고, 상위 layer로 갈수록, semantic, data genre 를 많이 고려하므로 많은 변화가 필요 할 것으로 예상 <br>

<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/ULMFit_5.png?raw=true" /><br>

<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/ULMFit_6.png?raw=true" /><br>

<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/ULMFit_7.png?raw=true" /><br>
warm-up scheduler <br>

<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/ULMFit_2.png?raw=true" /><br>
모든 layer 를 한꺼번에 fine tuning 하면 이전 general domain LM 의 정보가 사라질 수 있으므로, 한 layer 씩 학습시키도록 한다.<br>

<img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/ULMFit_8.png?raw=true" /><br>
sentence classification 과 같은 특정 task 에는 concat pooing 을 도입하여 더욱 정보의 손실이 없도록 한다.<br>


<h5> Conclusion </h5>
NLP task 에서의 transfer learning 의 state of the art 기준 제시<br>

<br>

[kmswin1@korea.ac.kr](kmswin1@korea.ac.kr)
