---
title: "pathlib commands"
date: 2021-07-28
---

{% highlight python %}
>>> from pathlib import Path
>>> Path('spam', 'bacon', 'eggs')

# The path will appear the same on both Windows and Linux
WindowsPath('spam/bacon/eggs')
PosixPath('spam/bacon/eggs')

>>> str(Path('spam', 'bacon', 'eggs'))
# Windows
'spam\\bacon\\eggs'
# Linux
'spam/bacon/eggs'

# Using the / Operator to Join Paths
>>> from pathlib import Path
>>> Path('spam') / 'bacon' / 'eggs'
WindowsPath('spam/bacon/eggs')
>>> Path('spam') / Path('bacon/eggs')
WindowsPath('spam/bacon/eggs')
>>> Path('spam') / Path('bacon', 'eggs')
WindowsPath('spam/bacon/eggs')
{% endhighlight python %}
A script that uses the .join operator with a \ is not safe, because it's backslashes would only work on Windows.
{% highlight python %}
>>> homeFolder = r'C:\Users\Al'
>>> subFolder = 'spam'
>>> homeFolder + '\\' + subFolder
'C:\\Users\\Al\\spam'
>>> '\\'.join([homeFolder, subFolder])
'C:\\Users\\Al\\spam'
{% endhighlight python %}
VS.
{% highlight python %}
>>> homeFolder = Path('C:/Users/Al')
>>> subFolder = Path('spam')
>>> homeFolder / subFolder
WindowsPath('C:/Users/Al/spam')
>>> str(homeFolder / subFolder)
'C:\\Users\\Al\\spam'
{% endhighlight python %}
