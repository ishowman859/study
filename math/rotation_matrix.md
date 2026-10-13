# 회전행렬의 의미

공부 정리: 2026-10-14

## 1. 무엇을 회전하는가?

좌표축은 고정하고, 평면의 벡터를 원점 중심으로 반시계 방향으로 $\theta$만큼 회전한다. 벡터는 열벡터로 표시한다.

```math
\begin{pmatrix}
x'\\
y'
\end{pmatrix}
=
R(\theta)\begin{pmatrix}
x\\
y
\end{pmatrix},
\qquad
R(\theta)=
\begin{pmatrix}
\cos\theta&-\sin\theta\\
\sin\theta&\cos\theta
\end{pmatrix}.
```

시계 방향 회전은 $R(-\theta)$이다. 벡터 대신 좌표축을 회전하는 경우에는 부호를 구분해야 한다.

## 2. 행렬의 열은 기저벡터가 이동하는 곳이다

표준기저는 다음과 같다.

```math
e_1=\begin{pmatrix}
1\\
0
\end{pmatrix},
\qquad
e_2=\begin{pmatrix}
0\\
1
\end{pmatrix}.
```

선형변환 행렬 $A$의 첫 번째 열은 $Ae_1$, 두 번째 열은 $Ae_2$이다. 따라서 회전행렬을 이해하려면 두 기저벡터가 회전한 뒤 어디에 놓이는지 보면 된다.

- $e_1$을 $\theta$만큼 회전하면 단위원 위의 $(\cos\theta,\sin\theta)$로 간다.
- $e_2$는 처음부터 $e_1$보다 반시계 방향으로 $90^\circ$ 앞서 있다. 함께 회전한 뒤에도 첫 번째 벡터에 수직이며, 그 좌표는 $(-\sin\theta,\cos\theta)$이다.

$(a,b)$를 반시계 방향으로 $90^\circ$ 돌린 좌표가 $(-b,a)$라는 점을 이용하면, 두 번째 열의 부호를 삼각함수 덧셈정리 없이도 이해할 수 있다.

이 두 벡터를 열로 나란히 놓으면:

```math
R(\theta)=
\begin{pmatrix}
\cos\theta&-\sin\theta\\
\sin\theta&\cos\theta
\end{pmatrix}.
```

## 3. 일반 벡터에 왜 같은 행렬을 적용하는가?

모든 벡터는 $\mathbf v=xe_1+ye_2$로 나타낼 수 있다. 회전은 선형변환이므로:

```math
R(\theta)\mathbf v
=xR(\theta)e_1+yR(\theta)e_2.
```

따라서:

```math
\begin{pmatrix}
x'\\
y'
\end{pmatrix}
=
x\begin{pmatrix}
\cos\theta\\
\sin\theta
\end{pmatrix}
+y\begin{pmatrix}
-\sin\theta\\
\cos\theta
\end{pmatrix},
```

즉,

```math
x'=x\cos\theta-y\sin\theta.
```

```math
y'=x\sin\theta+y\cos\theta.
```

행렬 곱은 원래 벡터의 계수 $x,y$로 **회전한 두 기저벡터를 선형결합하는 계산**이다.

## 4. 비대각 원소가 있으면 전단인가?

비대각 원소는 한 입력 좌표가 다른 출력 좌표에도 영향을 준다는 뜻이다. 비대각 원소가 있다는 사실만으로 전체 변환이 전단(shear)이라고 결론 내릴 수는 없다.

예를 들어:

```math
S=\begin{pmatrix}
1&k\\
0&1
\end{pmatrix}
\quad\Rightarrow\quad
(x,y)\mapsto(x+ky,y)
```

는 가로 방향 전단이다. 높이 $y$에 비례하여 가로 위치를 바꾸며, $k\ne0$이면 일반적으로 길이와 각도를 보존하지 않는다.

반면 회전행렬의 두 열은 길이가 각각 1이고 서로 수직이다.

```math
\cos^2\theta+\sin^2\theta=1,
\qquad
(\cos\theta)(-\sin\theta)+(\sin\theta)(\cos\theta)=0.
```

따라서:

```math
R(\theta)^{\mathsf T}R(\theta)=I,
\qquad
\det R(\theta)=1.
```

전체 회전은 길이와 내적, 각도, 방향성을 보존한다. 각 원소를 따로 떼어서 변환의 종류를 판단하기보다, 행렬 전체가 기저벡터와 도형을 어떻게 바꾸는지 봐야 한다.

## 5. 90도 회전으로 확인하기

```math
R\left(\frac{\pi}{2}\right)
=
\begin{pmatrix}
0&-1\\
1&0
\end{pmatrix},
\qquad
\begin{pmatrix}
x\\
y
\end{pmatrix}
\mapsto
\begin{pmatrix}
-y\\
x
\end{pmatrix}.
```

따라서 $(1,0)$은 $(0,1)$로, $(0,1)$은 $(-1,0)$으로 간다. 특히 두 번째 열의 위쪽에 음수가 들어가는 이유가 드러난다.

## 6. 삼각함수 덧셈정리와 연결하기

먼저 $\beta$만큼 회전하고, 이어서 $\alpha$만큼 회전하면 총 회전각은 $\alpha+\beta$이다.

```math
R(\alpha)R(\beta)=R(\alpha+\beta).
```

왼쪽을 곱하면:

```math
\begin{pmatrix}
\cos\alpha\cos\beta-\sin\alpha\sin\beta&
-(\cos\alpha\sin\beta+\sin\alpha\cos\beta)\\
\sin\alpha\cos\beta+\cos\alpha\sin\beta&
\cos\alpha\cos\beta-\sin\alpha\sin\beta
\end{pmatrix}.
```

이를 $R(\alpha+\beta)$의 첫 번째 열과 비교하면:

```math
\cos(\alpha+\beta)=\cos\alpha\cos\beta-\sin\alpha\sin\beta,
```

```math
\sin(\alpha+\beta)=\sin\alpha\cos\beta+\cos\alpha\sin\beta.
```

회전행렬을 기저벡터의 기하학적 회전으로 먼저 구하면, 이 비교를 통해 덧셈정리를 유도할 수 있다.

## 핵심

회전행렬의 열은 회전한 기저벡터의 좌표다. 일반 벡터의 회전은 그 두 열의 선형결합이며, 비대각 원소가 있다는 이유만으로 전단이 되는 것은 아니다.
