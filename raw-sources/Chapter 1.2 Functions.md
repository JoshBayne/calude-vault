#math1324/chapter1 

A **relation** is a set of **ordered pairs**. The first entry of each ordered pair is an element of the **domain**, while the second entry of each ordered pair is an element of the **range**. The most common relations we use are equaltions, tables and graphs. A **function** is a relation where each element of the domain is related to only one element of the range. In a table we typically list the elements of the domain first (top row or left column)

For each relation below, is the relation a function? State the domain and range.
1. 
| x   | -3  | 5   | 1   | 0   | 2   | -1  |
| --- | --- | --- | --- | --- | --- | --- |
| y   | 1   | 10  | -4  | -4  | 3   | -2  |
**Yes** this is a function
Domain: $\{-3,-1,0,1,2,5\}$
Range: $\{-4,-2,1,3,10\}$

2. 
| x   | 1   | -3  | 1   | 4   | 2   | 5   |
| --- | --- | --- | --- | --- | --- | --- |
| y   | 2   | -1  | -2  | -4  | 3   | -2  |
**No** this is not a function, 1 is in the domain twice and is related to two different ranges
Domain: $\{-3,1,2,4,5\}$
Range: $\{-4,-2,-1,2,3\}$

---

On a graph we always put the domain of a relation on the horizontal axis, and the range on the vertical axis.

Circle graph going from x-4,4 and y-4,4

Domain: $[-4,4]$
Range: $[-4,4]$
**Not** a function since the $x$ axis can be related to multiple $y$ axis points

Basically any graph that passes the vertical line test is a function.

---

When our function is an equation, we sometimes uise function notation. For example if we have the function $y=x^2+3$, we might choose to name this function $f$ and instead write $f(x)=x^2+3$. This would read "$f$ of $x$ is $x$ squared plus $3$". f is just the name of the function and it is very important that $f(x)$ **does not** mean $f$ times $x$. What f(x) means is that the name of the function is f and the x is the input (an element of the domain). The other side of the equation tells us what the output of the function (an element of the range) is when the input is x. We use function notation for a few reasons. One of the reasons is to make it clear ethat the relation we are using is a function. Another reason is that we often deal with many funcitons at once, so iving them all different names helps us to distinguish between them.

For the function $f(x)=12x-x^3$, find the following

a. $f(1)$
$f(1)=12(1)-1^3$
f(1)=11

The graph of y=f(x) has the point (1,11)

b. $f(-2)$
$f(-2)=12(-2)-(-2^3)$
$f(-2)=-16$


c. $f(a)$
$f(a)=12(a)-a^3$


d. $f(2x)$
$f(2x)=12(2x)-(2x)^3$
$f(2x)=24x-(2x)^3$
$f(2x)=24x-8x^3$

For the function $g(t)=t^2+2t+4$ find the following

$g(-2)$
4

$g(0)$
4

$g(10)$
124

$g(t+3)$
$g(t+3)=(t+3)^2+2(t+2)+4$
$g(t+3)=t^2+6t+9+2t+6+6$
$g(t+3)=t^2+8t+19$

---

f(x)=12-2x

f(2)
f(2)=12-2(2)
f(2)=12-4
f(2)=8

determine where f(x) =2
2=12-2x
2x+2=12
2x=10
x=5

It is important to know what the doamin of a particular function is. When a function is given as an equation, we are either explicitly told what the domain is, or the domain is implied by the equation. If the domain is implied, then the domain is the set of all real numbers that will allow the function to make valid calculations over the real numbers. For example, for the function f(x)=sqrt(x), -4 would not be the domain because sqrt(-4) is not a real number. For now, the only problems that will restrict the domain will be taking the square root (or fourth root, etc) of a negative number, and dividing by 0. Later this list of problems will grow.

find the doamin of each function

1.$f(x)=3x^2-5x+2$
	domain: $(-\infty ,\infty)$


2.$g(x)={X+1\over2x-4}$
	x=2 is not in the domain
	$(-\infty,2)$ or $(2,\infty)$

3.$h(x)=\sqrt{4-3x}$
	anything under sqrt cannot be negative
	$4-3x \ge 0$
	$-3x \ge -4$
	$x \le {4\over3}$
domain $(-\infty,{4\over3}]$

If a box with a square cross section is to be sent by a delivery service, there are restrictions on its size such that its volume is given by V(x)=x^2(108-4x), where x is the length of each side of the cross section in inches.

1. find V(10) and V(20)

$V(10)=10^2(108-4\cdot10)$
100(108-40)
100(68)
6,800 in^3


$V(20)=20^2(108-4\cdot20)$
400(108-80)
400(28)
11,200 in^3

2. What restrictions must be placed on x (the domain) so that the problem makes physical sense?

x>0
108-4x>0
-4x>-108
x<27
domain $(0,27)$


We can perform many operations on functions. The basic arthmetic operations of functions are straightforward
$(f+g)(x)=f(x)+g(x)$
$(f-g)(x)=f(x)-g(x)$
$(f\cdot g)(x)=f(x)\cdot g(x)$
$(\frac {f}{g})(x)=f(x) \ g(x)$ if $g(x)$ is not equal to 0

We also have some operations for functions that we do not have for real numbers. One of these operations is function composition.
$(f \circ g)(x)=f(g(x))$
We read the left side as "f composed with g and x" and the right as "f of g of x". When we compose two functions, we are basically putting one entire function into another function. First we give the input x to the functions g and it gives us the output g(x) . Then that output becomes the input for f, and it gives us back a new output. ($f \cdot g$ does not equal $f \circ g$)

for example, if $f(x)=3x+1$ and $g(x)=x^3-1$ then
$(f \cdot g)(x)=(3x+1)(x^3-1)=3x^4+x^3-3x-1$
$(f-g)(x)=3x+1-(x^3-1)=3x-x^3+2$
$(f \circ g)(x)=f(g(x))=f(x^3-1)=3(x^3-1)+1=3x^3-2$

For the functions $f(x)=3x+5$, $g(x)=x^2+1$, $h(x)=\sqrt{2x-1}$ find the following
(g-f)(x)
$g(x)-f(x) = x^2+1-(3x+5) = x^2-3x-4$

$\frac {h}{g}(x)$
$\frac{h(x)}{g(x)} \frac {\sqrt{2x-1}}{x^2+2}$

$h(f(x))$
$h(f(x))=\sqrt{2(3x+5)-1}$
$=\sqrt{6x+9}$

$(f \circ f)(x)$
$f(f(x)) = 3(3x+5)+5$
$9x+15+5$
$9x+20$


$(g+h)(x)$


$g\cdot h(x)$



