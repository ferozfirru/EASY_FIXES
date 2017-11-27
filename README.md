# EASY_FIXES
## php
### base64 url safe

```PHP
function base64_safeurl_encode($string) { 
  	return rtrim(strtr(base64_encode($string), '+/', '-_'), '='); 
} 
function base64_safeurl_decode($string) { 
 	return base64_decode(strtr($string, '-_', '+/').(strlen($string)%4 == 2?'==':(strlen($string)%4 == 3?'=':''))); 
}
```
