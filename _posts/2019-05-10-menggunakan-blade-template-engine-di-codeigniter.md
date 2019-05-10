---
layout: post
title: Menggunakan Blade Template Engine di Codeigniter
---

```php
// application/config/config.php

$config[‘composer_autoload’] = FALSE;

// ubah menjadi
$config[‘composer_autoload’] = ‘vendor/autoload.php’;
```

```bash
composer require jenssegers/blade
```

```php
// application/helpers/view_helper.php

<?php

use Jenssegers\Blade\Blade;

if (!function_exists('view')) {
	function view($view, $data = []) {
		$path = APPATH.'views';
		$blade = new Blade($path, $path . '/cache');

		echo $blade->make($view, $data);
	}
}
```

```php
// application/config/autoload.php

$autoload[‘helper’] = array(‘view’);
```

```php
// controller

return view('index', ['posts' => $data]);
```

Lalu pada folder `views`, gunakan ekstensi `blade.php`