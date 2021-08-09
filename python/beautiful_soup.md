<h1>Beautiful Soup</h1>
<h2>Install Beautiful Soup</h2>
{% highlight python %}
pip install --user beautifulsoup4
{% endhighlight %}
<h2>Example webpage:</h2>
{% highlight html %}
<!-- This is the example.html example file. -->

<html><head><title>The Website Title</title></head>
<body>
<p>Download my <strong>Python</strong> book from <a href="https://
inventwithpython.com">my website</a>.</p>
<p class="slogan">Learn Python the easy way!</p>
<p>By <span id="author">Al Sweigart</span></p>
</body></html>
{% endhighlight %}
<h2>Create a Beautiful Soup object</h2>
{% highlight python %}
>>> import requests, bs4
>>> res = requests.get('https://nostarch.com')
>>> res.raise_for_status()
>>> noStarchSoup = bs4.BeautifulSoup(res.text, 'html.parser')
>>> type(noStarchSoup)
<class 'bs4.BeautifulSoup'>
{% endhighlight %}
Doing the same thing but with the example.html (make sure python is running in the same directory as example.html)
{% highlight python %}
>>> exampleFile = open('example.html')
>>> exampleSoup = bs4.BeautifulSoup(exampleFile, 'html.parser')
>>> type(exampleSoup)
<class 'bs4.BeautifulSoup'>
{% endhighlight %}
