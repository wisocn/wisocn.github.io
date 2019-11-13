---
layout: post
title:  "Encryption context in DynamoDB"
subtitle: "A shot tale about table name beign bound to encryption context!"
date:   2019-01-01 14:52:11 +0100
categories: aws dynamodb
---
Here's common scenario i came accross lately.

You import some fancy new library/module and stuff works, life is good. 
Now, you add some custom features, tricks and code around it but library doesn't behave as you expected. 

Naturally, to fully understand what is going on, the next step is to rise up the logging level and get more verbose output in logs. 

But! 

Sometimes logging is not possible either because author of the library didn't include any logging statements or logging didn't even make sense.    

In my case it was the influx registry library that enabled pushing of metrics to influx-db.
It was working allright and the metrics did indeed get pushed over the wire. But some tags for metrics were not included!

WTF?

So, i dug into code of library (it's open sourced) and noticed that the only logging statement in the library was

"x numbers of Metrics sucessfully sent". 

No payload was ever logged because probably there was never a use case for that. 

So i turned to a quite useful tool in linux called TCPDUMP. 

What is tcpdump? 

For me, most important excerpt from man page:

{% highlight ruby %}
1.) tcpdump  prints  out  a  description  of the contents of packets on a network interface that match the boolean expression; 
2.) It can also be run with the -w flag, which causes it to save the packet data to a file for later analysis,
3.) It can also be run with the -V flag, which causes it to read a list of saved packet files.
{% endhighlight %}

In short: 
tcpdump prints out the contents of packets flowing from a certian local network interface (eth0, wlp0, tun0) 
You can write all of the intercepted packets to a file for later analysis (think wireshark)
Filter out a saved packet files that are stored on the disk.


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
