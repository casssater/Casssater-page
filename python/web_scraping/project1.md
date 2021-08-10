<h1>Project: Opening All Search Results</h1>
<b>Here is what the program will do:</b>
1. Gets search keywords from the command line arguments
2. Retrieves the search results page
3. Opens a browser tab for each result
{% highlight python %}
#!python3
# searchpypi.py - Open several search results.
 
import requests, sys, webbrowser, bs4
print('Searching...') # display text while downloading the search result page
res=requests.get('https://google.com/search?q=''https://pypi.org/search/?q='+''.join(sys.argv[1:]))
res.raise_for_status()
 
# Retrieve top search result links.
soup=bs4.BeautifulSoup(res.text,'html.parser')
# Open a browser tab for each result.
linkElems=soup.select('.package-snippet')
print(linkElems)
numOpen=min(5,len(linkElems))
for i in range(numOpen):
    urlToOpen='https://pypi.org'+linkElems[i].get('href')
    print('Opening',urlToOpen)
    webbrowser.open(urlToOpen)
{% endhighlight %}
