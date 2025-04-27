---
title: Principle of Least Action
author: Sejeong Son
date: 2025-04-19 01:42:00 +0900
categories: [Physics, Lagrangian Mechanics]
tags: [Action, Lagrange, Mechanics, Variations, Functional]
render_with_liquid: false
use_math: true
---
# Introduction
자연과학을 배우는 과정에서 어떠한 법칙에 대해 '그냥 그런 줄 알아'하고 넘어가는 경우가 많다. 특히 물리학I에서 파동의 반사와 굴절을 배울 때 이러한 논리는 자주 인용된다 Veritasium의 영상 [The Closest We’ve Come to a Theory of Everything](https://www.youtube.com/watch?v=Q10_srZ-pbs)에서는  최소 작용의 원리<sub>Principle of Least Action</sub> 혹은 해밀턴의 원리<sub>Hamilton's Principle</sub>을 통해 명쾌하게 설명한다. 이번 포스트에서는 영상에서 모든 사람들의 이해를 위해 간략하게 설명한 부분을 좀 더 보충하여 그 원리를 엄밀히 보이고자 한다. 

# Calculus of Variations
변분법<sub>calculus of variations</sub>은 범함수<sub>functional</sub>에 대한 미적분학으로, 이 때 범함수란 함수를 입력받아 스칼라를 내놓는 함수이다. 대표적으로 '정적분으로 정의된 함수'를 생각해볼 수 있을 것이다. <br>
해석개론에서 정의하였듯이 연속함수 $$f:X \to Y$$ 의 전체 집합을 $$C(X,Y)$$ 라고 하자. 이때 다음 $$J$$는 범함수이다.

$$J: C(X,Y) \ni f \mapsto J[f] \in \mathbb{R}$$

미적분학에서 최댓값, 최솟값 혹은 이를 통틀어서 extrema을 찾기 위해 미분계수가 0인 지점을 찾는 것처럼 변분법에서도 범함수의 그것이 0인 지점을 찾아야 한다. 그러기 위해서는 범함수의 미분이 무엇인지부터 정의해야 한다.

## Variation

미분을 처음 배울 때 $$x$$ 값이 $$\Delta x$$ 만큼 매우 작게 변할 때 $$y$$ 값이 얼마나 변하는지로 정의하였던 방식이 기억날 것이다. 범함수의 경우도 마찬가지로 입력값인 함수 $$f$$를 $$\delta f$$만큼 변화시키는 것으로 시작한다. 
<br> 그것을 $$\epsilon \eta(x)$$ 라고 하자.(단, $$\eta(x_1)=\eta(x_2)=0$$)

$$f_\epsilon (x) = f(x) + \epsilon \eta(x)$$

이때 $$\delta f = \epsilon \eta(x)$$ 를 $$f$$의 변분<sub>variation</sub>이라고 한다. 위에서 $$\Delta x$$와 같은 역할이다.<br>
쉽게 생각하면 두 점을 연결한 실의 경로를 아주 살짝 바꾼 것이라 볼 수 있다.

그런데 이때 변분의 $$\eta(x)$$의 방향에 따라 $$J$$의 변화도 다를 수 있다. 즉, 미적분학에서의 다변수함수의 미분의 상황과 비슷한 것이다. <br>
- 방향도함수<sub>directional derivative</sub>

$$\nabla_{\mathbf{v}} f(\mathbf{x}) = \lim_{h\to 0} \frac{f(\mathbf{x}+h\mathbf{v})-f(\mathbf{x})}{h}$$

다음은 이를 일반화한 내용이다.

### Gâteaux Derivative

Banach 공간 $$X,Y$$와 $$F:X \to Y$$, $$u, \phi \in X$$에 대해

$$\lim_{\epsilon \to 0} \frac{F(u+\epsilon \phi)-F(u)}{\epsilon}$$

이 존재하면 이를 $$u$$의 $$\phi$$ 방향으로의 Gâteaux derivative 라고 하며, 모든 방향 $$\phi \in X$$에 대해 그 값이 존재하면 Gâteaux differentiable 이라고 말한다.

물론, 다변수함수에서 모든 방향미분계수의 존재가 그 함수의 미분가능성(gradient의 존재성)을 보장할 수 없듯이 이 경우에도 Gâteaux differentiable은 비교적 약한 개념이다. gradient의 일반화로 Fréchet derivative가 정의되어 있지만 이는 너무 강한 조건을 만족해야 하기에 물리나 공학의 분야에서는 Gâteaux differentiable만 확인해도 충분하다. 후술할 내용도 이와 마찬가지이다.

다시 범함수로 돌아와서 위 내용을 적용해보면,

$$\delta J[f,\eta] = \lim_{\epsilon \to 0} \frac{J[f(x) + \epsilon \eta(x)]-J[f(x)]}{\epsilon}$$

로 표현할 수 있다. 즉, 변분 $$\delta J = \delta J[f,\eta]$$를 범함수의 방향도함수라고도 생각할 수 있다.

## Fundamental Lemma of Calculus of Variations

$$f:(a,b) \to \mathbb{R}$$가 연속, $$\eta$$가 $$(a,b)$$에서 매끄러운 함수, 컴팩트 지지<sub>compactly supported</sub>일 때,

$$\int_{a}^{b}f(x)\eta(x)dx=0 \Rightarrow f(x)=0$$

이 때 함수가 컴팩트 지지라 함은, $\\{x \in (a,b)\|\eta(x)\ne 0\\}$의 폐포가 compact임을 말한다.

### Proof
어떤 $$x \in (a,b)$$에 대해 $$f(x)>0$$라 가정.
f가 연속이므로 $$\exists c,d \textrm{ s.t. } (a<c<x<d<b, \forall t \in (c,d) f>0)$$

$$\eta(x)= \begin{cases} \exp \left(-\frac{1}{(x-c)(d-x)}\right) & x\in(c,d)\\
0 & {\sf otherwise} \end{cases}$$ 

라 하면 주어진 조건을 만족하며 또한 $(c,d)$에서 양수이다.

$$ \int_{a}^{b}f(x)\eta(x)dx>0$$

이므로 모순. $f(x)<0 $인 경우도 같은 방법으로 증명.

# Action Principle
## Maupertuis's Principle
Maupertuis는 두 점 사이를 잇는 모든 경로에서 $_{\sf 총에너지}E$는 같다는 제약 조건 하에서 작용<sub>action</sub>을 다음과 같이 정의하였다.

$$S_0 := \sum mvs$$ 

이는 운동 방향이 연속적으로 변하는 상황을 고려하여 다음과 같이 재정의되었다.

$$S_0 := \int mv ds = \int \mathbf{p} \cdot d\mathbf{q}$$

이때 $\mathbf{q}=\{q_1, q_2, ... , q_N\}$ 을 일반화 좌표<sub>generalized coordinates</sub>라 하며 $\mathbf{p}=\{p_1, p_2, ... , p_N\}$을 켤례 운동량<sub>conjugate momenta</sub>라고 한다.

즉, 운동량을 경로에 대해 적분한 값이 최소화되는 경로로 물체가 운동한다고 Maupertuis는 해석하였다.<br>
이 때 $(\delta \mathcal{S}_0)_E=0$ 를 만족하는 해는 두 좌표를 연결하는 함수이다. 

### example

이 원리로 간단하게 높이 $h$에서 $0$ 까지의 자유 낙하 운동의 궤적을 생각해보자.

$$S_0 = \int p dq = \int \sqrt(2m(E-V(q))) dq = \int \sqrt(2m(E-mgq)) dq$$

$$\delta S_0 = \lim_{\epsilon \to 0) $$


## Ferma's Principle
페르마의 원리<sub>Ferma's Principle</sub>는 즉, 최소 시간의 원리로 빛의 진행 경로를 시간이 최소가 되는 경로라고 설명하여 반사와 굴절을 설명한다. 
위에서 정의한 작용을 다시 살펴보자.

$$\delta \mathcal{S}_0=\delta \int mvds=\delta \int mv^2dt=\delta \int2Tdt=\delta \int(T+E-V)dt \\ =\delta \int (T-V)dt+\delta(E\Delta t)=\delta \int Ldt+E\delta (\Delta t)$$

이때 라그랑지언<sub>Lagrangian</sub>은 $$L := _\textrm{운동에너지}T-_\textrm{퍼텐셜에너지}V$$로 정의한다. 최소 시간이라 함은 즉, $$\delta (\Delta t)=0 $$ 를 의미한다.

## Hamilton's Principle

위의 두 원리를 절충해보자. 즉, 이번에는 제약 조건이 총에너지가 아닌 $_{소요 시간}\Delta t(=t_2-t_1)$이 일정하다는 것이다. (물론 한 경로에서 에너지 보존은 성립한다.)
이 경우 위의 식으로부터 작용을 새롭게 정의할 수 있다.

$$\mathcal{S}[\mathbf{q(t)}]\triangleq \int_{t_1}^{t_2}L(\mathbf{q}(t),\dot{\mathbf{q}}(t),t)dt$$

따라서 이 경우 최소화되는 경로는 $_{시간}t$에 대해 매개화된 곡선으로 나타난다. 

이제 변분법을 이용하면,

$$\delta \mathcal{S}=0 \Leftrightarrow 
\forall i,
\frac{\partial L}{\partial q_i}-\frac{d}{dt}\frac{\partial L}{\partial \dot{q_i}}=0$$

# Newton's Second Law

이제 구한 식을 수식적으로 풀어보면,
$$\frac{\partial L}{\partial q_i}=\frac{\partial (T-V)}{\partial q_i}=-\frac{\partial V}{\partial q_i}=_{보존력}F$$
$$\frac{d}{dt}\frac{\partial L}{\partial \dot{q_i}}=\frac{d}{dt}\frac{\partial (T-V)}{\partial \dot{q_i}}=\frac{d}{dt}\frac{\partial T}{\partial \dot{q_i}}=\frac{d}{dt}  {}_{운동량}P=ma$$
즉, 최소 작용의 원리는 뉴턴 역학의 공리와 동치이다.



## Euler-Lagrange Equation
정확히 말하면 1차원 오일러-라그랑주 방정식<sub>the one-dimensional Euler–Lagrange equation</sub>이다.

다음과 같은 범함수를 생각해보자.
$$J[f]=\int_{a}^{b}F(x,f(x),f'(x))dx$$
이 때, $f$는 경계값 조건 $f(a)=c, f(b)=d$를 만족하며, $F$는 연속적인 편미분값을 가진다. 

$g_\epsilon(x)=f(x)+\epsilon\eta(x)$를 고려해보자. ($\eta(a)=\eta(b)=0, \eta$는 미분가능)
$$\Phi(\epsilon)=J[g_\epsilon]=\int_{a}^{b}F(x,g_\epsilon(x),g_\epsilon'(x))dx$$

전미분의 정의에 의하여,
$$\frac{\mathrm{d}F}{\mathrm{d}\epsilon}=\frac{\partial F}{\partial x} \frac{\partial x}{\partial \epsilon} + \frac{\partial F}{\partial g_\epsilon}\frac{\partial g_\epsilon}{\partial \epsilon}+\frac{\partial F}{\partial g'_\epsilon}\frac{\partial g'_\epsilon}{\partial \epsilon}=\eta(x)\frac{\partial F}{\partial g_\epsilon}+\eta'(x)\frac{\partial F}{\partial g'_\epsilon}$$


$J$를 $\epsilon$에 대해 전미분하면,
$$\Phi'(\epsilon)=\frac{\mathrm{d}\Phi}{\mathrm{d}\epsilon}=\int_{a}^{b}\frac{\mathrm{d}F}{\mathrm{d}\epsilon}dx=\int_{a}^{b} \left[\eta(x)\frac{\partial F}{\partial g_\epsilon}+\eta'(x)\frac{\partial F}{\partial g'_\epsilon}\right]dx$$

이 때, $\epsilon=0$을 대입하고, 부분적분을 이용하면
$$\Phi'(0)=\int_{a}^{b} \left[\eta(x)\frac{\partial F}{\partial f}+\eta'(x)\frac{\partial F}{\partial f'}\right]dx=
\int_{a}^{b} \left[\frac{\partial F}{\partial f}-\frac{d}{dx}\frac{\partial F}{\partial f'}\right]\eta(x)dx+\left[\eta(x)\frac{\partial F}{\partial f'}\right]_a^b
\\

=\int_{a}^{b} \left[\frac{\partial F}{\partial f}-\frac{d}{dx}\frac{\partial F}{\partial f'}\right]\eta(x)dx$$

$f$에서 $J$가 극값을 가진다면, (극솟값으로 생각) 0 근처의 적당한 $\epsilon$에 대해 $J[f]\leq J[f+\epsilon \eta]=\Phi (\epsilon)$ 이므로 $\Phi (\epsilon)$은 $\epsilon =0$에서 극소이다. 따라서 $\Phi'(0)=0$, 변분법의 기본 보조정리에 의하여
$$\frac{\partial F}{\partial f}-\frac{d}{dx}\frac{\partial F}{\partial f'}=0$$

이 방정식은 함수$f$가 여러 개인 경우, $f$의 고계 도함수가 고려되는 경우로 일반화될 수 있다.