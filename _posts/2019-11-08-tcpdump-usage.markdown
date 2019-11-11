---
layout: post
title:  "TCPdump it!"
date:   2019-11-08 14:52:11 +0100
categories: cli tcpdump linux
---
Have you ever imported some fancy new library/module/subproject and then tried to log the output of whats get sent over the wire? Sometimes you just want to see the payload sent in order to debug effectivley. 
Of course you should first try to increase the log level and output. 

But! 

Sometimes logging is not possible either because author didn't include any logging statements or logging didn't even make sense.     

In my case it was the influx registry metrics push library.

I could see that metrics are in fact being sent but some influx tags were not included. At least this was my assumption.
If i've increased the log level the influx-push library would just log the "x numbers of Metrics sucessfully sent". 

So I digged into code.

I've found out that this is the only log statement in the whole class and this is the one i'm seeing currently. 

Allright time to check the internet traffic! 
   

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

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
