# bookmarklets
Here are a collection of Javascript bookmarklets that I've collected. Sometimes they are better than extensions.

This site is available at: [bookmarklets](https://mrrcollins.github.io/bookmarklets/).

# Using the bookmarklets

To install the bookmarklet, drag the link to your bookmarks bar (if your bookmarks bar isn't showing, you'll want to turn it on first). After the bookmarklet is on your bookmarks bar, you can use it by clicking on it.

![Screen capture dragging bookmarklet to bookmark bar](media/2023-03-11AddingBookmarklet.gif)

# Capturing the page title and address of a website

* [Copy Title & URL](javascript:%3B(()%3D%3E%7B(function%20()%20%7B%0Ainit()%0Afunction%20init()%20%7B%0Alet%20title%20%3D%20document.title%0Alet%20url%20%3D%20document.URL%0Aif%20(!!url.match('mail.google.com'))%20%7B%0Aconst%20id%20%3D%20location.hash.split('%2F').at(-1)%0Aif%20(location.hash%20%3D%3D%3D%20''%20%7C%7C%20id%5B0%5D%20%3D%3D%3D%20'%23')%20%7B%0A%2F%2F%20keep%20title%20and%20url%0A%7D%20else%20%7B%0Aconst%20email%20%3D%20document.title.split('-').at(-2).trim()%0A%2F%2F%20title%20pattern%20is%3A%20%60%24%7Bemail%20subject%20line%7D%20-%20%24%7Bemail%20address%7D%20-%20%24%7Bname%20of%20mail%20provider%7D%0A%2F%2F%20%24%7Bname%20of%20mail%20provider%7D%20is%20'Gmail'%20or%20the%20Google%20Workspace%20'Mail'%0Atitle%20%3D%20title.split('-').slice(0%2C%20-2).join().trim()%20%2B%20'%20-%20Gmail'%0Aurl%20%3D%20%60https%3A%2F%2Fmail.google.com%2Fmail%2Fu%2F%24%7Bemail%7D%2F%23all%2F%24%7Bid%7D%60%0A%7D%0A%7D%0AcopyLink(url%2C%20title)%0A%7D%0Afunction%20copyLink(url%2C%20title)%20%7B%0Afunction%20listener(e)%20%7B%0Aif%20(!title)%20title%20%3D%20url%0Ae.clipboardData.setData(%22text%2Fplain%22%2C%20title%20%2B%20'%5Cn'%20%2B%20url)%0Ae.clipboardData.setData(%22text%2Fhtml%22%2C%20%60%3Ca%20href%3D%22%24%7Burl%7D%22%3E%24%7Btitle%7D%3C%2Fa%3E%60)%0Ae.clipboardData.setData(%22text%2F_notion-text-production%22%2C%20%60%7B%22editing%22%3A%20%5B%5B%22%24%7Btitle%7D%22%2C%5B%5B%22a%22%2C%22%24%7Burl%7D%22%5D%5D%5D%5D%2C%22selection%22%3A%20%7B%22startIndex%22%3A%200%2C%22endIndex%22%3A%20%24%7Btitle.length%7D%7D%7D%60)%0Ae.preventDefault()%0A%7D%0Adocument.addEventListener(%22copy%22%2C%20listener)%0Atry%20%7B%0Adocument.execCommand(%22copy%22)%0Aconsole.log(%22Copied%3A%20%5Cn%22%2C%20%7B%0Atitle%2C%0Aurl%0A%7D)%0A%7D%20catch%20(e)%20%7B%0Aconsole.log(%22Copy%20failed.%22%2C%20e)%0A%7D%20finally%20%7B%0Adocument.removeEventListener(%22copy%22%2C%20listener)%0A%7D%0A%7D%0A%7D)()%7D)()%3B) - from [Erik's Bookmarklets](https://tools.eriknewhard.com/bookmarklets). This bookmarklet will copy the title and url in two formats. One, when you go to paste into a document or email it will be a link, or two, when you paste into something text only it will be the plain text title and then URL
* [URL to Markdown](javascript:(function()%20%7B%20%20function%20copyToClipboard(text)%20%7B%20%20%20%20%20if%20(window.clipboardData%20&&%20window.clipboardData.setData)%20%7B%20%20%20%20%20%20%20%20%20/*IE%20specific%20code%20path%20to%20prevent%20textarea%20being%20shown%20while%20dialog%20is%20visible.*/%20%20%20%20%20%20%20%20%20return%20clipboardData.setData(%22Text%22,%20text);%20%20%20%20%20%20%20%7D%20else%20if%20(document.queryCommandSupported%20&&%20document.queryCommandSupported(%22copy%22))%20%7B%20%20%20%20%20%20%20%20%20var%20textarea%20=%20document.createElement(%22textarea%22);%20%20%20%20%20%20%20%20%20textarea.textContent%20=%20text;%20%20%20%20%20%20%20%20%20textarea.style.position%20=%20%22fixed%22;%20%20/*%20Prevent%20scrolling%20to%20bottom%20of%20page%20in%20MS%20Edge.*/%20%20%20%20%20%20%20%20%20document.body.appendChild(textarea);%20%20%20%20%20%20%20%20%20textarea.select();%20%20%20%20%20%20%20%20%20try%20%7B%20%20%20%20%20%20%20%20%20%20%20%20%20return%20document.execCommand(%22copy%22);%20%20/*%20Security%20exception%20may%20be%20thrown%20by%20some%20browsers.*/%20%20%20%20%20%20%20%20%20%7D%20catch%20(ex)%20%7B%20%20%20%20%20%20%20%20%20%20%20%20%20console.warn(%22Copy%20to%20clipboard%20failed.%22,%20ex);%20%20%20%20%20%20%20%20%20%20%20%20%20return%20false;%20%20%20%20%20%20%20%20%20%7D%20finally%20%7B%20%20%20%20%20%20%20%20%20%20%20%20%20document.body.removeChild(textarea);%20%20%20%20%20%20%20%20%20%7D%20%20%20%20%20%7D%20%7D%20%20var%20markdown%20=%20'%5B'%20+%20document.title%20+%20'%5D('%20+%20window.location.href%20+%20')';%20copyToClipboard(markdown);%20%7D)();)

# Other bookmarklets

* [Archive.IS](javascript:(function()%7Bwindow.open('https%3A%2F%2Farchive.is%2F'%2Bdocument.location.href)%7D)()) - Bypass paywalls by viewing the current website on [archive.is](https://archive.is)
* [ROT13](javascript:(function()%7Bjavascript%3A%20var%20coding%20%3D%20%22abcdefghijklmnopqrstuvwxyzabcdefghijklmABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLM%22%3B%20%20function%20rot13(t)%20%7B%20for%20(var%20r%20%3D%20%22%22%2C%20i%20%3D%200%3B%20i%20%3C%20t.length%3B%20i%2B%2B)%20%7B%20character%20%3D%20t.charAt(i)%3B%20position%20%3D%20coding.indexOf(character)%3B%20if%20(position%20%3E%20-1)%20character%20%3D%20coding.charAt(position%20%2B%2013)%3B%20r%20%2B%3D%20character%3B%20%7D%20return%20r%3B%20%7D%20S%20%3D%20window.getSelection()%3B%20%20function%20t(N)%20%7B%20return%20N.nodeType%20%3D%3D%20N.TEXT_NODE%3B%20%7D%20%20function%20r(N)%20%7B%20if%20(t(N))%20N.data%20%3D%20rot13(N.data)%3B%20%7D%20for%20(j%20%3D%200%3B%20j%20%3C%20S.rangeCount%3B%20%2B%2Bj)%20%7B%20var%20g%20%3D%20S.getRangeAt(j)%2C%20e%20%3D%20g.startContainer%2C%20f%20%3D%20g.endContainer%2C%20E%20%3D%20g.startOffset%2C%20F%20%3D%20g.endOffset%2C%20m%20%3D%20(e%20%3D%3D%20f)%3B%20if%20(!m%20%7C%7C%20!t(e))%20%7B%20%2F*%20rot13%20each%20text%20node%20between%20e%20and%20f%2C%20not%20including%20e%20and%20f.%20*%2F%20q%20%3D%20document.createTreeWalker(g.commonAncestorContainer%2C%20NodeFilter.SHOW_ELEMENT%20%7C%20NodeFilter.SHOW_TEXT%2C%20null%2C%20false)%3B%20q.currentNode%20%3D%20e%3B%20for%20(N%20%3D%20q.nextNode()%3B%20N%20%26%26%20N%20!%3D%20f%3B%20N%20%3D%20q.nextNode())%20r(N)%3B%20%7D%20if%20(t(f))%20f.splitText(F)%3B%20if%20(!m)%20r(f)%3B%20if%20(t(e))%20%7B%20r(k%20%3D%20e.splitText(E))%3B%20if%20(m)%20f%20%3D%20k%3B%20e%20%3D%20k%3B%20%7D%20if%20(t(f))%20g.setEnd(f%2C%20f.data.length)%3B%20%7D%20void%200%7D)()) - ROT13 the selected text, usually for spoilers. This is not encryption!

# Bookmarklet tools

* [Bookmarklet Creator with Script Includer - Peter Coles](https://mrcoles.com/bookmarklet/)
* [Bookmarkify.it - Create bookmarklets from your javascript!](https://bookmarkify.it/)
