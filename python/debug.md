---
title: "Python Debugging"
date: 2021-08-05
---

<h1>Raising Exceptions</h1>
Raising an exception is a way of saying, “Stop running the code in this function and move the program execution to the except statement.”
{% highlight python %}

>>> raise Exception('This is the error message.')
Traceback (most recent call last):
  File "<pyshell#191>", line 1, in <module>
    raise Exception('This is the error message.')
Exception: This is the error message.

{% endhighlight python %}
If there are no try and except statements covering the raise statement that raised the exception, the program simply crashes and displays the exception’s error message.
<br><br>
<h2>boxPrint.py</h2>
{% highlight python %}
def boxPrint(symbol, width, height):
  if len(symbol) != 1:
    raise Exception('Symbol must be a single character string.')
  if width <= 2:
    raise Exception('Width must be greater than 2.')
  if height <= 2:
    raise Exception('Height must be greater than 2.')

  print(symbol * width)
  for i in range(height - 2):
     print(symbol + (' ' * (width - 2)) + symbol)
  print(symbol * width)

for sym, w, h in (('*', 4, 4), ('O', 20, 5), ('x', 1, 3), ('ZZ', 3, 3)):
  try:
    boxPrint(sym, w, h)
  except Exception as err:
    print('An exception happened: ' + str(err))
{% endhighlight python %}
Here is the script in action: https://autbor.com/boxprint
<h2>Traceback</h2>
Write traceback information to a text file and keep the program running
{% highlight python %}
>>> import traceback
>>> try:
...          raise Exception('This is the error message.')
>>> except:
...          errorFile = open('errorInfo.txt', 'w')
...          errorFile.write(traceback.format_exc())
...          errorFile.close()
...          print('The traceback info was written to errorInfo.txt.')


111
The traceback info was written to errorInfo.txt.
{% endhighlight python %}
<h2>Assertions</h2>
“I assert that the condition holds true, and if not, there is a bug somewhere, so immediately stop the program.”
{% highlight python %}
>>> ages = [26, 57, 92, 54, 22, 15, 17, 80, 47, 73]
>>> ages.sort()
>>> ages
[15, 17, 22, 26, 47, 54, 57, 73, 80, 92]
>>> assert
ages[0] <= ages[-1] # Assert that the first age is <= the last age.
{% endhighlight python %}
The assert statement here asserts that the first item in ages should be less than or equal to the last one. This is a sanity check; if the code in sort() is bug-free and did its job, then the assertion would be true.
<br><br>
Because the ages[0] <= ages[-1] expression evaluates to True, the assert statement does nothing.
<h2>Logging</h2>
To enable the logging module to display log messages on your screen as your program runs, copy the following to the top of your program (but under the #! python shebang line):
{% highlight python %}
import logging
logging.basicConfig(level=logging.DEBUG, format=' %(asctime)s -  %(levelname)s -  %(message)s')
{% endhighlight python %}
Logging in action:
{% highlight python %}
#!python
import logging
logging.basicConfig(level=logging.DEBUG, format='%(asctime)s -  %(levelname)s
-  %(message)s')
logging.debug('Start of program')

def factorial(n):
    logging.debug('Start of factorial(%s%%)'  % (n))
    total = 1
    for i in range(n + 1):
        total *= i
        logging.debug('i is ' + str(i) + ', total is ' + str(total))
    logging.debug('End of factorial(%s%%)'  % (n))
    return total

print(factorial(5))
logging.debug('End of program')
{% endhighlight python %}
Output:
{% highlight python %}
2019-05-23 16:20:12,664 - DEBUG - Start of program
2019-05-23 16:20:12,664 - DEBUG - Start of factorial(5)
2019-05-23 16:20:12,665 - DEBUG - i is 0, total is 0
2019-05-23 16:20:12,668 - DEBUG - i is 1, total is 0
2019-05-23 16:20:12,670 - DEBUG - i is 2, total is 0
2019-05-23 16:20:12,673 - DEBUG - i is 3, total is 0
2019-05-23 16:20:12,675 - DEBUG - i is 4, total is 0
2019-05-23 16:20:12,678 - DEBUG - i is 5, total is 0
2019-05-23 16:20:12,680 - DEBUG - End of factorial(5)
0
2019-05-23 16:20:12,684 - DEBUG - End of program
{% endhighlight python %}
<p>The factorial() function is returning 0 as the factorial of 5, which isn’t right. The for loop should be multiplying the value in total by the numbers from 1 to 5. But the log messages displayed by logging.debug() show that the i variable is starting at 0 instead of 1. Since zero times anything is zero, the rest of the iterations also have the wrong value for total. Logging messages provide a trail of breadcrumbs that can help you figure out when things started to go wrong.</p>
<br><br>
Change the for i in range(n + 1): line to for i in range(1, n + 1):, and run the program again. The output will look like this:
{% endhighlight python %}
Output:
{% highlight python %}
2019-05-23 17:13:40,650 - DEBUG - Start of program
2019-05-23 17:13:40,651 - DEBUG - Start of factorial(5)
2019-05-23 17:13:40,651 - DEBUG - i is 1, total is 1
2019-05-23 17:13:40,654 - DEBUG - i is 2, total is 2
2019-05-23 17:13:40,656 - DEBUG - i is 3, total is 6
2019-05-23 17:13:40,659 - DEBUG - i is 4, total is 24
2019-05-23 17:13:40,661 - DEBUG - i is 5, total is 120
2019-05-23 17:13:40,661 - DEBUG - End of factorial(5)
120
2019-05-23 17:13:40,666 - DEBUG - End of program
{% endhighlight python %}
Log levels: https://automatetheboringstuff.com/2e/chapter11/#calibre_link-1193
<br><br>
Sending logs to a file:
{% highlight python %}
import logging
logging.basicConfig(filename='myProgramLog.txt', level=logging.DEBUG, format='%(asctime)s -  %(levelname)s -  %(message)s')
{% endhighlight python %}
