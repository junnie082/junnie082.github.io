---
layout: post
title: Algorithm) Baekjoon /#11047. 동전 0
subtitle: Greedy Algorithm, C
author: Jun
categories: Algorithm
banner:
  video: https://vjs.zencdn.net/v/oceans.mp4
  loop: true
  volume: 0.8
  start_at: 8.5
  image: https://bit.ly/3xTmdUP
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
tags: jekyll theme yat
sidebar: []
---

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

## section 1

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int N, K; 
    scanf("%d %d", &N, &K);

    int *greedy = (int *)malloc(sizeof(int) * N); 

    int val; 
    for (int i = N-1; i >= 0; i--) {
        scanf("%d", &val);
        greedy[i] = val; 
    }

    int count = 0, remain = K; 

    for (int i = 0; i < N; i++) {
        count += remain / greedy[i]; 
        remain = remain % greedy[i]; 
    }

    printf("%d\n", count); 
    free(greedy); 
}
{% endhighlight %}

## section 2

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]: https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

$ a \* b = c ^ b $

$ 2^{\frac{n-1}{3}} $

$ \int_a^b f(x)\,dx. $

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int N, K; 
    scanf("%d %d", &N, &K);

    int *greedy = (int *)malloc(sizeof(int) * N); 

    int val; 
    for (int i = N-1; i >= 0; i--) {
        scanf("%d", &val);
        greedy[i] = val; 
    }

    int count = 0, remain = K; 

    for (int i = 0; i < N; i++) {
        count += remain / greedy[i]; 
        remain = remain % greedy[i]; 
    }

    printf("%d\n", count); 
    free(greedy); 
}
```

```python
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("John", 36)

print(p1.name)
print(p1.age)
```
