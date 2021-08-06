<h1>Web Scraping</h1>
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
