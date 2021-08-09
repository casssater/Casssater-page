<h1>Beautiful Soup</h1>
<h2>Install Beautiful Soup</h2>
{% highlight python %}
pip install --user beautifulsoup4
{% endhighlight %}
<h2>Example webpage:</h2>

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
