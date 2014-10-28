---
layout: post
title: Euler Project
---

In an attempt to practice Javascript writing and hone my problem solving at the same time I set up with solving [Project Euler](https://projecteuler.net/about) problems. A restriction I set myself was to use no `for` or `while` loops. This can be compensated for through recursions.

As an example I will talk about [problem 9](https://projecteuler.net/problem=9).

> A Pythagorean triplet is a set of three natural numbers, a < b < c, for which,

>a2 + b2 = c2
>For example, 32 + 42 = 9 + 16 = 25 = 52.

>There exists exactly one Pythagorean triplet for which a + b + c = 1000.
>Find the product abc.

This is an interesting problem because although you could blindly program a solver of pythagorean triplets there are a lot of information to be read from the description. If you spend a little time with a pen and paper it can give a very nice solution for your code. My approach was to parametrise `b` and `c` with a. Firstly with the obvious `c = 1000 - b - a`, then you put that into Pythagoras' theorem, do algebra and get

> b = (1000a-500000)/(a-1000)

Now the problem is only dependant on one parameter, I know that a solution exists and that it is unique since it's given so I can blindly start at a reasonable number, 1 or bigger and iterate.

{% highlight js %}

function addP9(a) {
			var b = (1000 * a - 500000)/(a - 1000);
			var c = 1000 - b - a;
			if (a*a + b*b == c*c && b%1 == 0) {
				return a*b*c;
			}
			return addP9(a+1);
		}

{% endhighlight %}

`a` and `c` are automatically integers. `b` is not however and there exists a solution where it isn't so you need to check for that as well.

Similarly I solved many other problems for Project Euler and you can see them on my github or reach out to me via email.
