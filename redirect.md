## Redirect

Redirect adalah pengalihan halaman web dari URL yang kita masukan ke URL lain. Pengalihan dilakukan oleh pengembang dengan alasan tertentu misal URL lama yang tidak dipakai dialihkan ke URL baru.
.

### HTML redirect

```
<meta http-equiv="refresh" content="0; URL='http://new-website.com'" />
```

### JavaScript redirect

```
window.location = "http://new-website.com";
```

Atau cara lainnya 

```
window.location = "http://new-website.com";
window.location.href = "http://new-website.com";
window.location.assign("http://new-website.com");
window.location.replace("http://new-website.com");
```

### Apache redirect

Di dalam file .htaccess ditulis sbb :

```
Redirect 301 / http://www.new-website.com
```

atau cara lain

```
RedirectMatch 301 /blog(.*) http://www.new-website.com$1
```

```
Redirect 301 /page.html http://www.old-website/new-page.html
```

```
<IfModule mod_rewrite.c>
  RewriteEngine on
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule .* 404.html [L]
</IfModule>
```

### Nginx redirect

Pada file nginx.conf ditulis sbb

```
server {
  listen 80;
  server_name old-website.com;
  return 301 $scheme://new-website.com$request_uri;
}
```

### PHP redirect

```
<?php 
  header('Location: http://www.new-website.com');
  exit;
?>
```
 atau cara lain

```
<?php
  header('Location: http://www.new-website.com/', true, 301);
  exit();
?>
```

### Ruby on Rails redirect

```
class WelcomeController < ApplicationController
  def index
    redirect_to 'http://new-website.com', :status => :moved_permanently 
  end
end
```

Atau cara lain

```
get "/blog" => redirect("http://new-website.com")
```

```
get "/blog/:post" => redirect("http://new-website.com/blog/%{post}")
```

### Node.js redirect

```
var http = require("http");

http.createServer(function(req, res) {
  res.writeHead(301,{Location: 'http://new-website.com'});
  res.end();
}).listen(8888);
```

```
var http = require("http");
var url = require("url");

http.createServer(function(req, res) {
  var pathname = url.parse(req.url).pathname;
  res.writeHead(301,{Location: 'http://new-website.com/' + pathname});
  res.end();
}).listen(8888);
```

Sumber : [https://css-tricks.com/redirect-web-page/]
