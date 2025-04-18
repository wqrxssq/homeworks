# Линайная алгебра и геометрия. ИДЗ №3(вариант 21)

## Выполнил студент Наседкин Дмитрий Сергеевич (группа 242)

### №1

Нам даны 2 вектора $v_1 = (-1, -1, 2, 1, 3, -2), v_2 = (-4, -2, -2, 1, 3, 2)$ и матрица СЛУ:

$$
A =
\begin{pmatrix}
3 & 3 & 2 & -3 & 5 & 5 \\
2 & 2 & 3 & -7 & 5 & 5 \\
-1 & -1 & 2 & -7 & 1 & 1
\end{pmatrix}
$$

Проверим, что $v_1, v_2$ действительно являются решениями системы:

$v_1$:
$$
-3 -3 + 4 -3 + 15 - 10 = 0 \text{, верно} \\
-2 -2 + 6 -7 + 15 - 10 = 0 \text{, верно} \\
1 + 1 + 4 -7 + 3 - 2 = 0 \text{, верно}
$$

$v_2$:
$$
-12 - 6 -4 - 3 + 15 + 10 = 0 \text{, верно} \\
-8 -4 -6 -7 + 15 + 10 = 0 \text{, верно} \\
4 + 2 - 4 -7 + 3 + 2 = 0 \text{, верно}
$$

Также очевидно, что они ЛНЗ.

Идея: воспользуемся алгоритмом поиска ФСР, однако подставлять будем не 1 в свободные переменные, а значения на позициях из свободных в $v_1, v_2$.

УСВ матрицы $A$:
$$
\begin{pmatrix}
3 & 3 & 2 & -3 & 5 & 5 \\
2 & 2 & 3 & -7 & 5 & 5 \\
-1 & -1 & 2 & -7 & 1 & 1
\end{pmatrix}
\sim
\begin{pmatrix}
1 & 1 & 0 & 1 & 1 & 1 \\
0 & 0 & 1 & -3 & 1 & 1 \\
0 & 0 & 0 & 0 & 0 & 0
\end{pmatrix}
$$

Позиции свободных переменных это $2, 4, 5, 6$, то есть будет 4 базисных вектора(причем первые 2 нам уже задали):

1) $u_1 = (*, -1, *, 1, 3, -2) = (-1, -1, 2, 1, 3, -2) = v_1$.
2) $u_2 = (*, -2, *, 1, 3, 2) = (-4, -2, -2, 1, 3, 2) = v_2$.

Нужно выбрать такие $u_3, u_4$, чтобы если взять их значения на позициях свободных переменных, то они образовывали базис всех решений $A$, для этого дополним систему из свободных переменных до базиса $F_4$ стандартными векторами:

$$
\begin{pmatrix}
-1 & 1 & 3 & -2 \\
-2 & 1 & 3 & 2
\end{pmatrix}
\sim
\begin{pmatrix}
1 & -1 & -3 & 2 \\
0 & 1 & 3 & -6
\end{pmatrix}
$$

Таким образом, добавив стандарнтные вектора $e_3, e_4$ получим базис $F_4$, тогда
$$u_3 = (*, 0, *, 0, 1, 0) = (-1, 0, -1, 0, 1, 0),$$
$$u_4 = (*, 0, *, 0, 0, 1) = (-1, 0, -1, 0, 0, 1).$$

### №2

$$
A =
\begin{pmatrix}
-6 & 5 & 3 & 1 \\
-6 & 5 & 3 & 1 \\
3 & -6 & 2 & 3 \\
-6 & 5 & 3 & 1
\end{pmatrix}
$$

Для начала нужно найти базис $Im \ \varphi, ker \ \varphi$:

- Для поиска базиса $Im \ \varphi$ найдем базис среди столбцов $A$:

$$
\text{УСВ } A =
\begin{pmatrix}
1 & 0 & \frac{-4}{3} & -1 \\
0 & 1 & -1 & -1 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$
Тогда первый($v_1$) и второй($v_2$) столбец образуют базис ядра, то есть $Im \ \varphi = \langle (-6, -6, 3, -6), (5, 5, -6, 5) \rangle$.

- Для поиска базиса $ker \ \varphi$ просто найдем ФСР системы $Ax = 0$.

Возьмем тот же УСВ $A$, в нем позиции свободных переменных: 3, 4, тогда:
$$
u_1 = (*, *, 3, 0) = (4, 3, 3, 0) \\
u_2 = (*, *, 0, 1) = (1, 1, 0, 1)
$$

То есть $ker \ \varphi = \langle (4, 3, 3, 0), (1, 1, 0, 1) \rangle$.

Теперь найдем базис $Im \ \varphi + ker \ \varphi$, для этого нужно найти базис $\langle v_1, v_2, u_1, u_2 \rangle$:

$$
\begin{pmatrix}
-6 & 5 & 4 & 1 \\
-6 & 5 & 3 & 1 \\
3 & -6 & 3 & 0 \\
-6 & 5 & 0 & 1
\end{pmatrix}

\sim

\begin{pmatrix}
-6 & 5 & 4 & 1 \\
0 & -7 & 10 & 1 \\
0 & 0 & -1 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$

Позиции главных переменных - 1, 2, 3, тогда $v_1, v_2, u_1$ образуют базис.
То есть $Im \ \varphi + ker \ \varphi = \langle (-6, -6, 3, -6), (5, 5, -6, 5), (4, 3, 3, 0) \rangle$.

Найдем $Im \ \varphi \cap ker \ \varphi$, для этого воспользуемся (очевидным!) алгоритмом(с гитхаба Димы):

1) Найдем ФСР системы $Dx = 0$, где $D = (v_1 | v_2 | u_1 | u_2)$:

$$
\begin{pmatrix}
-6 & 5 & 4 & 1 \\
-6 & 5 & 3 & 1 \\
3 & -6 & 3 & 0 \\
-6 & 5 & 0 & 1
\end{pmatrix}
\sim
\begin{pmatrix}
-6 & 5 & 4 & 1 \\
0 & -7 & 10 & 1 \\
0 & 0 & -1 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
\sim
\begin{pmatrix}
1 & 0 & 0 & \frac{-2}{7} \\
0 & 1 & 0 & \frac{-1}{7} \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$

$$
\begin{pmatrix}
* \\
* \\
* \\
7
\end{pmatrix}
=
\begin{pmatrix}
2 \\
1 \\
0 \\
7
\end{pmatrix}
- ФСР
$$

2)

$$
R =
\begin{pmatrix}
4 & 1 \\
3 & 1 \\
3 & 0 \\
0 & 1
\end{pmatrix}
\begin{pmatrix}
0 \\
7
\end{pmatrix}
=
\begin{pmatrix}
7 \\
7 \\
0 \\
7
\end{pmatrix}
$$

3) Дальше нужно найти базис среди столбцов $R$, но это очевидно и есть единственный столбец из $R$.

Таким образом $Im \ \varphi \cap ker \ \varphi = \langle (7, 7, 0, 7) \rangle.$

### №3

По лемме о стабилизации знаем, что $Im \ \varphi^4 = Im \ \varphi^5 = \dots = Im \ \varphi^{2019}$, так как $\dim \R^4 = 4$. То есть чтобы достаточно вычислить $\varphi^4$ и после этого найти базис $Im \ \varphi^4$.

Точно также, что $\ker \psi^4 = \ker \psi^5 = \dots = \ker \psi^{2020}$, то есть достаточно вычислить $\psi^4$ и после этого найти базис $ker \ \psi^4$.

Для дальнейшего удобства, отметим, что $(A^T)^4 = (A^4)^T$.

$$\varphi^4 =
\Bigg(\begin{pmatrix}
4 & 2 & -4 & 7 \\
-4 & -2 & 7 & -11 \\
0 & 0 & 4 & -4 \\
0 & 0 & 2 & -2
\end{pmatrix}^2\Bigg)^2
= \begin{pmatrix}
8 & 4 & -4 & 8 \\
-8 & -4 & 8 & -12 \\
0 & 0 & 8 & -8 \\
0 & 0 & 4 & -4
\end{pmatrix}^2 =
\begin{pmatrix}
32 & 16 & 0 & 16 \\
-32 & -16 & 16 & -32 \\
0 & 0 & 32 & -32 \\
0 & 0 & 16 & -16
\end{pmatrix}
$$

$$
\psi^4 =
\begin{pmatrix}
32 & 16 & 0 & 16 \\
-32 & -16 & 16 & -32 \\
0 & 0 & 32 & -32 \\
0 & 0 & 16 & -16
\end{pmatrix}^T =
\begin{pmatrix}
32 & -32 & 0 & 0 \\
16 & -16 & 0 & 0 \\
0 & 16 & 32 & 16 \\
16 & -32 & -32 & -16
\end{pmatrix}
$$

Чтобы найти базис $Im \ \varphi^4$ нужно найти базис среди столбцов матрицы $A^4$.

Приведем матрицу оператора $\varphi^4$ к ступенчатому виду:
$$
\begin{pmatrix}
32 & 16 & 0 & 16 \\
-32 & -16 & 16 & -32 \\
0 & 0 & 32 & -32 \\
0 & 0 & 16 & -16
\end{pmatrix}
\sim
\begin{pmatrix}
32 & 16 & 0 & 16 \\
0 & 0 & 16 & -16 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$

1, 3 - позиции главных переменных, тогда $v_1 = (1, -1, 0, 0), v_3 = (0, 1, 2, 1)$ - базис $Im \ \varphi^4$. То есть $dim  \ Im \ \varphi^4 = 2$.

Чтобы найти базис $ker \ \psi^4$ нужно найти ФСР системы $\psi^4 x = 0$.

Приведем матрицу оператора $\psi^4$ к УСВ:
$$
\begin{pmatrix}
32 & -32 & 0 & 0 \\
16 & -16 & 0 & 0 \\
0 & 16 & 32 & 16 \\
16 & -32 & -32 & -16
\end{pmatrix}
\sim
\begin{pmatrix}
1 & -1 & 0 & 0 \\
1 & -1 & 0 & 0 \\
0 & 1 & 2 & 1 \\
1 & -2 & -2 & -1
\end{pmatrix}
\sim
\begin{pmatrix}
1 & 0 & 2 & 1 \\
0 & 1 & 2 & 1 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$
Тогда ФСР равно:
$$
u_1 = (*, *, 1, 0) = (-2, -2, 1, 0)\\
u_2 = (*, *, 0, 1) = (-1, -1, 0, 1)\\
$$
Отметим, что $\dim \ker \psi^4 = 2$.

Так как $\dim \R^4 = \dim \ Im \ \varphi^{2019} + \dim \ker \psi^{2020} = 2 + 2 =4$, то $\R^4 = Im \ \varphi^{2019} \oplus \ker \psi^{2020}$.

Разложим $v$ в сумму векторов $u \in Im \ \varphi^{2019}$ и $w \in \ker \psi^{2020}$. Для этого решим систему $Dx = v$, где $D = (v_1|v_3|u_1|u_2)$.

$$
\begin{pmatrix}
\begin{array}{c c c c|c}
1 & 0 & -2 & -1 & -3\\
-1 & 1 & -2 & -1 & -4\\
0 & 2 & 1 & 0 & 7\\
0 & 1 & 0 & 1 & 6
\end{array}
\end{pmatrix}
\sim
\begin{pmatrix}
\begin{array}{c c c c|c}
1 & 0 & 0 & 0 & 2 \\
0 & 1 & 0 & 0 & 3 \\
0 & 0 & 1 & 0 & 1 \\
0 & 0 & 0 & 1 & 3
\end{array}
\end{pmatrix}
$$

Таким образом $v = (2v_1 + 3v_3) + (u_1 + 3u_2) = (2, 1, 6, 3) + (-5, -5, 1, 3)$, где $(2, 1, 6, 3) \in Im \ \varphi^{2019}$ и $(-5, -5, 1, 3) \in \ker \psi^{2020}$.

### №4

Для начала найдем харакеристический многочлен оператора $\varphi$:

$$
A =
\begin{pmatrix}
2 & -3 & 6 & -5 \\
1 & -2 & 4 & -3 \\
2 & -2 & 6 & -5 \\
2 & 0 & 4 & -4
\end{pmatrix}
$$

Для дальнейшего удобства приведем ее к УСВ:

$$
\begin{pmatrix}
2 & -3 & 6 & -5 \\
1 & -2 & 4 & -3 \\
2 & -2 & 6 & -5 \\
2 & 0 & 4 & -4
\end{pmatrix}
\sim
\begin{pmatrix}
1 & 0 & 0 & -1 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & \frac{-1}{2} \\
0 & 0 & 0 & 0
\end{pmatrix}
$$

Вместо того чтобы заниматься ужасными вещами и искать хар. многочлен у матрицы 4 на 4, поступим проще:

- Представим, что оператор имеет всего 2 собственных значения $\lambda_1, \lambda_2$
- Мы знаем, что $tr(A) = 2$ - сумма собственных значений матрицы $A$, пусть $m_1, m_2$ кратности $\lambda_1, \lambda_2$ в $\chi_{\varphi}(\lambda)$ соответственно, то есть $m_1 \lambda_1 + m_2 \lambda_2 = 2$. Также знаем, что $m_1 + m_2 = 4$
- Из УСВ: $\det(A) = 0$, то есть $\lambda_2 = 0$. Тогда, если бы мы знали $m_2$, то смогли восстановить $m_1$, а значит и получить $\lambda_1$.
- С лекций знаем, что кратность собственного значения - $k$, на котором происходит стабилизация, то есть $\ker\varphi^{k - 1} \subset \ker \varphi^k = \ker \varphi^{k + 1} = \dots $

Рассмотрим $\varphi^2$:

$$
\begin{pmatrix}
2 & -3 & 6 & -5 \\
1 & -2 & 4 & -3 \\
2 & -2 & 6 & -5 \\
2 & 0 & 4 & -4
\end{pmatrix}^2 =
\begin{pmatrix}
3 & -12 & 16 & -11 \\
2 & -7 & 10 & -7 \\
4 & -14 & 20 & -14 \\
4 & -14 & 20 & -14
\end{pmatrix}
$$

Таким образом, $\dim \ker \varphi^2 = 2$, то есть кратность хотя бы 2.

Рассмотрим $\varphi^3$:

$$
\begin{pmatrix}
3 & -12 & 16 & -11 \\
2 & -7 & 10 & -7 \\
4 & -14 & 20 & -14 \\
4 & -14 & 20 & -14
\end{pmatrix}
\begin{pmatrix}
2 & -3 & 6 & -5 \\
1 & -2 & 4 & -3 \\
2 & -2 & 6 & -5 \\
2 & 0 & 4 & -4
\end{pmatrix}
=
\begin{pmatrix}
4 & -17 & 22 & -15 \\
3 & -12 & 16 & -11 \\
6 & -24 & 32 & -22 \\
6 & -24 & 32 & -22
\end{pmatrix}
$$

Таким образом $\dim \ker \varphi^3 = 2 = \dim \ker \varphi^2$, то есть $m_2 = 2$.

- Тогда $m_1 = 2$, $\lambda_1 = \frac{2}{2} = 1$. То есть, **если** собственных значений ровно 2, то $\chi_{\varphi}(\lambda) = \lambda^2(\lambda - 1)^2$. Для корректности осталось доказать, что $\lambda = 1$ - это собственное значение:

Рассмотрим $(\varphi - E)$:
$$
\begin{pmatrix}
1 & -3 & 6 & -5 \\
1 & -3 & 4 & -3 \\
2 & -2 & 5 & -5 \\
2 & 0 & 4 & -5
\end{pmatrix}
\sim
\begin{pmatrix}
1 & -3 & 6 & -5 \\
0 & 4 & -7 & 5 \\
0 & 0 & -2 & 2 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$

Ранг равен 3, значит определитель 0, то есть это действительно собственное значение.

ч.т.д

Итого имеем $\chi_{\varphi}(\lambda) = \lambda^2(\lambda - 1)^2$.

Также правильно выбрали $\lambda_1 = 1$ как наибольшее по модулю.

Теперь найдем $V^{\lambda_1}, V^{\lambda_2}$.

- Знаем, что $V^{\lambda_1} = \ker(\varphi - \lambda_1 E)^2$, чтобы найди ядро нужно найти ФСР системы $(\varphi - \lambda_1 E)^2x = 0$ (должно получится 2 вектора, так как $m_1$ = 2):

$$
(\varphi - E)^2 =
\begin{pmatrix}
1 & -3 & 6 & -5 \\
1 & -3 & 4 & -3 \\
2 & -2 & 5 & -5 \\
2 & 0 & 4 & -5
\end{pmatrix}^2 =
\begin{pmatrix}
0 & -6 & 4 & -1 \\
0 & -2 & 2 & -1 \\
0 & -10 & 9 & -4 \\
0 & -14 & 12 & -5
\end{pmatrix}
\sim
\begin{pmatrix}
0 & 1 & 0 & \frac{-1}{2} \\
0 & 0 & 1 & -1 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$

Тогда ФСР:
$$
v_1 = (1, *, *, 0) = (1, 0, 0, 0) \\
v_2 = (0, *, *, 2) = (0, 1, 2, 2)
$$

Таким образом: $Im \ \psi = V^{\lambda_1} = \langle v_1, v_2\rangle$. Обозначим $C = (v_1|v_2)$.

- Знаем, что $V^{\lambda_2} = \ker(\varphi - \lambda_2 E)^2$. Тут зададим подпространство как систему с ЛНЗ строками: $(\varphi - \lambda_2 E)^2x = 0$ (должно получится 2 линейно , так как $m_2$ = 2):

$$
\varphi^2 =
\begin{pmatrix}
3 & -12 & 16 & -11 \\
2 & -7 & 10 & -7 \\
4 & -14 & 20 & -14 \\
4 & -14 & 20 & -14
\end{pmatrix}
\sim
\begin{pmatrix}
3 & 0 & 8 & -7 \\
0 & 3 & -2 & 1 \\
\end{pmatrix} = D
$$

Таким образом: $\ker\psi = V^{\lambda_2} = \{y \in \R^4\ | \ Dy = 0\}$

Осталось найти матрицу линейного оператора $\psi$ с заданным образом и ядром. Она равна $CD$:

$$CD =
\begin{pmatrix}
1 & 0 \\
0 & 1 \\
0 & 2 \\
0 & 2
\end{pmatrix}
\begin{pmatrix}
3 & 0 & 8 & -7 \\
0 & 3 & -2 & 1
\end{pmatrix}
=
\begin{pmatrix}
3 & 0 & 8 & -7 \\
0 & 3 & -2 & 1 \\
0 & 6 & -4 & 2 \\
0 & 6 & -4 & 2
\end{pmatrix}
$$

Таким образом, матрица оператора $\psi: \R^4 \rightarrow \R^4$ задается матрицей:
$$
\begin{pmatrix}
3 & 0 & 8 & -7 \\
0 & 3 & -2 & 1 \\
0 & 6 & -4 & 2 \\
0 & 6 & -4 & 2
\end{pmatrix}
$$

### №5

Обозначим за $G$ - матрица перехода от стандартного базиса к базису $g = (g_1|g_2|g_3)$. Т.е. $(g_1|g_2|g_3) = (e_1|e_2|e_3)G$, тогда:

$$
G = (g_1|g_2|g_3) =
\begin{pmatrix}
-1 & -1 & -1\\
1 & 0 & -1\\
1 & 2 & 2
\end{pmatrix}
$$

Тогда получим, что $C = G^{-1}AG$ и отсюда же $A = GCG^{-1}$, то есть если мы сможем восстановить матрицу $C$, то найдем и $A$.

Теперь рассмотрим подробнее $\phi(v) = u$:

$$
\phi(v) = Av = u \\
GCG^{-1}v = u \\
$$
Пусть $\alpha = (\alpha_1|\alpha_2|\alpha_3)^T$ - координаты разложения $v$ по базису $g$, то есть $v = G\alpha$, тогда
$$
GCG^{-1}v = GC\alpha \Rightarrow \\ \Rightarrow
GC\alpha = u
$$

Отсюда получим СЛУ и найдем оставшиеся элементы $C$, а значит и решим задачу.

- Найдем $\alpha$, для этого решим систему $G\alpha = v$:

$$
\begin{pmatrix}
\begin{array}{c c c|c}
-1 & -1 & -1 & -1\\
1 & 0 & -1 & 3\\
1 & 2 & 2 & 1
\end{array}
\end{pmatrix}
\sim
\begin{pmatrix}
\begin{array}{c c c|c}
-1 & -1 & -1 & -1 \\
0 & -1 & -2 & 2 \\
0 & 0 & -1 & 2
\end{array}
\end{pmatrix}
\sim
\begin{pmatrix}
\begin{array}{c c c|c}
1 & 0 & 0 & 1 \\
0 & 1 & 0 & 2 \\
0 & 0 & 1 & -2
\end{array}
\end{pmatrix}
$$
Таким образом $\alpha = (1 \ | \ 2 \ | -2)^T$.

- Рассмотрим теперь уравнение:

$$
GC\alpha = u \\[10pt]
\begin{pmatrix}
-1 & -1 & -1\\
1 & 0 & -1\\
1 & 2 & 2
\end{pmatrix}
\begin{pmatrix}
x & -3 & -4 \\
5 & y & 8 \\
-3 & -6 & z
\end{pmatrix}
\begin{pmatrix}
1\\
2\\
-2
\end{pmatrix}
=
\begin{pmatrix}
-3\\
4\\
5
\end{pmatrix}
\\[10pt]
\begin{pmatrix}
-1 & -1 & -1\\
1 & 0 & -1\\
1 & 2 & 2
\end{pmatrix}
\begin{pmatrix}
x+2 \\
2y-11 \\
-2z-15
\end{pmatrix} =
\begin{pmatrix}
-3\\
4\\
5
\end{pmatrix} \\[10pt]
\begin{pmatrix}
-x-2y+2z+24 \\
x+2z+17 \\
x+4y-4z-50
\end{pmatrix} =
\begin{pmatrix}
-3\\
4\\
5
\end{pmatrix}
$$
То есть:
$$
\begin{cases}
-x-2y+2z+24 = -3\\
x+2z+17 = 4\\
x+4y-4z-50 = 5
\end{cases}
\iff
\begin{cases}
-x-2y+2z = -27\\
x+2z = -13\\
x+4y-4z = 55
\end{cases}
\iff
\begin{pmatrix}
\begin{array}{c c c|c}
-1 & -2 & 2 & -27 \\
1 & 0 & 2 & -13 \\
1 & 4 & -4 & 55
\end{array}
\end{pmatrix}
\sim \\[10pt]
\sim
\begin{pmatrix}
\begin{array}{c c c|c}
-1 & -2 & 2 & -27 \\
0 & -2 & 4 & -40 \\
0 & 0 & 2 & -12
\end{array}
\end{pmatrix}
\sim
\begin{pmatrix}
\begin{array}{c c c|c}
1 & 0 & 0 & -1 \\
0 & 1 & 0 & 8 \\
0 & 0 & 1 & -6
\end{array}
\end{pmatrix} \Rightarrow
\begin{pmatrix}
x\\
y\\
z
\end{pmatrix} =
\begin{pmatrix}
-1\\
8\\
-6
\end{pmatrix}
$$

Таким образом нашли $C$:
$$
C = \begin{pmatrix}
-1 & -3 & -4 \\
5 & 8 & 8 \\
-3 & -6 & -6
\end{pmatrix}
$$

Осталось найти матрицу $A$, по формуле выше: $A = GCG^{-1}$:

- Найдем $G^{-1}$ решая уравнение $GG^{-1} = E$:

$$
\begin{pmatrix}
\begin{array}{c c c|c c c}
-1 & -1 & -1 & 1 & 0 & 0 \\
1 & 0 & -1 & 0 & 1 & 0 \\
1 & 2 & 2 & 0 & 0 & 1
\end{array}
\end{pmatrix}
\sim
\begin{pmatrix}
\begin{array}{c c c|c c c}
1 & 1 & 1 & -1 & 0 & 0 \\
0 & -1 & -2 & 1 & 1 & 0 \\
0 & 1 & 1 & 1 & 0 & 1
\end{array}
\end{pmatrix}
\sim
\begin{pmatrix}
\begin{array}{c c c|c c c}
1 & 1 & 1 & -1 & 0 & 0 \\
0 & 1 & 2 & -1 & -1 & 0 \\
0 & 0 & 1 & -2 & -1 & -1
\end{array}
\end{pmatrix}
\sim \\[10pt]
\sim
\begin{pmatrix}
\begin{array}{c c c|c c c}
1 & 1 & 0 & 1 & 1 & 1 \\
0 & 1 & 0 & 3 & 1 & 2 \\
0 & 0 & 1 & -2 & -1 & -1
\end{array}
\end{pmatrix}
\sim
\begin{pmatrix}
\begin{array}{c c c|c c c}
1 & 0 & 0 & -2 & 0 & -1 \\
0 & 1 & 0 & 3 & 1 & 2 \\
0 & 0 & 1 & -2 & -1 & -1
\end{array}
\end{pmatrix} \Rightarrow \\[10pt]
\Rightarrow
G^{-1} =
\begin{pmatrix}
-2 & 0 & -1 \\
3 & 1 & 2 \\
-2 & -1 & -1
\end{pmatrix}
$$

- Получим, наконец, $A$:

$$
A = GCG^{-1} =
\begin{pmatrix}
-1 & -1 & -1\\
1 & 0 & -1\\
1 & 2 & 2
\end{pmatrix}
\begin{pmatrix}
-1 & -3 & -4 \\
5 & 8 & 8 \\
-3 & -6 & -6
\end{pmatrix}
\begin{pmatrix}
-2 & 0 & -1 \\
3 & 1 & 2 \\
-2 & -1 & -1
\end{pmatrix} = \\[10pt] =
\begin{pmatrix}
-1 & 1 & 2 \\
2 & 3 & 2 \\
3 & 1 & 0
\end{pmatrix}
\begin{pmatrix}
-2 & 0 & -1 \\
3 & 1 & 2 \\
-2 & -1 & -1
\end{pmatrix} =
\begin{pmatrix}
1 & -1 & 1 \\
1 & 1 & 2 \\
-3 & 1 & -1
\end{pmatrix}.
$$
