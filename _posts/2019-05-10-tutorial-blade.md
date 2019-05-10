---
layout: post
title: Tutorial Blade
---

We will be using `@include` to bring in slices and `@yield` to bring in content from the individual pages we will be using.

```php
<!doctype html>
<html>
<head>
    @include('includes.head')
</head>
<body>
<div class="container">

    <header class="row">
        @include('includes.header')
    </header>

    <div id="main" class="row">

            @yield('content')

    </div>

    <footer class="row">
        @include('includes.footer')
    </footer>

</div>
</body>
</html>
```

Blade lets us use the layout that we just created by using `@extends`. By creating `@section`, we create a section that will be used in the layout. Here we use `@section('content')` and in our layout, all that we type here will be injected in `@yield` in the layout.

```php
@extends('layouts.default')
@section('content')
    i am the home page
@stop
```