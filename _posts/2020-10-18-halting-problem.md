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
as well as a basic explanation of the halting problem and the proof of
its undecidability.


Image Source: [Coopertoons](https://www.coopertoons.com/education/haltingproblem/haltingproblem.html)

---


## Hilbert's Program

It all began with this guy who comes by the name of *David Hilbert*.

![img_small](https://upload.wikimedia.org/wikipedia/commons/7/79/Hilbert.jpg)

In the 1920's, he proposed a research program with the aim of providing
mathematics with a secure foundation. This should include the following:

* **Completeness**: Every statement's veracity should be possible to determine.
* **Consistency**: No contradiction should be obtained in the formalism of mathematics.
* **Decidability**: An algorithm to decide the truth or falsity of any statement.

Hilbert actually believed that such axiomatic system existed. However, years
later, another guy called *Kurt Gödel* appears, who’s incompleteness
theorems showed that Hilbert’s optimism was undue.

## Gödel's Incompleteness Theorem

To understand Gödel's conclusions, first we have to ask ourselves a question:
What even are mathematics?

Well, I might not be well suited to answer this, since I am not a mathematician,
but I can tell you this. In mathematics we work with a set of rules, called
axioms, and from there we are able to arrive at conclusions using a certain
logical system.

[//]: # (sistema axiomático)

So, for any new statement, we should be able make a inference over its truth
value using nothing but our axioms. This means that different sets of axioms
could lead to different theorems in different axiomatic systems.

With this said, we can further explain what *completeness* and *consistency*
tell us. It means that for every statement, we should be able to tell if it's
*True* or *False* using nothing but our axioms, and this result should not contradict
any other statement proven before ($i.e.$ we can't prove $p$ and $\neg p$ in the
same axiomatic system).

And what does Gödel's Incompleteness Theorems state about this?

In few words, they tell us that this is impossible to accomplish with our
mathematics. We won't go deep in the mathematical explanation of this, but
we can see a little of the idea behind this using a contradiction reasoning.

Let's suppose we define an axiomatic system which is complete and consistent,
given by our set of axioms $\\{A_1, A_2, ... , A_n\\}$, and we receive a new
statement $P$ whose veracity we need to determine. This statement $P$ says the
following:

> *Statement $P$ cannot be proved from axioms $A_1, A_2, ... , A_n$.*

According to our axioms, is this statement *True* or *False*? If it was *False*, this
would mean that the statement $P$ **can** be proved from axioms
$A_1, A_2, ... , A_n$, but this would mean $P$ is *True*, because it is *provable*.
So there is a contradiction found in our axiomatic system, and because we said
that our system had to be consistent, we cannot accept this.

Then our statement $P$ must be *True*. This means we've found a *True*
statement, which cannot be proved from the axioms. This leads to another
contradiction, because we said that our axiomatic system should be also
complete. Thus if an axiomatic system is consistent, then it
cannot be complete.

This is an absurdly simplified form of Gödel's proof, but the idea remains the same.

So it was set, the first two postulates of Hilbert's program were proved
to be mutually exclusive. What then? Well, we haven't said anything about the
*Decidability* problem yet.

## The Entscheidungsproblem

*Entscheidungsproblem* is the german name given to the decision problem
(decidability).

This is when Alonzo Church comes. In 1936, he states that the set of valid
formulas of first-order logic is not effectively decidable: there is no method
or algorithm for deciding which formulas of first-order logic are valid. For
this proof, Church proposed a mathematical definition for what a
*effectively solvable problem* is, using his lambda calculus.

Alan Turing, the mathematician who is widely considered to be the father of
modern computer science, and Church's student, arrived at the same conclusions
than him, independently.

![img_small](https://upload.wikimedia.org/wikipedia/commons/a/a1/Alan_Turing_Aged_16.jpg)

The same year, Alan Turing's paper:
*On Computable Numbers, with an Application to the Entscheidungsproblem*
is published. Here, he explains his own definition of a computing machine
(later known as a Turing machine), which would have the same computing
capability as Church's lambda calculus (according to the Church-Turing
thesis).

## A Turing Machine

A Turing machine is a model that simplifies the notion of computing to its basics,
but the main idea is that it has an incredible computing capability. When
we talk about computing capability we are not talking about speed, or accuracy,
but what the machine is capable of doing.

A Turing machine $M$ is defined as infinite tape divided in cells, which can
contain one symbol $a$ each, from a given set $\Sigma$. Over the tape there is a
*head* which positions in the current cell. The head can read the symbol written
in that cell, and it can move left, right or stay in that place. The machine
also contains a finite set of states $Q=\\{q_0,q_1,...,q_n\\}$ in which the machine
can be at a given time.
From $Q$, there is a $q_0 \in Q$ which is the initial state, and a
set $F \subset Q$ of accepting states. Finally, there is a transition function
$\delta : Q \times \Sigma \rightarrow Q \times \Sigma \times \\{L, R, S\\}$,
whose purpose is to tell the head which state to transition to, what to write in
the current cell, and where to move for the next step. The set of symbols, is
often called the *tape alphabet*, and it is usually considered to be
$\\{0, 1, \sqcup\\}$.

[//]: # (máquina de turing)

Okay, enough mathematical notation, how does it work? There is actually a very
good explanation at
[this post](https://www.futurelearn.com/courses/how-computers-work/0/steps/49259).

But the main idea is that the head receives instruction on what to write, what
state to transition to, and where to move to, depending only on its current
state and the symbol it reads at a given time.

![img_big](https://s3-eu-west-1.amazonaws.com/rpf-futurelearn/how-computers-work/week_1/Turing_machines_02.gif)

![img_big](https://s3-eu-west-1.amazonaws.com/rpf-futurelearn/how-computers-work/week_1/Turing_machines_03.gif)

Source: [Future Learn](https://www.futurelearn.com/courses/how-computers-work/0/steps/49259)

If you understand the idea behind a Turing machine, you should know that we can
treat it as a black box to which we give an input (written in the tape at the
initial state), and it outputs a result (could be a boolean value, or an
output written in the tape, depending on the design of the machine).

[//]: # (black box)

An important thing to clarify, is that for a machine to output a result, it must
**halt**. Eventually it arrives at a certain combination of state $q$ and tape
symbol $s$, for which there is no defined value for the transition function
$\delta$, so it can only stay at its position forever. It halts.

## The Halting Problem
We can now talk about this post's main topic. This problem was a fundamental
piece for Turing to solve the Entscheidungsproblem. It formulates the following
question:

> Is it possible to build a Turing machine $H$, such that it receives an encoded
  version of a machine $M$ and an input $w$, and it outputs whether $M$ will
  eventually halt on input $w$?

The important thing here, is that solving this problem is equivalent to solving
the Entscheidungsproblem. ¿Why? Well, we use something called *reductions*, this
basically means that an instance of a problem A is expressed as an instance of a
problem B such that both instances have the same output.
So if we reduced the Halting Problem to the Entscheidungsproblem,
it would mean that if we can solve the latter, we can solve the former. But more
important, it means that if we can't solve the Halting Problem, then we can't
solve the Entscheidungsproblem. To learn more about reducing the
Halting Problem to the Entscheidungsproblem, you can check out
[this post](http://kilby.stanford.edu/~rvg/154/handouts/incompleteness.html).


Let's translate this problem to something less abstract: Can we build a
function $H(M, w)$, such that it tells us whether a piece of code (or a function)
$M$ with a given input $w$ will end its execution in a finite amount of time?

As you can imagine, the answer is **no**, and we will show why. Let's use a
more understandable model than Turing machines. We'll use python-styled
pseudocode to explain what we are doing.

Lets suppose we have a defined function $H$ that does the following


```python
def H(M, w):
    """
    Returns:
        True if the execution of M(w) finishes in a finite amount of time
        False in other case
    """
```


Let's now define a function A (for *absurd*) this way:


```python
def A(M):
    if H(M, M):
        # Loop infinitely
        while(True):
            pass
    else:
        return True
```


Now, what would happen if we called ```>>> A(A)```? Will it halt?
Let's suppose it actually halts, this would mean that $H(A, A)$ returned
*False*, and this means $A$ doesn't halt on input $A$, which is a contradiction.
What if ```>>> A(A)``` doesn't halt? Then it must have got caught in
the ```while(True)``` loop, meaning that the output of $H(A, A)$ was *True*,
but then it would mean that $A$ halts on input $A$, so either way we have found
a contradiction, which means $H$ can't exist.

Using this simple but creative and powerful idea, Turing proved that there is
no solution for the Entscheidungsproblem. He proved Hilbert wrong and, in the
way, settled the foundations for modern computer science.

## A little extra
Finally, I leave you the video that inspired me on investigating about this
topic. It is a fragment from BBC's television movie *Breaking the Code*.

<iframe width="560" height="315" src="https://www.youtube.com/embed/gV67Sj2jkVg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## References


[1] Zach, Richard, "Hilbert’s Program", The Stanford Encyclopedia of Philosophy (Fall 2019 Edition), Edward N. Zalta (ed.), https://plato.stanford.edu/archives/fall2019/entries/hilbert-program/.

[2] Parikh, Rohit. Church’s theorem and the decision problem, 1998, doi:10.4324/9780415249126-Y003-1. Routledge Encyclopedia of Philosophy, Taylor and Francis, https://www.rep.routledge.com/articles/thematic/churchs-theorem-and-the-decision-problem/v-1.

[3] A. M. Turing, On Computable Numbers, with an Application to the Entscheidungsproblem, Proceedings of the London Mathematical Society, Volume s2-42, Issue 1, 1937, Pages 230–265, https://doi.org/10.1112/plms/s2-42.1.230

[4] M. Sipser, Introduction to the Theory of Computation, International Thomson Publishing, 1996.

[5] Wise, Herbert (Director). 1996. Breaking the Code [Film]. BBC.
