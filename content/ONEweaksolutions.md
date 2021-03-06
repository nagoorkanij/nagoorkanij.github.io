Title:Conservation laws - II (Weak solutions) <!--In the name of Almighty-->
Date: 2017-11-10 18:32
Category: Blog

In this article, we will mainly discuss some standard numerical
techniques to analyse two types of Hyperbolic partial differential equations: 

####Advection equation

\begin{equation}
u_t + a(x,t)~u_x = 0
\label{advection}
\end{equation}


####scalar conservation laws

\begin{equation}
u_t + (f(x,t,u))_x  = 0
\label{conservation}
\end{equation}


The conservation law equation (\ref{conservation}) models the evolution of a conservative quantity like mass, momentum, and energy. That is a quantity whose variation inside a closed domain is equal to its flux across the boundaries, i.e, the amount which flows in minus the amount which flows out, of the closed domain.

The advection and the conservation law equations are intimately interconnected. In the case when
$f = f(u)$, the conservation equation Eq. 2 can be rewritten in the advective form as

\begin{equation}
u_t + \dfrac{df}{du}u_x  = 0
\end{equation}

and when a is constant with respect to x, the advection equation can also be viewed as a conservation
law. For example, a very commonly used prototype example of a nonlinear conservation
law is the celebrated Burger’s equation


\begin{equation}
u_t + \dfrac{1}{2} (u^2)_x  = 0
\label{burgers}
\end{equation}


which becomes


\begin{equation}
u_t + u~u_x  = 0
\end{equation}


when written in advective form.

### The method of characteristics
Consider the quasi-linear equation of the form

\begin{equation}
u_t + a(x,t,u)~u_x + b(x,t,u) = 0
\label{quasi}
\end{equation}

Let $x = x(t)$ be a parametric curve in the ($x, t$) plane
such that $\dot{x}= a(x, t, u(x(t), t))$, where $u(x(t), t) = z(t)$ is the solution to Eq. \ref{quasi}  along this curve.
Using the chain rule and plugging into Eq. \ref{quasi} yields

\begin{equation}
\dot{z} = \dfrac{\partial u}{\partial t} + \dfrac{\partial u}{\partial x}~\dot{x} = \dfrac{\partial u}{\partial t} + a(x,t,u)~\dfrac{\partial u}{\partial x} = -b(x,t,u) = -b(x,t,z)
\end{equation}

i.e, finding a solution for the quasi-linear equation reduces to solving the following system of first
order ordinary differential equations.

\begin{equation}
\begin{aligned}
\dot{x} &= a(x,t,z) \\
\dot{z} &= -b(x,t,z) \\
x(0) &= x_0 \quad z(0) = u(x_0, 0) = u_0(x_0)
\end{aligned}
\label{quasicharact}
\end{equation}


Equations \ref{quasicharact} are known as the characteristic equations and the resulting solution curves 
$x = x(t)$, $x(0) = x_0$ are called characteristic curves.

For example, The characteristic equations for the advection equation is

\begin{equation}
\begin{aligned}
\dot{x} &= a \\
\dot{z} &= 0 
\end{aligned}
\end{equation}

whose solution is $x(t) = x_0 + at$, $z(t) = u(x(t), t) = u_0(x_0)$. Two key important points should be
noted here. i) The characteristic curves are straight lines. ii) The solution u is constant along the
characteristic lines.  Note that when $a > 0$ the characteristic lines are directed to the right and
when $a < 0$ they are directed to the left. In some sense the sign of $a$ indicates the direction of
propagation of information. In fact, the advection equation is also called the one-way wave equation,
where $a$ is the speed of propagation of the wave.

To find the solution $u(x, t)$ at an arbitrary point ($x, t$) in the x-t plane, one needs to follow the
characteristic line passing through ($x, t$) back to its original point at $t$ equal to 0: ($x_0 , 0$) with 
$x = x_0 + at$.
This leads to

\begin{equation}
u(x,t) = u_0(x_0) = u_0(x-at)
\end{equation}


The system of characteristic equations for Burger’s equation is given by

\begin{equation}
\begin{aligned}
\dot{x} &= z \\
\dot{z} &= 0 
\end{aligned}
\end{equation}

The characteristic solution is thus given by

\begin{equation}
u(x(t), t) = u_0(x_0) 
\end{equation}

where $x(t) = x_0 + u_0(x_0)t$.

Again note that the characteristics are straight lines and the solution is constant along the char-acteristic lines, with one important difference, however; the characteristic curves are no longer
parallel to each other. As we will see below this has rather unpleasant consequences. Provided
the characteristics lines do not cross each other, which is guaranteed for at least a short period of
time if the initial data $u_0$ is continuous, the solution to Burgers equation is given by the following
implicit formula

\begin{equation}
\begin{aligned}
u(x,t) &= u_0(x-u_0(x_0)~t) \\
x &= x_0 + u_0(x_0)t
\end{aligned}
\end{equation}

We would notice that, the slope of the characteristic curves $x = x_0 + u_0(x_0)t$ for Burger’s equation (Eq. \ref{burgers})
increases when $u_0(x_0)$ increases and decreases when $u_0(x_0)$ decreases. Therefore, the characteristic curves will
accordingly diverge or converge toward each other. The aforementioned behaviour can cause two convergent characteristic
lines to ultimately cross each other at some point in the x-t plane. Beyond such intersection point
the characteristic solution is no-longer valid, because the value of $u(x, t)$ at such a point is not
univalued–one can follow back either one of the two intersecting characteristic lines.

One way to correct for this flaw is by stopping the characteristic lines as soon as they cross each
other. Let $\Sigma$ be the set of such crossing points in the x-t plane. The solution can then be defined
on both sides of $\Sigma$ by following the corresponding characteristic line back to its origin. Below we
will see that $\Sigma$ is a parametric curve on the form $x = s(t)$  and constitutes a
curve of discontinuity for $u(x, t)$. Such a curve is called a shock by analogy to gas dynamics. One
of the main difficulties in practice is to find the shock curve $x = s(t)$. For any given ($x_1, t_1$), one
has to determine whether two characteristic lines cross each other prior to time $t_1$ along the curve
$x = x_1$.

After a shock is formed the solution $u(x, t)$ is no longer valid in the classical sense except for its
restrictions on the sub-domains located on either side on the shock. Nevertheless, such solution
can be defined in the weak sense on the whole x-t plane.

--------------------------------------

-------------------------------------

> Definition (**Weak solution**) A function $u(x, t)$ is said to be a weak solution for the conservation law
> $u_t + (f(x, t, u))_x = 0$, if for any test function $\phi(x,t)$ sufficiently smooth  with a compact support in ($- \infty, + \infty$ $) \times$
> $(0, + \infty)$, the solution $u(x, t)$ satisfies
\begin{equation}
\int \limits_0^{+ \infty} \int \limits_{-\infty}^{+\infty}  u(x,t)~\phi_t(x,t) dxdt + f(x,t,u)~\phi_x(x,t) dxdt = 0.
\end{equation}

The notion of weak solutions is more general and the set of weak solutions contains
discontinuous solutions as well as the classical $\mathit{C}^1$ solutions as a special subset. However, in some
situations weak solutions are not unique, in the sense that one initial value problem can have more
than one weak solution. Selecting the physically relevant solution can be tricky. However, common sense suggests that for any given Cauchy problem, only one
solution is physically relevant. We need an additional constraint to choose this physically relevant
solution among all the weak solutions. In fact, in reality some viscosity is always associated with
a given conservation law, so instead we have

\begin{equation}
u_t^{\epsilon} + (f(u^{\epsilon}))_x  = \epsilon~\dfrac{\partial^2 u^{\epsilon}}{\partial x^2}
\label{viscous}
\end{equation}

and the zero viscosity limit, $\epsilon \rightarrow 0$, is just a convenient mathematical idealization. The above mentioned point is true in
many physical applications. Therefore, one universally accepted criterion states that the physically
relevant weak solution for the conservation law $u_t + (f(u))_x = 0$ is the limit of the solution to the
viscous equation (Eq. \ref{viscous}) when $\epsilon \rightarrow 0$. On the other hand, it is easy to show that, when combined
with appropriate initial conditions, the latter has a unique solution. In practice, however, it is
not clear how to establish if a given weak solution is actually the vanishing viscosity limit or not.
The answer to this question is provided by the concept of entropic solutions. In a nutshell, the
entropy condition states that the physical solution satisfies a general principle of thermodynamics
that the entropy always decreases. It remains to find which among the weak solutions for a given
conservation law satisfies the so-called entropy condition. 


The theorem below provides the necessary ingredients both for
constructing weak solutions and to gain physical insight.

> Theorem  (**Rankine-Hugoniot Condition**) Let $\Sigma$ be a curve in ($- \infty, + \infty$) $\times$
> $(0, + \infty)$ parametrized by $x = s(t)$. Let $u(x, t)$ be a $\mathit{C}^1$ function on both side of but possibly not defined and discontinuous
> across the curve $\Sigma$. Assume $u$ is a solution to the conservation law
> $u_t + (f(u))_x = 0$ on all points $(x, t)$ not on $\Sigma$. For each point $(x_1,t_1) \in \Sigma$ we set

\begin{equation}
u(x_1,t_1) = \lim \limits_{\Omega_1 \cup \Omega_2 \cup \ni (x,t) \rightarrow (x_1,t_1)} u(x,t)
\end{equation}

> i.e. the limits from the right and from the left of $\Sigma$. Then $u(x, t)$ is a weak solution for the
> conservation law if and only if the shock speed $\dot{s}$ satisfies

\begin{equation}
\dot{s} = \dfrac{ds}{dt} = \dfrac{f(u_{+}) - f(u_{-})}{u_{+} - u_{-}}
\end{equation}














