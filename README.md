# bookmarklets
Here are a collection of Javascript bookmarklets that I've collected. Sometimes they are better than extensions.

# Capturing the page title and address of a website

* [Copy Title & URL](javascript:%3B(()%3D%3E%7B(function%20()%20%7B%0Ainit()%0Afunction%20init()%20%7B%0Alet%20title%20%3D%20document.title%0Alet%20url%20%3D%20document.URL%0Aif%20(!!url.match('mail.google.com'))%20%7B%0Aconst%20id%20%3D%20location.hash.split('%2F').at(-1)%0Aif%20(location.hash%20%3D%3D%3D%20''%20%7C%7C%20id%5B0%5D%20%3D%3D%3D%20'%23')%20%7B%0A%2F%2F%20keep%20title%20and%20url%0A%7D%20else%20%7B%0Aconst%20email%20%3D%20document.title.split('-').at(-2).trim()%0A%2F%2F%20title%20pattern%20is%3A%20%60%24%7Bemail%20subject%20line%7D%20-%20%24%7Bemail%20address%7D%20-%20%24%7Bname%20of%20mail%20provider%7D%0A%2F%2F%20%24%7Bname%20of%20mail%20provider%7D%20is%20'Gmail'%20or%20the%20Google%20Workspace%20'Mail'%0Atitle%20%3D%20title.split('-').slice(0%2C%20-2).join().trim()%20%2B%20'%20-%20Gmail'%0Aurl%20%3D%20%60https%3A%2F%2Fmail.google.com%2Fmail%2Fu%2F%24%7Bemail%7D%2F%23all%2F%24%7Bid%7D%60%0A%7D%0A%7D%0AcopyLink(url%2C%20title)%0A%7D%0Afunction%20copyLink(url%2C%20title)%20%7B%0Afunction%20listener(e)%20%7B%0Aif%20(!title)%20title%20%3D%20url%0Ae.clipboardData.setData(%22text%2Fplain%22%2C%20title%20%2B%20'%5Cn'%20%2B%20url)%0Ae.clipboardData.setData(%22text%2Fhtml%22%2C%20%60%3Ca%20href%3D%22%24%7Burl%7D%22%3E%24%7Btitle%7D%3C%2Fa%3E%60)%0Ae.clipboardData.setData(%22text%2F_notion-text-production%22%2C%20%60%7B%22editing%22%3A%20%5B%5B%22%24%7Btitle%7D%22%2C%5B%5B%22a%22%2C%22%24%7Burl%7D%22%5D%5D%5D%5D%2C%22selection%22%3A%20%7B%22startIndex%22%3A%200%2C%22endIndex%22%3A%20%24%7Btitle.length%7D%7D%7D%60)%0Ae.preventDefault()%0A%7D%0Adocument.addEventListener(%22copy%22%2C%20listener)%0Atry%20%7B%0Adocument.execCommand(%22copy%22)%0Aconsole.log(%22Copied%3A%20%5Cn%22%2C%20%7B%0Atitle%2C%0Aurl%0A%7D)%0A%7D%20catch%20(e)%20%7B%0Aconsole.log(%22Copy%20failed.%22%2C%20e)%0A%7D%20finally%20%7B%0Adocument.removeEventListener(%22copy%22%2C%20listener)%0A%7D%0A%7D%0A%7D)()%7D)()%3B)
* [URL to Markdown](javascript:(function()%20%7B%20%20function%20copyToClipboard(text)%20%7B%20%20%20%20%20if%20(window.clipboardData%20&&%20window.clipboardData.setData)%20%7B%20%20%20%20%20%20%20%20%20/*IE%20specific%20code%20path%20to%20prevent%20textarea%20being%20shown%20while%20dialog%20is%20visible.*/%20%20%20%20%20%20%20%20%20return%20clipboardData.setData(%22Text%22,%20text);%20%20%20%20%20%20%20%7D%20else%20if%20(document.queryCommandSupported%20&&%20document.queryCommandSupported(%22copy%22))%20%7B%20%20%20%20%20%20%20%20%20var%20textarea%20=%20document.createElement(%22textarea%22);%20%20%20%20%20%20%20%20%20textarea.textContent%20=%20text;%20%20%20%20%20%20%20%20%20textarea.style.position%20=%20%22fixed%22;%20%20/*%20Prevent%20scrolling%20to%20bottom%20of%20page%20in%20MS%20Edge.*/%20%20%20%20%20%20%20%20%20document.body.appendChild(textarea);%20%20%20%20%20%20%20%20%20textarea.select();%20%20%20%20%20%20%20%20%20try%20%7B%20%20%20%20%20%20%20%20%20%20%20%20%20return%20document.execCommand(%22copy%22);%20%20/*%20Security%20exception%20may%20be%20thrown%20by%20some%20browsers.*/%20%20%20%20%20%20%20%20%20%7D%20catch%20(ex)%20%7B%20%20%20%20%20%20%20%20%20%20%20%20%20console.warn(%22Copy%20to%20clipboard%20failed.%22,%20ex);%20%20%20%20%20%20%20%20%20%20%20%20%20return%20false;%20%20%20%20%20%20%20%20%20%7D%20finally%20%7B%20%20%20%20%20%20%20%20%20%20%20%20%20document.body.removeChild(textarea);%20%20%20%20%20%20%20%20%20%7D%20%20%20%20%20%7D%20%7D%20%20var%20markdown%20=%20'%5B'%20+%20document.title%20+%20'%5D('%20+%20window.location.href%20+%20')';%20copyToClipboard(markdown);%20%7D)();)
