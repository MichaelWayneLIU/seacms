### seacms V6.61 has xss vulnerability in site name parameter of admin_config.php 

In login with admin and visit http://127.0.0.1/seacms/adm1n/admin_config.php to set the web site name as 
```
<img src=x onerror=alert(1)>

```
Then save it.

![image](1.png)

There is a alert box when browse the site again.In other words,there is xss vulnerability.

![image](2.png)

