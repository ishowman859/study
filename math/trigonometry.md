# Trigonometry: 코사인 법칙

## 공식

두 변의 길이가 $a$, $b$이고 그 사이의 각이 $\theta$인 삼각형에서, $\theta$의 맞은편 변의 길이를 $c$라고 하면 다음이 성립한다.

$$
c^2 = a^2 + b^2 - 2ab\cos\theta
$$

이 관계를 **코사인 법칙(law of cosines)**이라고 한다.

## 피타고라스 정리로 유도하기

두 변이 만나는 꼭짓점을 $O=(0,0)$에 놓고, 길이가 $a$인 변을 가로축에 놓는다. 두 변의 끝점은 다음과 같다.

$$
A=(a,0), \qquad B=(b\cos\theta, b\sin\theta)
$$

세 번째 변 $AB$의 가로 방향 좌표 차이는 $a-b\cos\theta$, 세로 방향 좌표 차이는 $-b\sin\theta$이다. 피타고라스 정리를 적용하면:

$$
\begin{aligned}
c^2
&=(a-b\cos\theta)^2+(b\sin\theta)^2\\
&=a^2-2ab\cos\theta+b^2\cos^2\theta+b^2\sin^2\theta\\
&=a^2-2ab\cos\theta+b^2(\cos^2\theta+\sin^2\theta)\\
&=a^2+b^2-2ab\cos\theta.
\end{aligned}
$$

마지막 단계에서는 $\cos^2\theta+\sin^2\theta=1$을 사용했다. 이 좌표를 이용한 유도는 예각, 직각, 둔각 삼각형 모두에 적용된다.

## 피타고라스 정리와의 관계

$\theta=90^\circ$이면 $\cos\theta=0$이므로:

$$
c^2=a^2+b^2
$$

즉, 피타고라스 정리는 코사인 법칙의 직각인 경우에 해당한다.

## 왜 이런 이름을 쓰는가?

공식에 코사인이 등장하고, 코사인을 통해 변의 길이와 각도를 연결하기 때문에 코사인 법칙이라고 부른다. 피타고라스 정리는 사람의 이름을 딴 명칭이고, 코사인 법칙은 공식에 등장하는 함수의 이름을 딴 명칭이다.

여기서 법칙(law)과 정리(theorem)는 모두 증명할 수 있는 수학적 관계를 가리킨다. 이 문맥에서 두 표현의 차이는 전통적인 명칭의 차이이지, 법칙이 정리보다 더 기본적이라는 뜻은 아니다.

## 벡터에서 세 번째 변이 왜 차이인가?

같은 점 $O$에서 출발하는 두 벡터를 $\mathbf a=\overrightarrow{OA}$, $\mathbf b=\overrightarrow{OB}$라고 하자. $O$에서 $B$를 거쳐 $A$로 이동하면:

$$
\mathbf b+\overrightarrow{BA}=\mathbf a
$$

따라서 두 끝점을 연결하는 벡터는:

$$
\overrightarrow{BA}=\mathbf a-\mathbf b.
$$

반대 방향의 벡터는 $\mathbf b-\mathbf a$이며 길이는 같다. 세 번째 변의 **벡터**는 $\mathbf a-\mathbf b$이고, 그 **길이**는 $\|\mathbf a-\mathbf b\|$이다. 따라서 벡터에 코사인 법칙을 적용하면:

$$
\|\mathbf a-\mathbf b\|^2
=\|\mathbf a\|^2+\|\mathbf b\|^2
-2\|\mathbf a\|\|\mathbf b\|\cos\theta.
$$
