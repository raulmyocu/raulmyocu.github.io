---
title: The Halting Problem for People in a Hurry
layout: post
post-image: "https://www.coopertoons.com/education/haltingproblem/haltingproblem_alan.jpg"
description: A simple review over computable numbers and the halting problem.
tags:
- turing
- halting problem
- entscheidungsproblem
- computer science
- theory of computation
---

In this post we will review the historical context of Alan Turing's paper
***On Computable Numbers with a Application to the Entscheidungsproblem***,
as well as a basic explanation of the halting problem and its contradiction.

Image Source: [Coopertoons](https://www.coopertoons.com/education/haltingproblem/haltingproblem.html)

---



## Hilbert's Program

It all began with this guy who comes by the name of *David Hilbert*.

[//]: # (David Hilbert Image)

who in the 1920's proposed a research program with the aim of providing mathematics
with a secure foundation. This should include at least the following:

* **Completeness**: Every statement's veracity should be possible to determine.
* **Consistency**: No contradiction should be obtained in the formalism of mathematics.
* **Decidability**: An algorithm to decide the truth or falsity of any statement.

Years later, another guy appears by the name of *Kurt Gödel*, who’s incompleteness
theorems showed that Hilbert’s optimism was undue [1]. What does this mean?

## Gödel's Incompleteness Theorem

First we have to ask ourselves a question: What even are mathematics?

Well, I might not be well suited to answer this, since I am not a mathematician,
but I can tell you this. In mathematics we work with a set of rules we take as a
fact, called axioms, and from there we are able to arrive at conclusions using a
certain logical system.

[//]: # (sistema axiomático)

So, for any new statement, we should be able make a inference over its truth
value using nothing but our axioms. This means that different sets of axioms
could lead to different theorems in different axiomatic systems.

With this said, we can further explain what *completeness* and *consistency* tells us.
It means that for every statement, we should be able to tell if it is true or
false using nothing but our axioms, and this result should not contradict any
other statement proven before ($i.e.$ we can't prove $p$ and $\neg p$ in the same
axiomatic system).

And what does Gödel's Incompleteness Theorems state about this?

In few words, it tells us that this is impossible to accomplish with our
mathematics. We won't go deep in the mathematical explanation of this, but
we can see a little of the idea behind this using a contradiction reasoning.

Let's suppose we have a defined axiomatic system which is complete and consistent,
given by our set of axioms $\\{A_1, A_2, ... , A_n\\}$, and we receive a new statement
$P$ whose veracity we need to determine. This statement says the following:

> *The statement P cannot be proved from axioms $A_1, A_2, ... , A_n$.*

According to our axioms, is this statement true or false? If it was false, this
would mean the following:
*The statement P CAN be proved from axioms $A_1, A_2, ... , A_n$*, but this
would mean P is true, because it is *provable*. So there is a
contradiction, but we said that our system had to be consistent, so we cannot
accept this.

Then our statement $P$ must be true, but if we further analyze its meaning, we
can see that we've found a true statement, which cannot be proved from the
axioms. This leads to another contradiction, since we had said that our axiomatic
system should be also complete. So we can see that if an axiomatic system is
consistent, then it cannot be complete.

This is an absurdly simplified form of Gödel's proof, but the idea remains the same.

So it was set then, the first two postulates of Hilbert's program were proved
to be mutually exclusive. What then? Well, we haven't said anything about the
*Decidability* problem yet.

## The Entscheidungsproblem

*Entscheidungsproblem* is the german name given to the decision problem.

This is when Alonzo Church comes. In 1936, he states that the set of valid
formulas of first-order logic is not effectively decidable: there is no method
or algorithm for deciding which formulas of first-order logic are valid. For
this proof, Church proposed a mathematical definition for what a
*effectively solvable problem* is [2], and it is here where lambda calculus
appears, being the foundation for functional programming.

And what about procedural programming? This is where Alan Turing appears, the
mathematician widely considered to be the father of modern computer science.
Alan Turing was Church's student and he arrived at the same conclusions
than him independently.

[//]: # (turing)

In 1936 a paper by the name of *On Computable Numbers, with an Application to the Entscheidungsproblem* by Alan Turing is published.
In this paper he explains his own definition of a computing machine (later
known as a Turing machine), which has the same computing capability as Church's
lambda calculus (Church-Turing thesis).

## A Turing Machine

A Turing machine is a model that simplifies the notion of computing to its basics,
but the main idea is that it has an incredible computing capability. When
we talk about computing capability we are not talking about speed, or accuracy,
but what the machine is capable of doing.

A Turing machine $M$ is defined as infinite tape divided in cells, which can
contain one symbol $a$ each, from a given set $\Sigma$. Over the tape there is a
*head* which positions in the current cell. The head can read the symbol written
at that cell and it can move left, right or just stay in that place. The machine
also contains a finite set of states $Q=\\{q_0,q_1,...,q_n\\}$ in which the machine
can be at a given time.
From $Q$, there is a $q_0 \in Q$ which is the initial state, and a
set $F \subset Q$ of accepting states. Finally, there is a transition function
$\delta : Q \times \Sigma \rightarrow Q \times \Sigma \times \\{L, R, S\\}$,
whose purpose is to tell the head a which state to transition, what to write in
the current cell, and where to move for the next step. The set of symbols, is
often called the *tape alphabet*, and usually it is considered to be
$\\{0, 1, \sqcup\\}$.

[//]: # (máquina de turing)

Okay, enough mathematical notation, how does it work?

There is a very good explanation at [this post](https://www.futurelearn.com/courses/how-computers-work/0/steps/49259).

But the main idea is that the head receives instruction on what to write, what
state to go to, and where to move depending only on its current state and the
symbol it reads at a given time.

![Turing Machine 1](https://s3-eu-west-1.amazonaws.com/rpf-futurelearn/how-computers-work/week_1/Turing_machines_02.gif)

![Turing Machine 2](https://s3-eu-west-1.amazonaws.com/rpf-futurelearn/how-computers-work/week_1/Turing_machines_03.gif)

Source: [Future Learn](https://www.futurelearn.com/courses/how-computers-work/0/steps/49259)

If you understand the idea behind a Turing machine, you should know that we can
treat it as a black box to which we give an input (perhaps written in the tape
at the beginning), and it outputs a result (could be a boolean value, or an
output written in the tape), it all depends on the design of our machine.

[//]: # (black box)

The thing we must understand here is that a Turing machine is capable of
computing everything a modern computer can also do. The set of inputs for which
a Turing machine $M$ outputs True, is called *The Language of M*, $L(M)$, and
it is said that the set of all possible languages $L$ that the language of a
machine M, $i.e.$ $\\{L \in \Sigma * \mid \exists M, L(M) = L \\}$, are called
Recursively Enumerable Languages.

An important thing to clarify, is that for the machine to output a result, it must
**halt**. Eventually the machine arrives at a certain combination of state and
symbol for which there is no defined value for the transition function $\delta$
so it can only stay at its position forever. It halts.

## The Halting Problem
This is a fundamental piece to solve the Entscheidungsproblem, it formulates the
following question:

> Is it possible to build a Turing machine $H$, such that it receives an encoded
  version of a machine $M$ and an input $w$, and it outputs whether M will
  eventually halt?

Turing proved that solving this problem was equivalent to solving the
Entscheidungsproblem, in his paper [3].

Let's translate this problem to much more recent concepts: Can we build a
function $H(M, w)$, such that it tells us whether a piece of code (or a function)
$M$ with given input $w$ will end its execution in a finite amount of time, or
it will loop?

As you can imagine, the answer is **no**.

To be continued...


[1] https://plato.stanford.edu/entries/hilbert-program/

[2] https://www.rep.routledge.com/articles/thematic/churchs-theorem-and-the-decision-problem/v-1

[3] On Computable numbers ...
