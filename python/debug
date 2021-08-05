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
<h2>Tracback</h2>
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
