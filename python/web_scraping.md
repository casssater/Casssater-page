<h1>Web Scraping</h1>
[Beautiful Soup](/Casssater-page/python/beautiful_soup.html)
<h2>Modules</h2>
<p><b>webbrowser</b> Comes with Python and opens a browser to a specific page.</p>
<p><b>requests</b> Downloads files and web pages from the internet.</p>
<p><b>bs4</b> Parses HTML, the format that web pages are written in.</p>
<p><b>selenium</b> Launches and controls a web browser. The selenium module is able to fill in forms and simulate mouse clicks in this browser.</p>
<h2>mapIt.py</h2>
mapIt.py - Launches a map in the browser using an address from the command line or clipboard.
{% highlight python %}
#!python3
# mapIt.py - Launches a map in the browser using an address from the command line or clipboard.
 
import webbrowser, sys, pyperclip
if len(sys.argv) > 1:
  # Get address from command line.
  # Assign address to address variable and join it as a string
  address = ''.join(sys.argv[1:])
else:
  # Get address from clipboard.
  address = pyperclip.paste()
 
webbrowser.open('https://www.google.com/maps/place/' + address)
{% endhighlight python %}
<h2>Using requests module</h2>
{% highlight python %}
>>> import requests
>>> # Set Variable res to URL with downloadable content
>>> res = requests.get('https://automatetheboringstuff.com/files/rj.txt')
>>> type(res)
<class 'requests.models.Response'>
>>> # Make sure the status_code attribute of the Response object is equal to requests.codes.ok 
>>> res.status_code == requests.codes.ok
True
>>> len(res.text)
178981
>>> print(res.text[:250])
The Project Gutenberg EBook of Romeo and Juliet, by William Shakespeare

This eBook is for the use of anyone anywhere at no cost and with
almost no restrictions whatsoever.  You may copy it, give it away or
re-use it under the terms of the Proje
{% endhighlight python %}
<h2>Save downloaded files to hard drive</h2>
{% highlight python %}
>>> import requests
>>> # Make sure the URL exists
>>> res.raise_for_status()
>>> # Create/Open file RomeoAndJuliet.txt in write binary mode
>>> playFile = open('RomeoAndJuliet.txt', 'wb')
>>> # Loop over the Response object's iter_content() method
>>> for chunk in res.iter_content(100000):
>>> # Call write() on each iteration to write the content to the file.
...     playFile.write(chunk)
... 
100000
78978
>>> playFile.close()
{% endhighlight python %}
