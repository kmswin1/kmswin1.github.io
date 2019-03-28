---
layout: page
title: Neural ODE
permalink: /NeuralODE/
---

<h1> Deep Neural Network using by ODE </h1>
<h3> Subject : FFJORD: Free-form Continuous Dynamics for Scalable Reversible Generative Models </h3>
<h5> Abstract <h5> 
  <img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/FFJORD_1.png?raw=true" />
  <h5> Prior knowledge </h5>
  <img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/FFJORD_2.png?raw=true" />
  Proof of Change of variable <br>
  <p>
    P(A)=P(z1≤z≤z2)=∫z2z1pZ(z)dz(1)
이제 같은 사건 A가 일어날 확률을 X=g(Z)로 변환된 확률변수 X로 표현하면 다음과 같을 것이다.

P(A)=P(x1≤x≤x2)=∫g(z2)g(z1)pX(x)dx(2)
아직 변환된 X에 대한 확률분포 pX(x)를 모르는데 두 경우 사건 A가 일어날 확률을 동일하므로 X=g(Z)관계에 의해 적당히 잘 변환된 pX(x)를 다음과 같은 관계식으로부터 찾을 수 있다.[1]

P(z1≤z≤z2)=∫z2z1pZ(z)dz=∫x2=g(z2)x1=g(z1)pX(x)dx=P(x1≤x≤x2)(3)
일단 z1≤z≤z2 전구간에서 X=g(Z)의 역함수 Z=g−1(X)가 존재한다고 가정하면 다음처럼 변수를 바꿔서 적분할 수 있다.

∫z2z1pZ(z)dz=∫x2=g(z2)x1=g(z1)pZ(g−1(x))dg−1(x)dxdx(4)
확률변수 Z와 X의 도메인이 모두 1차원이라면 식(4)와 같으나 2차원 이상이 되어 적분의 경계가 영역이 되면 다음처럼 Jacobian에 절대값을 적용해야한다. 확률변수 Z와 X의 특정 영역을 Ẑ , X̂ 라 하면

∫z∈Ẑ pZ(z)dz=∫x∈X̂ pZ(g−1(x))∣∣∣dg−1(x)dx∣∣∣dx(5)
1차원에서 절대값이 필요없는 이유는 적분구간 양끝의 순서를 바꿀 수 있기 때문이다. 예를 들어

∫21(3x+1)3dx=7154
에서 x=g(t)=−t+13으로 치환한다고 하면 t=−3x−1 이므로

∫21(3x+1)3dx=∫−3(2)−1−3(1)−1(3g(t)+1)3dg(t)dtdt=∫−7−4(−t)3(−13)dt=7154
가 되는데 변수를 바꾸고 나서 적분의 경계를 보면 큰수가 아래오고 작은 수가 위로 가 있다. 이는 g(t)를 감소함수로 선택했기 때문에 일어나는 현상인데 이때 적분의 경계의 위치를 바꾸어 작은수가 밑으로 오고 큰수가 위로 가게 하면

∫−7−4(−t)3(−13)dt=−∫−4−7(−t)3(−13)dt=∫−4−7(−t)3(13)dt=7154
가 되어 경계를 바꾸는것으로 인해 dg(t)/dt의 음의 부호가 사라진다. 그래서 항상 작은 수를 아래쪽 경계로 쓰기로 하고, g(t)가 증가함수든 감소함수든 상관이 없으려면 식(5)와 같이 절대값을 써준다. 하지만 1차원에서는 경계의 아래쪽이 크든 작든 상관없으므로 g(t)가 어떤 함수라하더라도 절대값을 안써도 상관없다.

어쨋거나 식(5)의 우변은 식(3)에 의해 아래와 같으므로

∫x∈X̂ pZ(g−1(x))∣∣∣dg−1(x)dx∣∣∣dx=∫x∈X̂ pX(x)dx(6)
결과적으로 pX(x)는 다음과 같다.

pX(x)=pZ(g−1(x))∣∣∣dg−1(x)dx∣∣∣(7)
pX(x)를 교재에 따라 다음처럼 다르게 표현하기도 하는데 다 같은 표현이다. [2][3]

pX(x)=pZ(g−1(x))∣∣∣dg−1(x)dx∣∣∣=pZ(g−1(x))∣∣∣dzdg(z)∣∣∣=pZ(g−1(x))∣∣dg(z)dz∣∣=pZ(z)∣∣dg(z)dz∣∣(8)
반대로 pX(x)로 부터 pZ(z)는 다음과 같이 구해진다.

pZ(z)=pX(x)∣∣∣dg(z)dz∣∣∣=pX(g(z))∣∣∣dg(z)dz∣∣∣(9)
여기서 알 수 있는 점은 pX(x)가 Z=g−1(X) 관계에 의해 단순히 합성함수인 pZ(g−1(x)) 와 같지 않다는 점이다. </p>

  <h5> Model </h5>
   <img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/FFJORD_3.png?raw=true" />
    <img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/FFJORD_4.png?raw=true" />
    <img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/FFJORD_5.png?raw=true" />
    <img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/FFJORD_6.png?raw=true" />
    <img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/FFJORD_7.png?raw=true" />
    <img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/FFJORD_8.png?raw=true" />
    <img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/FFJORD_9.png?raw=true" />
   <h5> Experiment </h5>
       <img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/FFJORD_10.png?raw=true" />
<h5> Conclusion </h5>
    <img src="https://github.com/kmswin1/kmswin1.github.io/blob/master/images/FFJORD_11.png?raw=true" />

[kmswin1@korea.ac.kr](kmswin1@korea.ac.kr)
