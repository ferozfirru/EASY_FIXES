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

## MariaDB
### Ignoring order by in sub query - Fix

```mysql
select * from (SELECT * FROM `table` where login = 'y' order by timestamp desc limit 0,18446744073709551615) as temp  group by type /* This Number is the Max number for rows as said in mysql docs dev.mysql.com/doc/refman/5.7/en/select.html*/
```
