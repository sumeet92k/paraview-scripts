---
layout: post
title:  "Auto Generating code!"
#date:   <%= Time.now.strftime('%Y-%m-%d %H:%M:%S %z') %>
categories: ParaView
---
There are two ways to start scripting in ParaView, one is the hard way by starting from scratching which teaches us the nitty gritty details of ParaView along the way. The other is the faster approach we follow here of modifying the auto generated python code. This approach is preferred if we only need to make small modifications to the code generated. Lets begin by opening ParaView from the terminal. Its better at this stage to open ParaView without passing any arguments:
{% highlight shell %}
paraview 
{% endhighlight %}

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
