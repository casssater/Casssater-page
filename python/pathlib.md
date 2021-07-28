---
title: "pathlib commands"
date: 2021-07-28
---

">>> from pathlib import Path"
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

# A script that uses .join operator with a \ is not save, because its backslashes would only work on Windows.
>>> homeFolder = r'C:\Users\Al'
>>> subFolder = 'spam'
>>> homeFolder + '\\' + subFolder
'C:\\Users\\Al\\spam'
>>> '\\'.join([homeFolder, subFolder])
'C:\\Users\\Al\\spam'

# Vs.
>>> homeFolder = Path('C:/Users/Al')
>>> subFolder = Path('spam')
>>> homeFolder / subFolder
WindowsPath('C:/Users/Al/spam')
>>> str(homeFolder / subFolder)
'C:\\Users\\Al\\spam'
