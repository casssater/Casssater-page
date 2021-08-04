The code will take whatever is currently loaded on the clipboard and save it to the file 'mcb' using a specified keyword. 
If the script is ran against an existing keyword, the associated phrase will be copied to the clipboard.

{% highlight python %}

#!python3
 # mcb.pyw - Saves and loads pieces of text to the clipboard.
 # Usage: python3 mcb.pyw save <keyword> - Saves clipboard to keyword.
 #        python3 mcb.pyw <keyword> - Loads keyword to clipboard
 #        python3 mcb.pyw list - Loads all keywords to clipboard.
 #        python3 mcb.pyw delete <keyword> - Delete keyword from save file
 #        python3 mcb.pyw delete-all - Delete all keywords
 
 import shelve, pyperclip, sys
 
 mcbShelf = shelve.open('mcb')
 
 if len(sys.argv) == 3 and sys.argv[1].lower() == 'save':
     mcbShelf[sys.argv[2]] = pyperclip.paste()
 elif len(sys.argv) == 3 and sys.argv[1].lower() == 'delete':
     del mcbShelf[sys.argv[2]]
 elif len(sys.argv) == 2:
     # List keywords and load content.
     if sys.argv[1].lower() == 'list':
         pyperclip.copy(str(list(mcbShelf.keys())))
     elif sys.argv[1].lower() == 'delete-all':
         mcbShelf.clear()
     elif sys.argv[1] in mcbShelf:
         pyperclip.copy(mcbShelf[sys.argv[1]])
 
 mcbShelf.close()
  
{% endhighlight python %}
