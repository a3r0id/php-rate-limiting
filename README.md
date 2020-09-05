# php-rate-limiting
A simple system to rate-limit site visitors by time interval/request amount.

Adjust specifications via config.json.

-------
Security Issue:
Many webservers will serve `.json` files willingly, this is bad if our config/database file is ocated within our service area aka: `/var/www/*`.
Fix:
You can literally change the file extension to ANYTHING, use `.conf` for best security as most webservers will not server them by default.


## Usage
```php
<?php
require "rate-limiting.php";
echo "hello world!";
?>
```
