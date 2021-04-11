# php-rate-limiting
A simple system to rate-limit site visitors by time interval/request amount.

![](https://pbs.twimg.com/profile_images/664136112353492992/Xr4FwuAE_400x400.png)

Adjust specifications via config.json (aka rate-limiting.conf).

-------

## Usage:

[1] Edit your configuration:

Notes:
<br/>
If "die_on_rate_limit" is false then visitor will be redirected to the "redirect_location" when limited. 
<br/>
"request_allowance" should always be (amount to allow + 1) as in regards to the example config, it will limit the visitor on their 25th request, NOT THE 26th!

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
