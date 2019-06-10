# Affinity4/DebugBar

Displays a debug bar in the browser with information from php.
No more `var_dump()` in your code!

## Documentation

See [PHP DebugBar](http://phpdebugbar.com/docs) for full docs

Any changes to the standard API will be below.

## Installation

The best way to install DebugBar is using [Composer](http://getcomposer.org)
with the following command:

```composer require affinity4/debugbar```

## Quick start

DebugBar is very easy to use and you can add it to any of your projects in no time.
The easiest way is using the `render()` functions

```PHP
<?php

// Require the Composer autoloader, if not already loaded
require 'vendor/autoload.php';

use Affinity4\DebugBar\StandardDebugBar;

$debugbar = new StandardDebugBar();
$debugbarRenderer = $debugbar->getJavascriptRenderer();

$debugbar["messages"]->addMessage("hello world!");
?>
<html>
    <head>
        <?php echo $debugbarRenderer->renderHead() ?>
    </head>
    <body>
        ...
        <?php echo $debugbarRenderer->render() ?>
    </body>
</html>
```

The DebugBar uses DataCollectors to collect data from your PHP code. Some of them are
automated but others are manual. Use the `DebugBar` like an array where keys are the
collector names. In our previous example, we add a message to the `MessagesCollector`:

```PHP
$debugbar["messages"]->addMessage("hello world!");
```

`StandardDebugBar` activates the following collectors:

 - `MemoryCollector` (*memory*)
 - `MessagesCollector` (*messages*)
 - `PhpInfoCollector` (*php*)
 - `RequestDataCollector` (*request*)
 - `TimeDataCollector` (*time*)
 - `ExceptionsCollector` (*exceptions*)

Learn more about DebugBar in the [docs](http://phpdebugbar.com/docs).
