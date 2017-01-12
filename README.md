Bidirectional text support for Sublime Text 3
===================

Currently Sublime Text 3 is not supporting bidirectional languages like Arabic, Hebrew etc.. Using this plugin you can view bidirectional texts.

Please note, I don't know Arabic or Hebrew. I have checked the results by pattern matching. Its a starting point. 

<img alt="" src="https://lh6.googleusercontent.com/-GAIfpn6Oeyg/UHHVmqjSG7I/AAAAAAAAEng/wWPjpxu5e5I/s799/sublime-text2-arabic.jpg" title="Sublime text 2 BiDi - RTL Support plugin" class="alignnone" width="799" height="268">

Install
-----------------
Clone it into Sublime Package directory.

<img alt="" src="https://lh6.googleusercontent.com/-zm8xnRDkluI/UG9mLrQYgPI/AAAAAAAAEm0/8qOUUMngOlw/s800/rtl-sublime-text.jpg" title="Sublime Text 2 - BiDi Plugin" class="alignnone" width="800" height="569">

Set Font face to any Arabic supporting font (Arial) in user settings. <br>
<img alt="" src="https://lh3.googleusercontent.com/-l_CN_p6kJKM/UHHVlhvTU5I/AAAAAAAAEnY/8fLi3mbYoUU/s412/sublime-text2-user-pref-menu.jpg" title="Sublime text 2 user settings" class="alignnone" width="412" height="321"> <br>

<img alt="" src="https://lh6.googleusercontent.com/-VM_A9JCJhT0/UHHVlFSsMNI/AAAAAAAAEnU/CXvpyMjdv2U/s516/sublime-text2-user-pref.jpg" title="Sublime text 2 user settings" class="alignnone" width="516" height="153">

Usage
----------------------
Open file.
Enter text
Tools > Bidirectional text (ctrl+b)


<img alt="" src="https://lh6.googleusercontent.com/-o8kkAWZDmcw/UG9lAk9omKI/AAAAAAAAEmk/u__PYos0-IY/s800/bidi-sublime-text2.jpg" title="Sublime text 2 Bidirectional text" class="alignnone" width="800" height="569">


Command Accebility 
-------------------
Tools > Bidirectional text
Ctrl + B
Right click > Bidirectional text

How does this work?
-------------------

This tool takes a similar approach as to tools like [python-bidi](https://github.com/MeirKriheli/python-bidi), [python-arabic-reshaper](https://github.com/mpcabd/python-arabic-reshaper), [Better-Arabic-Reshaper](https://github.com/agawish/Better-Arabic-Reshaper/) and others.
It does not make Sublime Text fully support bidirectional text.
Rather, it uses a clever hack to make the text in the Arabic family of languages look acceptable.

Take the word سلام, for instance, made of the these Unicode code-points in the order that they are typed and stored on disk:

- `U+0633 ARABIC LETTER SEEN`
- `U+0644 ARABIC LETTER LAM`
- `U+0627 ARABIC LETTER ALEF`
- `U+0645 ARABIC LETTER MEEM`

These letters should be displayed right-to-left visually, and the letters should change shape depending on their position as expected in Arabic, like in this image:

![](docs/normal_peace.png)

Instead, Sublime Text 3 displays the letters left-to-right visually (which is the wrong order), and the letters are incorrectly disconnected:

![](docs/sublime_peace.png)

When you run this plugin with the selected text, it transforms the text into these Unicode code points in this order:

- `U+FEE1 ARABIC LETTER MEEM ISOLATED FORM`
- `U+FEFC ARABIC LIGATURE LAM WITH ALEF FINAL FORM`
- `U+FEB3 ARABIC LETTER SEEN INITIAL FORM`

These Unicode code-points are different from the original ones, because they specify exactly in which inflexible form each letter should be displayed (and the two letters *lam* and *alef* have been converted into one code point).
The order as well as changed, now the letter that is the right-most is first, rather then the letter that is read the first.

The effect is that the Arabic text now looks pretty in editors with poor bidi support like Sublime Text, like in this image:

![](docs/sublime_peace_after.png)

However, you will still have issues if you try to edit the text.


Bug tracker
----------
Post an issue here on Github. 
https://github.com/praveenvijayan/Sublime-Text-2-BIDI/issues

Resources
----------
http://www.decodize.com/html/sublime-text-2-bidirectional-language-support-plugin/

Twitter 
------------------
Follow for updates :  <a href="http://twitter.com/praveen_vijaya">@praveen_vijaya</a>

Thanks
----
https://github.com/MeirKriheli/python-bidi <br>
https://github.com/mpcabd/python-arabic-reshaper








