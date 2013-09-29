# Profiler

This is an active fork of the recently-abandoned [juy/profiler](https://github.com/juy/profiler).

## What's New

- Toggle Profiler by visiting yoursite.dev*/_profiler/toggle*
- Code, comment, and readme cleanup

[![](https://dl.dropboxusercontent.com/u/76869590/laravel-package/juy-profiler.png)](https://dl.dropboxusercontent.com/u/76869590/laravel-package/juy-profiler.png "Click for big picture")

## Features

- Environment info
- Current controller/action info
- Routes
- Log events
- SQL query log with syntax highlighting
- Total execution time
    - Custom "checkpoints", see [this section](#custom-timers)
- Total memory usage
- Included files
- All variables passed to views
- Session variables
- Laravel auth variables
- Sentry auth variables

## Installation
To add Profiler to your Laravel application, follow these three steps:

Add the following to your `composer.json` file:

```json
"ericmagnuson/profiler" : "dev-master"
```

Then, run `composer update` or `composer install` if you have not already installed packages.

Add the below line to the `providers` array in `app/config/app.php` configuration file (add at the end):

```php
'Ericmagnuson\Profiler\Providers\ProfilerServiceProvider',
```

Add the below line to the `aliases` array in `app/config/app.php` configuration file (add at the end):

```php
'Profiler' => 'Ericmagnuson\Profiler\Facades\Profiler',
```

## Configuration

You will want to run the following command to publish the config to your application, otherwise it will be overwritten when the package is updated.

```shell
php artisan config:publish ericmagnuson/profiler
```

### Profiler

Set this option to `FALSE` to disable Profiler. By default, it is `NULL`, which makes the profiler refer to the app debug option in `config/app.php`.

```php
// config.php
'profiler' => NULL
```

If you wish to disable Profiler during your application, just do:

```php
Config::set('profiler::profiler', FALSE);

// or

Profiler::disable();
```

>**Note::** Profiler will still do its background listening but will not output it to the browser.

## Usage

### Custom Timers

To start a timer, all you need to do is:

```php
Profiler::start('my timer key');
```

To end the timer, simply call the end function like so:

```php
Profiler::end('my timer key');
```

## Logging

Profiler utilizes Laravel's built in logging system and captures logged events. To log events, you can do (as you would with Laravel) any of these:

```php
Log::debug('Your message here');
Log::info('Your message here');
Log::notice('Your message here');
Log::warning('Your message here');
Log::error('Your message here');
Log::critical('Your message here');
Log::alert('Your message here');
Log::emergency('Your message here');
```

These are color-coded in the logs section of Profiler – colors may change in future to more accurately reflect the log type.

## Credit

- Backend based on [sorora/omni](https://github.com/sorora/omni)
- Frontend based on [loic-sharma/profiler](https://github.com/loic-sharma/profiler)
- Other features inspired by [juy/profiler](https://github.com/juy/profiler) and [papajoker/profiler](https://github.com/papajoker/profiler
