# php-rate-limiting
A simple system to rate-limit site visitors by time interval/request amount.

Adjust specifications via config.json.

-------
Security Issue:
Many webservers will serve `.json` files willingly, this is bad if our config/database file is located within our service area (`/var/www/*` in most cases).

Fix:
You can literally change the file extension to ANYTHING, use `.conf` for best security as most webservers will not server them by default.

-------

## Update
 __For quick-setup, potentially unsafe, you'll literally just drop contents of DIST/ to the directory of your php files being served.__



## Usage:

[1] Edit your configuration:
```json
[
    {
        "database_file_name": "requests.db",
        "interval_time_seconds": 300,
        "request_allowance": 25,
        "redirect_location": "https://google.com",
        "die_on_rate_limit": false 
    }
]
```
[2] Simply transfer the contents of `dist/` to your PHP include path.

[3] - Include in your project
```php
<?php
require "rate-limiting.php";// Process request
echo "hello world!";// If not limited, serve the rest of the file.
?>
```
Note: Process may fail on the first run but will stay persistant after the first request through the file.
