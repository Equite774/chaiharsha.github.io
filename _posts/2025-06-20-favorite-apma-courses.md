---
layout: post
title:  "My Favorite APMA Courses at Brown"
date:   2025-06-20 13:46:10
categories: math
---
{% newthought 'Over my time at Brown,' %} I have taken nine courses within the Division of Applied Mathematics. Here are some of my favorites.

<!--more-->

<div class="course-block">
  <hr class="course-divider first-divider">
  <div class="course-entry">
    <strong>APMA 1690:</strong> <em>Computational Probability and Statistics</em><br>
    Instructor: Prof. Kun Meng<br>
    Semester: Fall 2024
  </div>
  <hr class="course-divider">
</div>

APMA 1690 is probably the course that has blown my mind the most. The content is not particularly advanced. Broadly, it is a class on Monte Carlo algorithms and how to sample from a distribution. The path of course is quite straightforward, starting with a brief review of probability, before diving into random number generation via the inverse CDF method. Then, upon seeing the computational intractibility of the inverse CDF for higher dimensional sampling, the course briefly pivots to build up the necessary Markov theory to introduce MCMC methods, in particular Metropolis-Hastings and Gibbs sampling, which is then applied to the Ising model.

The coolest part of this course by far is the portion on the Gibbs sampler. I struggle to put into words how cool this algorithm is to me. In almost any instance where we might need to sample from a distribution, we can do so with Gibbs sampling. And it's so simple to understand! Iterate through each dimension/node/random variable, fix everything else, and sample one-dimensionally! I didn't really grasp how amazing this was until one of the homeworks implementing the Gibbs sampler on the Ising model. It felt like Gibbs sampling was a magical solution to any* problem{% sidenote 'nonparametric-bayes' 'In fact, this is only somewhat true. In the Spring of 2025, I participated in a Directed Reading Project on [Nonparametric Bayesian Statistics](https://github.com/Equite774/nonparametric-bayes-drp), in which I learned that Gibbs sampling could not just be used to sample from a given known distribution for Monte Carlo simulations, but additionally to simulate conditional distributions and learn parameters for Bayesian statistics.' %}. And of course, I would be remiss to not discuss Monte Carlo simulations. You can have a problem that would be difficult to solve deterministically, and by the Law of Large Numbers, you can throw Gibbs sampling at it and in return, get a fairly good estimate for the solution.

This class is not particularly difficult. I don't think that getting an A in this course was especially an achievement, nor do I feel particularly proud of the work I did in it. But as it was an inflection point in my life. In retrospect, it's easy for me to say that I was always going to study mathematical statistics, but this class was my Rubicon. It was upon the conclusion of this class that I realized that this was the type of math I wanted to be working with for the rest of my life. And for that, it's easily one of the best classes I've taken at Brown. I highly recommend it to anyone considering it.

<div class="course-block">
  <hr class="course-divider first-divider">
  <div class="course-entry">
    <strong>APMA 1930W:</strong> <em>Probabilities in Quantum Mechanics</em><br>
    Instructor: Prof. Stuart Geman<br>
    Semester: Spring 2025
  </div>
  <hr class="course-divider">
</div>

APMA 1930W is a course about quantum mechanics for people who do not know anything about physics. The first half of this course is simply devoted to building the mathematical framework to be able to describe quantum mechanics: the formulation of the spin state in $$\mathbb{C}^n$$, Dirac bra-ket notation, operators represented as Hermitian matrices, before moving results, such as the uncertainty principle, the Schrödinger equation, and entanglement. Then, time is spent on applications of quantum mechanics: Bell's inequality, teleportation, quantum encryption, the free will theorem, and of course, quantum computing.

This class really does not need any physics background. It really is a course for math people. The first half of this course might as well just be a linear algebra class. Everything is built towards rigorously. On the first day, Professor Geman discussed the famous paper "The Unreasonable Effectiveness of Mathematics in the Natural Sciences," (for which quantum mechanics is an exemplar) and every time we reached a result purely through derivation, he would remind us, *The Unreasonable Effectiveness of Mathematics!* The opening of the course description has become somewhat of a joke among me and some close friends: **We will start from scratch. We will be rigorous, while making a careful account of the (surprisingly few) conceptual assumptions that lead inexporably to consequences that are almost impossible to believe.** Who starts a course description like that? But it's all true! This is one of courses that I have taken where I thought *whether or not this is relevant to my career, I am better off for having taken this class.* It was a truly enlightening experience, and I recommend it to anyone who might be considering it, even if for the sole reason of "I want a review of linear algebra," which you will certainly get a lot of.

It would be a shame if I did not talk about Stu Geman here{% sidenote 'meng' 'Unfortunately, Kun Meng has left Brown University, so I omitted a discussion of him above.' %}. Funnily enough, Professor Geman is the co-inventor of the Gibbs sampler I raved on about before, but he is also an amazing lecturer. Despite a small penchant for digression, Geman has a knack for making a topic feel very intuitive. Of course, he hammers in the rigor as well, but everything just makes sense when he says it. It's a joy to listen to him speak, and a greater joy to speak with him. Every Wednesday, I would go to his office hours to just have conversations with him. Sometimes to review quantum mechanics of course, but usually about topics like deep learning and the cognition of neural networks, the state of ML as a field right now, etc. If you have the luxury of taking a course with him before he retires, spend as much time in his office as you can. You won't regret it.

<div class="course-block">
  <hr class="course-divider first-divider">
  <div class="course-entry">
    <strong>APMA 1360:</strong> <em>Applied Dynamical Systems</em><br>
    Instructor: Prof. Björn Sandstede<br>
    Semester: Spring 2025
  </div>
  <hr class="course-divider">
</div>

I never thought that a differential equations course could be one of my favorite courses of all time. My experience before with differential equations had been a mixed bag. ODEs was fairly easy but rather uninteresting, and my time in PDEs was spent stuck in the trees without being able to see the forest, so to speak. Generally speaking, undergraduate diff eqs lack the rigor to see why we're stuck to only these particular cases, and generally the lack of "completeness" (I use this term loosely) is deeply unsatisfying to me. But the first advice I ever received upon arriving at Brown was to "take a class with Björn." When I had the opportunity, I seized it, and it was absolutely worth it.

This is a class on dynamical systems. We start with parametric ordinary differential equations, in which we try to evaluate what a diff eq or a system of diff eqs might look like (stability, long-term behavior, etc) at different parameter values. We additionally study periodic systems, and spend some time formalizing chaos theory. The course also ends with a final group project, where each group studies a particular application of any of the content from the course. In particular, my group studied an SEIR model, particularly in the case of Ebola, which has some added complexity due to unburied dead bodies.

Despite my misgivings, I am happy to have taken this course, and it was great peek behind the curtains into the world of differential equations. Professor Sandstede is a fantastic lecturer, who makes the content seem much easier than it might actually be. It's fun to be in his class! If you are like me and generally stick to prob/stat, I would highly recommend this course just to broaden your horizons. Like 1930W, it's a course that I feel better off having taken.

# Honorable Mentions

While the above are probably my top three at this moment, there are some other courses, both APMA and not, that I would like to include on this list.

### APMA 1740: Recent Applications of Probability and Statistics

1740 is the pinnacle of undergrad prob/stat at Brown, in my opinion. It really is just a topics course, one part information theory, one part statistical learning{% sidenote 'ml' 'In my opinion, one should take this course before taking **CSCI 1420: Machine Learning**. I think it provides a better introduction and overview to machine learning techniques and the math behind it, and then cs1420 builds on it in a natural way' %}, and one part graphical models. The content of this course is some of the coolest content I have ever learned. The homeworks are absurdly useful in actually understanding what is going on. For instance, I particularly enjoyed learning about kernel density estimation, and the homework on implementing it was just as cool. My only issue with it is that it feels like all three parts of this course should be their own course. For the first third, this is just true, in APMA 1710: Information Theory, but the lack of an APMA course on statistical learning really is quite sad to me.

### CSCI 1520/1952Q: Algorithmic Aspects of Machine Learning

I cannot include this item in a list about APMA courses because it is technically in the CSCI department, but I need to mention it. I love this course. It is taught and structured extremely well. I especially enjoyed how the homeworks were. The more stencil code a homework assignment has, generally the worse it is. This class's homeworks do not have any stencil, it is up to the individual to implement the algorithm from scratch. The first chunk of content is on hash methods(e.g. locality-sensitive hashing, bloom filter), the second is on networks (i.e. PageRank), the third is on linear algebra techniques (NMF, matrix completion), and the last is on theoretical deep learning. As a disclaimer, as any good machine learning course should be, this is much more of a mathematical theory course than a coding course, despite how free the homeworks are. I consider this class to be adding a number of new methods to my toolkit, such that I can now solve a completely different class of applied problems than before.

### CSCI 1010: Theory of Computation

I really love Theory of Computation. The proofs are a bit hand-wavey, and a lot more writing explanations than concise mathematical language, but the content is just so interesting. The course starts with deterministic finite automata, before introducing the nondeterministic version. Then we move through context-free grammars and their equivalent pushdown automata, before finally arriving at Turing machines. We discuss (un)decidability, before moving on to time and space complexity, and of course discussing P vs NP. The love I have for this content is rather pure, and hard to put into words. I feel like in some ways it changed the way I think about problem-solving. I approach, well, everything, from a much more logical angle having taken this course. I break problems down into manageable components. Just take this class. It's healthy for one's development as a computer scientist, and of course P and NP are extremely relevant concepts for anyone using computers to solve problems.