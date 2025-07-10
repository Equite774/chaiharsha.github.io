---
layout: page
title:  "A Proof Of My Favorite Mathematical Result"
date:   2025-07-07 13:46:10
categories: math
---
{% newthought 'The Law of Large Numbers' %} is my favorite mathematical result. Why? The short answer is that the Law of Large Numbers yields Monte Carlo simulations, which allow us to exchange precision and the difficulty of analytical solutions with comparatively mathematically and computationally easy sampling. (The long answer will be saved for some other time) In this post, I will arrive at the (Weak) Law of Large Numbers *ab initio*. <!--more--> I will assume some basic knowledge of set theory, that we have the Axiom of Choice, and that we are working within the extended reals.

## The Probability Measure

Consider a set $$\Omega.$$ We call $$\Omega$$ a **sample space**. We wish to construct a function $$\mathbb{P}:\Omega\to [0,1],$$ which we call a probability function, such that it has a few nice properties:

1) $$\mathbb{P}(\emptyset) = 0$$

2) $$\mathbb{P}(\Omega) = 1$$

Let $$A_1,A_2\ldots\subseteq\Omega.$$ Then...

3) $$\mathbb{P}\left(\bigcup_{i=1}^\infty A_i\right)\leq\sum_{i=1}^\infty\mathbb{P}(A_i)$$

4) $$A_i\cap A_j=\emptyset\,\forall\,i\neq j\implies\sum_{i=1}^\infty\mathbb{P}(A_i) = \mathbb{P}\left(\bigcup_{i=1}^\infty A_i\right)$$

While this certainly seems reasonable, unfortunately, this is not necessarily possible. To see why, let us consider an example.

Take the probability function $$\mathbb{P}:[0,1]\to[0,1].$$ such that $$\mathbb{P}(E+r)=\mathbb{P}(E),$$ with $$r\in\mathbb{Q},$$ i.e. $$\mathbb{P}$$ is translational invariant for rationals. Intuitively, this corresponds with the uniform distribution. We will show that, with the prior assumptions, the uniform distribution results in a disastrous contradiction.

By property 1, we have that $$\mathbb{P}([0,1])=1.$$

Now, define a relation $$\sim$$ such that $$x \sim y \iff x - y \in\mathbb{Q}.$$ We claim that $$\sim$$ is an equivalence relation. For $$x,y,z\in[0,1],$$

1) $$x - x = 0 \in \mathbb{Q}.$$

2) $$x - y \in \mathbb{Q} \iff y - x\in \mathbb{Q}$$ since $$x - y = - (y - x)$$ and $$a\in\mathbb{Q} \iff -a\in\mathbb{Q}.$$

3) $$x - y \in \mathbb{Q} \land y - z \in \mathbb{Q} \implies x - z \in \mathbb{Q},$$ since the rationals are closed under addition.

Since $$\sim$$ is an equivalence relation, we can construct disjoint equivalence classes $$\mathcal{E}_i$$ such that $$\mathcal{E}_i\cap \mathcal{E}_j\neq\emptyset\implies\mathcal{E}_i=\mathcal{E}_j.$$

Using the Axiom of Choice, select an element from each equivalence class $$e_i\in\mathcal{E}_i.$$ Call the set of these selections $$V.$$ Since each element of $$V$$ is in $$[0,1],$$ we necessarily have $$V\subseteq [0,1].$$ We also have, for every $$q\in\mathbb{Q}\cap(0,1),$$ that for all $$x\in V,\, x + q \notin V.$$

Hence, define $$V_q = \{x + q \mod{1}:x\in V\}$$ for $$q\in\mathbb{Q}\cap(0,1).$$ We claim that each $$V_q$$ is pairwise disjoint. Suppose not, that $$V_r\cap V_s\neq\emptyset$$ for $$r \neq s.$$ Then, take $$y\in V_r\cap V_s.$$ Thus, $$y-s\mod 1\in V\land y-r\mod 1\in V.$$ We enforce that $$y - r\mod 1 \neq y-s\mod 1.$$ But then, we clearly have 

$$
(y-r)-(y-s)\mod 1 = s - r\mod 1\in\mathbb{Q}\cap(0,1),
$$ 

a contradiction of the construction of $$V,$$ since this means $$r,s$$ are in the same equivalence class, but we only chose one element from each.

We claim that 

$$
\bigcup_{q\in\mathbb{Q}\cap(0,1)} V_q = [0,1].
$$ 

Consider some $$a\in[0,1].$$ Then $$\exists\, e_a\in V$$ such that $$a - e_a\mod 1 \in\mathbb{Q}\cap(0,1).$$ Then, let $$q = a - e_a\mod 1,$$ so $$a \in V_{q}.$$ 

Now consider $$b\in\bigcup_{q\in\mathbb{Q}\cap(0,1)} V_q.$$ Since each $$V_q$$ is disjoint, without loss of generality, say that $$b\in V_t.$$ Then $$b = v + t\mod 1.$$ Consider $$b < t.$$ Then $$b = v + t - 1\implies b + 1 = v + t.$$ But since $$0\leq v, t\leq 1,$$ we have $$b + 1< 2\implies b < 1.$$ Additionally, we necessarily have that $$v + t > 1$$ here, so $$b > 0.$$ Now, consider $$b\geq t.$$ Then $$v + t < 1,$$ for otherwise, $$b = v + t - 1 < t.$$ Hence, $$b < 1.$$ Additionally, $$v + t > 0,$$ since $$v, t > 0.$$ Hence, $$b\in[0,1].$$

Now, note that each $$V_q = V + q.$$ Hence, since $$\mathbb{P}$$ is translational invariant, we have that $$\mathbb{P}(V_q)=\mathbb{P}(V).$$

With this, we now have that, since $$\bigcup_{q\in\mathbb{Q}\cap(0,1)}=[0,1]$$ and each $$V_q$$ are pairwise disjoint, then 

$$
\mathbb{P}([0,1])=\mathbb{P}\left(\bigcup_{q\in\mathbb{Q}\cap(0,1)} V_q\right)=\sum_{q\in\mathbb{Q}\cap(0,1)}\mathbb{P}(V_q).
$$

Clearly, $$\mathbb{P}([0,1])=\mathbb{P}\left(\bigcup_{q\in\mathbb{Q}\cap(0,1)} V_q\right) = 1.$$ Now, however, we have 

$$
\sum_{q\in\mathbb{Q}\cap(0,1)} \mathbb{P}(V_q) = \sum_{q\in\mathbb{Q}\cap(0,1)}\mathbb{P}(V).
$$ 

Now, if 

$$
\mathbb{P}(V)=0,$$ then $$\sum_{q\in\mathbb{Q}\cap(0,1)}\mathbb{P}(V_q) = \sum_{q\in\mathbb{Q}\cap(0,1)}\mathbb{P}(V) = 0.
$$ 

But if $$\mathbb{P}(V)>0,$$ then 

$$
\sum_{q\in\mathbb{Q}\cap(0,1)}\mathbb{P}(V_q) = \sum_{q\in\mathbb{Q}\cap(0,1)}\mathbb{P}(V) = \infty.
$$ 

Both of these cases lead to a contradiction. Hence, we have constructed a set, that under certain assumptions, cannot have this probability function.

How do we rescue this? We have to restrict the sets upon which our probability function (which we will soon establish as a **probability measure**) can act upon (i.e. measure). To do so, we introduce the concept of an **algebra.** An algebra is simply a collection sets that is closed under finite union and complement. That is, let $$\mathcal{A}$$ be an algebra, and let $$X, X_1,\ldots,X_n\in\mathcal{A}.$$ Then $$\bigcup_{i=1}^n X_i\in\mathcal{A}\land X^C\in\mathcal{A}.$$

We introduce an algebra for its extension: the **$$\sigma$$-algebra**. A $$\sigma$$-algebra is closed under countable union and complement. That is, for $$\sigma$$-algebra $$\mathcal{M},$$ if $$X,X_1,X_2,\ldots\in\mathcal{M},$$ then $$\bigcup_{i=1}^\infty X_i\in\mathcal{M}\land X^C\in\mathcal{M}.$$

We say that $$\mathcal{M}$$ is a $$\sigma$$-algebra of $$\Omega$$ if all elements in $$\mathcal{M}$$ are subsets of $$\Omega$$ and $$\Omega\in\mathcal{M}.$$

Now, we say that sets in $$\mathcal{M}$$ are, by definition, **measurable**. Hence, we may construct our probability measure, $$\mathbb{P},$$ such that we have $$\mathbb{P}(\Omega)=1,\,\mathbb{P}(\emptyset)=0,\,$$ for any $$X\in\mathcal{M},\mathbb{P}(A)\geq 0,$$ and for disjoint $$X_1,X_2\ldots,\, \mathbb{P}\left(\bigcup_{i=1}^\infty X_i\right)=\sum_{i=1}^\infty \mathbb{P}(X_i).$$ Hence, we have a more rigorous definition of probability work with.

We call the collection $$(\Omega,\mathcal{M},\mathbb{P})$$ a **probability space**, or a probability triple.

*Note: I am ommitting the proof of existence of the probability measure. If you are interested, the keywords are outer measure and Carathéodory criterion.*

## Integration / Expected Value

Given a probability space $$(\Omega,\mathcal{M},\mathbb{P}),$$ A function $$f:\Omega\to\mathbb{R}$$  is said to be **measurable** iff $$\forall\,t\in\mathbb{R},$$ 

$$
\{x\in\Omega:f(x)>t\}\in\mathcal{M}.
$$

We claim that given two measurable functions $$f$$ and $$g,$$ and a constant $$c,$$ we have that $$f + g$$ is measurable and $$cf$$ is measurable.

Consider $$\{x\in\Omega:f(x)+g(x)>t\}.$$ Note that $$f(x) + g(x) > t\iff f(x) > t - s \land g(x) > s\,\forall s.$$ Then, 

$$
\{x\in\Omega:f(x)+g(x)>t\} = \bigcup_{s\in\mathbb{Q}} \left(\{x\in\Omega:f(x)>t - s\}\cap\{x\in\Omega:g(x)>s\}\right).
$$ 

It is trivial that $$f + s$$ is measurable, and since $$\mathbb{M}$$ is closed under countable union, we are done.

Now, we consider cases. If $$c > 0,$$ then $$\{x\in\Omega:f(x)>t/c\}\in\mathcal{M}.$$ If $$c < 0,$$ then $$\{x\in\Omega:-f<-t/c\}$$ is also measurable, because $$f$$ measurable implies $$-f$$ measurable. And finally if $$c=0,$$ then clearly 

$$
\{x\in\Omega:cf(x)>t\}=\begin{cases}\Omega\text{ if }t < 0 \\ \emptyset\text{ if }t \geq 0\end{cases}
$$ 

Hence, we are done here too.

Now, given a set $$E\in\mathcal{M},$$ consider the indicator function, which we call the **characteristic function**, $$\chi_E:\Omega\to\{0,1\}$$ such that 

$$
\chi_E(x)=\begin{cases} 1 \text{ if } x\in E \\ 0 \text{ if }x\notin E \end{cases}
$$ 

We claim that $$\chi_E$$ is measurable.

Let $$t < 0.$$ Then $$\{x\in\Omega:f(x)>t\}=\Omega\in\mathcal{M}.$$ Similarly, letting $$t \geq 1$$ yields $$\{x\in\Omega:f(x)>t\}=\emptyset\in\mathcal{M}.$$ Now, let $$t\in[0,1).$$ Then $$\{x\in\Omega:f(x)>t\}=E\in\mathcal{M}.$$

The definition of an integral follows: $$\int \chi_E\,d\mathbb{P}=\mathbb{P}(E).$$

Now, we may define **simple functions**. Let $$E_1,\ldots,E_n\in\mathcal{M},$$ with corresponding sequence $$a_1,\ldots,a_n,$$ in which $$a_i<\infty$$ and $$a_i\neq a_j\,\forall E_i\cap E_j=\emptyset.$$ A simple function is a function 

$$
\phi = \sum_{i=1}^n a_i\chi_{E_i}.
$$ 

Here, we define the integral by 

$$
\int\phi\,d\mathbb{P} = \sum_{i=1}^n a_i\mathbb{P}(E_i).
$$ 

Intuitively, while the Riemann integral works by slicing verticle rectangles, this integral works by slicing *horizontal rectangles*.

We claim that this integral is linear, i.e. 

$$
\int c\phi\,d\mathbb{P} = c\int\phi\,d\mathbb{P}
$$ 

and 

$$
\int \phi + \psi\,d\mathbb{P} = \int\phi\,d\mathbb{P} + \int\psi\,d\mathbb{P}.
$$

First, we have $$\int c\phi\,d\mathbb{P} = \sum_{i=1}^n ca_i\mathbb{P}(E_i) = c \sum_{i=1}^n a_i\mathbb{P}(E_i) = c\int\phi\,d\mathbb{P}.$$

Now, let $$\phi = \sum_{i=1}^n a_i\chi_{E_i}$$ and $$\psi = \sum_{j=1}^m b_j\chi_{F_j}$$ for measurable $$\{E_i\}_{i=1}^n, \{F_j\}_{j=1}^m.$$ 

Then 

$$
\int \phi\,d\mathbb{P} + \int\phi\,d\mathbb{P} = \sum_{i=1}^n a_i\mathbb{P}(E_i) + \sum_{j=1}^m b_j\mathbb{P}(F_j).
$$ 

We demand a standard representation, which is achievable as we can perform a finite number of zero-measure set unions with zero coefficient. Hence, we have $$E_i = \bigcup_{j=1}^m E_i\cap F_j$$ and $$F_j = \bigcup_{i=1}^n E_i\cap F_j.$$ 

Therefore, 

$$
\sum_{i=1}^n a_i\mathbb{P}(E_i) + \sum_{j=1}^m b_j\mathbb{P}(F_j) = \sum_{i=1}^n a_i\mathbb{P}\left(\bigcup_{j=1}^m E_i\cap F_j\right) + \sum_{j=1}^m b_j\mathbb{P}\left(\bigcup_{i=1}^n E_i\cap F_j\right).
$$

Now, since we have a disjoint union, we can rewrite this as 

$$
\sum_{i=1}^n a_i\sum_{j=1}^m \mathbb{P}(E_i\cap F_j) + \sum_{j=1}^m b_j\sum_{i=1}^n\mathbb{P}(E_i\cap F_j).
$$ 

Rearranging, we find 

$$
\sum_{i=1}^n\sum_{j=1}^m a_i\mathbb{P}(E_i\cap F_j) + \sum_{i=1}^n\sum_{j=1}^m b_i\mathbb{P}(E_i\cap F_j),
$$

which can be factored. Hence, we have 
 
$$
\int \phi\,d\mathbb{P} + \int\phi\,d\mathbb{P} = \sum_{i=1}^n\sum_{j=1}^m (a_i+b_j)\mathbb{P}(E_i\cap F_j).
$$

Now, we seek the formulation of $$\int \phi + \psi \,d\mathbb{P}.$$ We have 

$$
\phi + \psi = \sum_{i=1}^n a_i\chi_{E_i} + \sum_{j=1}^m b_j\chi_{F_j}.
$$

Before we proceed, we must show that for $$A,B$$ such that $$A\cap B = \emptyset,$$ we have $$\chi_{A\cup B} = \chi_A + \chi_B.$$ This follows immediately, since $$x\in A\iff x\notin B$$ and its contrapositive are true.

Hence, we have the representation 

$$
\sum_{i=1}^n a_i\chi_{\bigcup_{j=1}^m E_i\cap F_j} + \sum_{j=1}^m b_j\chi_{\bigcup_{i=1}^n E_i\cap F_j} = \sum_{i=1}^n a_i\sum_{j=1}^m \chi_{E_i\cap F_j} + \sum_{j=1}^m b_j\sum_{i=1}^m \chi_{E_i\cap F_j}.
$$ 

Rearranging, we obtain 

$$
\sum_{i=1}^n\sum_{j=1}^m a_i\chi_{E_i\cap F_j} + \sum_{i=1}^n\sum_{j=1}^m b_j\chi_{E_i\cap F_j}.
$$ 

This is factorable, which yields the representation: 

$$
\phi + \psi = \sum_{i=1}^n\sum_{j=1}^m (a_i+b_j)\chi_{E_i\cap F_j}.
$$ 

Hence, the integral 

$$
\int \phi + \psi\,d\mathbb{P} = \sum_{i=1}^n\sum_{j=1}^m(a_i+b_j)\mathbb{P}(E_i\cap F_j),
$$ 

the same representation as before. Therefore we have linearity.

Now, we define the **Lebesgue integral** of a given function $$f:\Omega\to[0,\infty]$$ on $$(\Omega,\mathcal{M},\mathbb{P})$$ by 

$$
\int_\Omega f\,d\mathbb{P} = \sup_{\phi \leq f}\int_\Omega \phi\,d\mathbb{P}
$$

where $$\phi$$ is a simple function. We say a function is **integrable** if $$\int_{\Omega} f\,d\mathbb{P}<\infty.$$

That $$f \geq g \implies \int_\Omega f \,d\mathbb{P}\geq \int_\Omega g \,d\mathbb{P}$$ follows immediately from the definitions of Lebesgue integration and the supremeum. For linearity, we have that $$\int_\Omega cf\,d\mathbb{P} = c\int_\Omega f\,d\mathbb{P}$$ follows immediately from the definition of Lebesgue integration and the same property on simple functions. To show that $$\int_\Omega f + g\,d\mathbb{P} = \int_\Omega f \,d\mathbb{P} + \int_\Omega g\,d\mathbb{P}$$ requires the **Monotone Convergence Theorem**.

Let $$\{f_n\}_{i=1}^\infty$$ be a monotone-increasing sequence of measurable functions whose limit is $$f.$$ Then 

$$
\int_{\Omega} \lim_{n\to\infty} f_n\,d\mathbb{P} = \lim_{n\to\infty} \int_{\Omega} f_n\,d\mathbb{P}.
$$

We have $$f_n\leq f$$ by monotonicity and so it follows that 

$$
\int_{\Omega}f_n\,d\mathbb{P} \leq \int_{\Omega} f\,d\mathbb{P} = \int_{\Omega} \lim_{n\to\infty} f_n\,d\mathbb{P}.
$$

Since the sequence of integrals is bounded above, the limit exists, which is: 

$$
\lim_{n\to\infty} \int_{\Omega}f_n\,d\mathbb{P} \leq \int_{\Omega} \lim_{n\to\infty} f_n\,d\mathbb{P}.
$$

To prove the other direction, let $$0\leq\phi\leq f$$ be a simple function and let $$\alpha\in(0,1).$$ Let 

$$
A_n = \{x\in\Omega:f_n(x) \geq \alpha\phi(x)\}.
$$

Since $$\{f_n\}$$ is monotone increasing, we have that $$A_1\subseteq A_2\subseteq\ldots\subseteq A_n\subseteq\ldots.$$ We also have that $$\bigcup_{i=1}^\infty A_i = \Omega$$ since for each $$x\in\Omega,$$ for all $$\varepsilon > 0$$ there exists an $$n$$ for which $$f_n(x)$$ lies within an $$\varepsilon$$-ball of $$f(x).$$ Since $$f(x)>\alpha\phi(x),$$ we can always choose an $$n$$ large enough such that $$f_n(x)\geq\alpha\phi(x).$$

We see that 

$$
\int_\Omega f_n\,d\mathbb{P} \geq \int_{A_n} f_n\,d\mathbb{P} \geq \alpha\int_{A_n}\phi\,d\mathbb{P}.
$$

Since $$\phi$$ is simple, it may be written as 

$$
\phi = \sum_{i=1}^k c_i\chi_{E_i}.
$$

Then, we have 

$$
\int_{A_n} \phi\,d\mathbb{P} = \sum_{i=1}^k c_i\mathbb{P}(E_i\cap A_n).
$$

Taking the limit in $$n,$$ however, yields

$$
\lim_{n\to\infty} \int_{A_n} \phi\,d\mathbb{P} = \int_\Omega \phi\,d\mathbb{P} = \sum_{i=1}^k c_i\mathbb{P}(E_i) = \lim_{n\to\infty} \sum_{i=1}^k c_i\mathbb{P}(E_i\cap A_n).
$$

Therefore, if we take the same limit before, we find 

$$
\lim_{n\to\infty}\int_\Omega f_n\,d\mathbb{P} \geq \lim_{n\to\infty}\int_{A_n} f_n\,d\mathbb{P} \geq \lim_{n\to\infty}\alpha\int_{A_n}\phi\,d\mathbb{P} = \alpha\int_\Omega\phi\,d\mathbb{P}.
$$

Rearranging, this is 

$$
\lim_{n\to\infty}\int_\Omega f_n\,d\mathbb{P} \geq \alpha\int_\Omega\phi\,d\mathbb{P}.
$$

Since $$t\in(0,1)$$ we can say that 

$$
\lim_{n\to\infty}\int_\Omega f_n\,d\mathbb{P} \geq \int_\Omega\phi\,d\mathbb{P}.
$$

Hence, we may take the supremum over all $$\phi\leq f$$ and we get the desired result:

$$
\lim_{n\to\infty}\int_\Omega f_n\,d\mathbb{P} \geq \sup_{\phi\leq f}\int_\Omega\phi\,d\mathbb{P} = \int_\Omega f\,d\mathbb{P}.
$$

With the Monotone Convergence Theorem, we may prove the linearity of the Lebesgue integral of nonnegative functions.

Let $$\{\phi_n\}_{n=1}^\infty$$ and $$\{\psi_n\}_{n=1}^\infty$$ be sequences of nonnegative simple functions such that $$\lim_{n\to\infty}\phi_n=f$$ and $$\lim_{n\to\infty}\psi_n=g$$ pointwise for nonnegative functions $$f$$ and $$g.$$ Then 

$$
\lim_{n\to\infty}\phi_n + \lim_{n\to\infty}\psi_n = \lim_{n\to\infty}\phi_n+\psi_n = f + g.
$$

Hence, invoking the linearity of the Lebesgue integral of simple functions and the Monotone Convergence Theorem, we have 

$$
\int_{\Omega} f+g \,d\mathbb{P} = \int_{\Omega} \lim_{n\to\infty}\phi_n+\psi_n \,d\mathbb{P} = \lim_{n\to\infty}\int_{\Omega} \phi_n+\psi_n \,d\mathbb{P} 
$$

$$
= \lim_{n\to\infty}\int_\Omega\phi_n\,d\mathbb{P} + \lim_{n\to\infty}\int_\Omega\psi_n\,d\mathbb{P} = \int_\Omega\lim_{n\to\infty}\phi_n\,d\mathbb{P} + \int_\Omega\lim_{n\to\infty}\psi_n\,d\mathbb{P} = \int_\Omega f\,d\mathbb{P}+\int_\Omega g\,d\mathbb{P}.
$$

Now, we transition the Lebesgue Integral from nonnegative functions to any general function. For any general function $$f,$$ we can define $$f^+ = \max(0,f)$$ and $$f^-=\max(-f,0).$$ Then $$f = f^+ - f^-.$$ Then 

$$
\int_{\Omega} f\,d\mathbb{P} = \int_{\Omega} f^+-f^-\,d\mathbb{P} = \int_{\Omega} f^+\,d\mathbb{P} - \int_{\Omega} f^-\,d\mathbb{P}.
$$

By a notational change, we find that a **random variable** $$X$$ is just a measurable function on the sample space $$\Omega.$$ Then, we define the **expected value** of a random variable to be $$\mathbb{E}[X] = \int_{\Omega} X\,d\mathbb{P}.$$

## Markov's Inequality

Now, we prove **Markov's Inequality**, which states that, in a probability space $$(\Omega,\mathcal{M},\mathbb{P}),$$ for a measurable random variable $$X$$ such that $$\mathbb{E}[\|X\|^p]=\int_\Omega \|X\|^p\,d\mathbb{P}<\infty,$$ then 

$$
\mathbb{P}(\|X\|>\varepsilon)\leq\frac{\mathbb{E}[\|X\|^p]}{\varepsilon^p}\,\forall\,\varepsilon > 0.
$$

Now, we must prove Markov's inequality. Let $$A_\varepsilon = \{\omega\in\Omega : \mathbb{P}(\|X(\omega)\|)>\varepsilon\}\subseteq \Omega.$$ Additionally, clearly $$A_\varepsilon\in\mathcal{M},$$ since $$A$$ takes the form of the condition for a measurable function.

Then, given $$x\in X,$$ we have $$\|x\|^p \geq \varepsilon^p.$$ Hence, we have 

$$
\mathbb{E}[\|X\|^p] = \int_\Omega \|x\|^p d\mathbb{P}\geq \int_{A_\varepsilon} \|x\|^p\,d\mathbb{P}\geq \int_{A_\varepsilon} \varepsilon^p\,d\mathbb{P} = \varepsilon^p\mathbb{P}(A_\varepsilon) = \varepsilon^p\mathbb{P}(\|X\| > \varepsilon).
$$

Rearranging, we immediately find that 

$$
\mathbb{P}(\|X\|>\varepsilon)\leq\frac{\mathbb{E}[\|X\|^p]}{\varepsilon^p}.
$$ 

Since we added no additional assumptions on $$\varepsilon,$$ this is true for all $$\varepsilon > 0.$$

## Variance

Now, we introduce **variance**. The variance of a random variable is defined by $$\text{Var}(Z) = \mathbb{E}[(Z-\mathbb{E}[Z])^2].$$

We can also write this as

$$
\text{Var}(Z) = \mathbb{E}[(Z-\mathbb{E}[Z])^2] = \mathbb{E}[Z^2 - 2Z\mathbb{E}[Z]+\mathbb{E}[Z]^2] = \mathbb{E}[Z^2]-2\mathbb{E}[Z]\mathbb{E}[Z]+\mathbb{E}[Z]^2 = \mathbb{E}[Z^2]-\mathbb{E}[Z]^2.
$$

We claim that, for some constant $$c,$$

$$
\text{Var}(cZ)=c^2\text{Var}(Z).
$$

We have 

$$
\text{Var}(cZ) = \mathbb{E}[(cZ - \mathbb{E}[cZ])^2] = \mathbb{E}[(cZ-c\mathbb{E}[Z])^2] = \mathbb{E}[(c(Z - \mathbb{E}[Z]))^2] = \mathbb{E}[c^2(Z - \mathbb{E}[Z])^2] = c^2\mathbb{E}[(Z - \mathbb{E}[Z])^2]
$$

by simply evoking the linearity of expectation (i.e. the linearity of the Lebesgue integral).

There is another property of variance we need, but it requires the concept of independence to continue.

A collection of random variables $$\{X_i\}_{i=1}^n$$ on a probability space are considered **independent** if, for measurable sets $$\{A_i\}_{i=1}^n$$ we have

$$
\mathbb{P}(X_1\in A_1,\ldots,X_n\in A_n) = \prod_{i=1}^n \mathbb{P}(X_i\in A_i).
$$

We claim that if we have measurable, twice-differentiable random variables $$X,Y$$ then 

$$
\mathbb{E}[XY] = \mathbb{E}[X]\mathbb{E}[Y]
$$

if $$X$$ and $$Y$$ are independent.

First, consider when $$X$$ and $$Y$$ are simple functions, i.e. $$X = \sum_{i=1}^n a_i\chi_{E_i}$$ and $$Y = \sum_{j=1}^m b_j\chi_{F_j}$$ for collections of measurable sets $$\{E_i\}_{i=1}^n$$ and $$\{F_j\}_{j=1}^m.$$

Then 

$$
XY = \sum_{i=1}^n\sum_{j=1}^m a_ib_j\chi_{E_i}\chi_{F_j} = \sum_{i=1}^n\sum_{j=1}^m a_ib_j\chi_{E_i\cap F_j}.
$$

$$
\mathbb{E}[XY] = \int_\Omega XY\,d\mathbb{P} = \sum_{i=1}^n\sum_{j=1}^m a_ib_j\mathbb{P}(E_i\cap F_j).
$$

By independence,

$$
\sum_{i=1}^n\sum_{j=1}^m a_ib_j\mathbb{P}(E_i\cap F_j) = \sum_{i=1}^n\sum_{j=1}^m a_ib_j\mathbb{P}(E_i)\mathbb{P}(F_j).
$$

Then, we have 

$$
\sum_{i=1}^n\sum_{j=1}^m a_ib_j\mathbb{P}(E_i)\mathbb{P}(F_j) = \sum_{i=1}^n a_i\mathbb{P}(E_i)\sum_{j=1}^m b_j\mathbb{P}(F_j) = \mathbb{E}[X]\mathbb{E}[Y].
$$

Hence, $$\mathbb{E}[XY] = \mathbb{E}[X]\mathbb{E}[Y]$$ for simple functions. However, we wish to show this for all random variables. By a prior argument, we can decompose a signed function into two nonnegative functions and apply linearity, so it suffices to show equality for nonnegative random variables.

Similar to linearity, we would like to show that a seqence of simple functions converges to our random variables. But since we need $$\{X_n\}$$ and $$\{Y_n\}$$ to converge together, so we will construct a particular monotonic sequence of functions. Consider the sequence of "staircase" functions $$\{\alpha_n\}$$ such that 

$$
\alpha_n = \begin{cases}
    0 \text{ if }x=0 \\ (i-2)2^{-n}\text{ if }(i-1)2^{-n}<x\leq i2^{-n}\leq n,\, i\in\mathbb{N} \\ n\text{ if } x>n.
\end{cases}
$$

Clearly, this is simple and monotonic. Then, given the nonnegative function $$f,$$ define the sequence $$\{f_n\}$$ by $$f_n=\alpha_n\circ f.$$ We claim that $$\lim_{n\to\infty} f_n = f.$$

If $$f(x)=0,$$ then so does $$f_n(x),$$ so clearly $$\|f(x)-f_n(x)\|<\varepsilon\,\forall\varepsilon>0.$$

Now, consider $$0<f(x)<\infty.$$ Choose an arbitrary $$\varepsilon>0.$$ Then, there exists an $$n$$ such that $$2^{-n}<\varepsilon.$$ Hence, we have 

$$
\|f_n(x)-f(x)\| \leq 2^{-n} < \varepsilon.
$$

Finally, consider $$f(x)=\infty.$$ Then, since as $$n\to\infty,$$ we have $$f_n(x)\to\infty,$$ this case is also treated, and $$f_n(x)\to f(x).$$

Now, let $$\{X_n\}_{n=1}^\infty$$ and $$\{Y_n\}_{n=1}^\infty$$ be monotone-increasing sequences of simple functions defined by 

$$
X_n = \alpha_n \circ X
$$

and

$$
Y_n = \alpha_n \circ Y
$$

respectively. Since both $$X_n$$ and $$Y_n$$ are monotone-increasing, so is their product. Now, we just need to argue that $$\lim_{n\to\infty}X_nY_n=XY.$$

If either $$X$$ or $$Y$$ is 0, then $$X_nY_n$$ is also 0. If either is $$\infty,$$ then $$X_nY_n\to\infty$$ as $$n\to\infty$$ as well.

If both both $$0<X,Y<\infty,$$ then for a given $$\varepsilon>0,$$ there exists $$n$$ such that $$2^{-n}<\varepsilon.$$ Then 

$$
|X_nY_n - XY| < \|2^{-n}2^{-n}\| = \|2^{-2n}\| < \|2^{-n}\| \leq \varepsilon.
$$

Then, we have 

$$
\mathbb{E}[X_nY_n] = \mathbb{E}[X_n]\mathbb{E}[Y_n]
$$

since $$X_n$$ and $$Y_n$$ are simple functions. Taking the limit as $$n\to\infty,$$ by the Monotone Convergence Theorem, we have 

$$
\lim_{n\to\infty}\mathbb{E}[X_nY_n] = \mathbb{E}[XY] = \mathbb{E}[X]\mathbb{E}[Y] = \lim_{n\to\infty}\mathbb{E}[X_n]\mathbb{E}[Y_n].
$$

Hence, we are done. This allows us to show the other property that we need, which is that if $$X$$ and $$Y$$ are independent, then $$\text{Var}(X + Y) =\text{Var}(X) + \text{Var}(Y).$$

The alternate formula of variance gives us 

$$
\text{Var}(X+Y) = \mathbb{E}[(X+Y)^2] - \mathbb{E}[E+Y]^2.
$$

We take these individually:

$$
\mathbb{E}[(X+Y)^2] = \mathbb{E}[X^2+2XY+Y^2] = \mathbb{E}[X^2] + 2\mathbb{E}[XY] + \mathbb{E}[Y^2]
$$

and 

$$
\mathbb{E}[X+Y]^2 = \mathbb{E}[X+Y]\mathbb{E}[X+Y] = \mathbb{E}[X]^2 + 2\mathbb{E}[X]\mathbb{E}[Y] + \mathbb{E}[Y]^2.
$$

Subtracting, we find

$$
\mathbb{E}[X^2] + 2\mathbb{E}[XY] + \mathbb{E}[Y^2] - \mathbb{E}[X]^2 - 2\mathbb{E}[X]\mathbb{E}[Y] - \mathbb{E}[Y]^2 = \mathbb{E}[X^2] - \mathbb{E}[X]^2 + \mathbb{E}[Y^2] - \mathbb{E}[Y]^2 + 2\mathbb{E}[XY] - 2\mathbb{E}[X]\mathbb{E}[Y].
$$

Hence, 

$$
\text{Var}(X+Y) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 + \mathbb{E}[Y^2] - \mathbb{E}[Y]^2 + 2\mathbb{E}[XY] - 2\mathbb{E}[X]\mathbb{E}[Y] = \text{Var}(X) + \text{Var}(Y)  +2\mathbb{E}[XY] - 2\mathbb{E}[X]\mathbb{E}[Y].
$$

However, since $$X$$ and $$Y$$ are independent, we find 

$$
\text{Var}(X+Y) = \text{Var}(X) + \text{Var}(Y)  +2\mathbb{E}[XY] - 2\mathbb{E}[X]\mathbb{E}[Y] = \text{Var}(X) + \text{Var}(Y)  +2\mathbb{E}[XY] - 2\mathbb{E}[XY] = \text{Var}(X) + \text{Var}(Y)
$$

and we are done.

Now, we may return to Markov's Inequality. Assuming that $$X$$ is measurable and twice-integrable, we substitute $$X = Z - \mathbb{E}[Z]$$ and $$p = 2$$ into Markov's Inequality to find 

$$
\mathbb{P}(\|Z - \mathbb{E}[Z]\| > \varepsilon)\leq\frac{\mathbb{E}[\|Z - \mathbb{E}[Z]\|^2]}{\varepsilon^2} = \frac{\text{Var}(Z)}{\varepsilon^2}.
$$

This is called **Chebyshev's Inequality**.

## Weak Law of Large Numbers

We say that a collection of random variables $$\{X_i\}_{i=1}^n$$ are **identically distributed** if, for every measurable set $$A\subseteq\Omega,$$ we have 

$$
\mathbb{P}(X_1\in A) = \mathbb{P}(X_2\in A) = \ldots = \mathbb{P}(X_n\in A).
$$

It follows that 

$$
\mathbb{E}[X_1] = \ldots = \mathbb{E}[X_n]
$$

and

$$
\text{Var}(X_1) = \ldots = \text{Var}(X_n).
$$

This yields the idea of a sequence of random variables being **independent and identically distributed**, or "i.i.d." This is important to the Law of Large Numbers.

Now, we may finally move onto the Weak Law of Large Numbers. Given an i.i.d. sequence of random variables, $$\{X_i\}_{i=1}^n,$$ such that $$\mathbb{E}[X_i]=\mu$$ and $$\text{Var}[X_i]=\sigma^2<\infty,$$ we have that for the sample mean 

$$
\bar{X} = \frac{1}{n}\sum_{i=1}^n X_i,
$$ 

$$
\mathbb{E}[\bar{X}]=\mu
$$ 

and 

$$
\text{Var}(\bar{X}) = \frac{\sigma^2}{n}.
$$ 

For the prior, we have 
$$
\mathbb{E}\left[\frac{1}{n}\sum_{i=1}^n X_i\right] = \frac{1}{n}\sum_{i=1}^n\mathbb{E}[X_i] = \frac{1}{n}n\mu=\mu
$$

by the linearity of expectation.

For the latter, see that 

$$
\text{Var}(\bar{X}) = \text{Var}\left(\frac{1}{n}\sum_{i=1}^n X_i\right)=\frac{1}{n^2}\sum_{i=1}^n \text{Var}(X_i) = \frac{1}{n^2} n\sigma^2 = \frac{\sigma^2}{n}
$$

by the properties of variance as proven above.

The Weak Law of Large Numbers states that given an i.i.d. sequence of random variables $$\{X_i\}_{i=1}^n,$$ each with $$\mathbb{E}[X_i]=\mu$$ and $$\text{Var}[X_i]=\sigma^2<\infty,$$ we have that 

$$
\lim_{n\to\infty}\mathbb{P}(\|\bar{X} - \mu\| > \varepsilon) = 0\,\forall\,\varepsilon>0.
$$

We invoke Chebyshev's inequality. We have 

$$
\mathbb{P}(\|\bar{X} - \mathbb{E}[\bar{X}]\| > \varepsilon)\leq\frac{\text{Var}(\bar{X})}{\varepsilon^2}.
$$

However, since we know $$\text{Var}(\bar{X}) = \frac{\sigma^2}{n},$$ we simplify the right side: 

$$
\frac{\text{Var}(\bar{X})}{\varepsilon^2} = \frac{\sigma^2}{n}\cdot\frac{1}{\varepsilon^2} = \frac{\sigma^2}{n\varepsilon^2}.
$$ 

Then we have 

$$
\mathbb{P}(\|\bar{X} - \mathbb{E}[\bar{X}]\| > \varepsilon)\leq\frac{\sigma^2}{n\varepsilon^2}.
$$

Now, we simply take $$n$$ to infinity: 

$$
\lim_{n\to\infty}\mathbb{P}(\|\bar{X} - \mathbb{E}[\bar{X}]\| > \varepsilon)\leq\lim_{n\to\infty}\frac{\sigma^2}{n\varepsilon^2} = 0.
$$ 

We also have

$$
\lim_{n\to\infty}\mathbb{P}(\|\bar{X} - \mathbb{E}[\bar{X}]\| > \varepsilon)\geq 0
$$

because the probability lies in $$[0,1],$$ which is closed and thus includes all limit points, so we have 

$$
\lim_{n\to\infty}\mathbb{P}(\|\bar{X} - \mathbb{E}[\bar{X}]\| > \varepsilon) = \lim_{n\to\infty}\mathbb{P}(\|\bar{X} - \mu\| > \varepsilon) = 0,
$$ 

and we are finally done.

## Reflection

I must say, this blog post took much longer to write than I expected it to take when I started it a little over two weeks ago. While almost all of the measure theory and probability that I have presented is mathematics that I have learned and am familiar with, to actually collect and reproduce it here from scratch made me realize just how much actually goes into the Weak Law of Large Numbers. I believe that I have provided the almost the infimum of concepts necessary to achieve this proof, it is just that the infimum was larger than I expected. Some of the the things that I did not go into this expecting to need to prove was the linearity of the Lebesgue integral (as we have seen, it is *not* trivial and required the Monotone Convergence Th'm) and the notion of independent and identically distributed. In the back of my head I knew that these were important concepts I would need to discuss, the scope of their proof was much larger than I remembered. This retroactively made my early decision to omit covering outer measures, Carathéodory's criterion, and the exitence of measures a bit of a blessing, despite it decreasing the rigor involved. I am quite happy that I did this, as it was a nice refresher of both measure theory and measure-theoretic probability for me, and some of these proofs have clicked much more nicely in my brain that I initially had.