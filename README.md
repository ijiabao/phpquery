# phpQuery 原始镜像

>此为phpQuery原始源码，项目主页: http://code.google.com/p/phpquery/

####为解决源版网络不通问题而生，未做任何修改。

## 原始说明文档

* [Manual](wiki/README.md) 此文档来自 http://code.google.com/p/phpquery/wiki

````
composer安装：
composer require ijiabao/phpquery

注：如果项目中已包含其它源内的phpQuery,则无需安装此源。
````

>简单使用：
```php

<?php
$html = file_get_contents('http://www.jurlu.com/');
$doc = phpQuery::newDocumentHTML($html);
// 类似 jQuery, 查找、修改相关属性
$doc->find('.service-title')->each(function(DOMElement $dom){
    echo pq($dom)->addClass('some')->attr('data-id', 'myId')->html();
});
// save modified
file_put_contents('test.html', $doc->html());

```

### 此源码的其它 github 仓库参见:

* https://github.com/denis-isaev/phpquery
* https://github.com/fmorrow/pQuery--PHPQuery- (big project so far)
* https://github.com/r-sal/phpquery
* https://github.com/damien-list/phpquery-1
* https://github.com/nev3rm0re/phpquery
* https://github.com/Aurielle/phpquery
* https://github.com/kevee/phpquery (include php-css-parser)
* https://github.com/lucassouza1/phpquery



### 原始 README.md：

### Whats phpQuery?
To quote the phpQuery *(orignally concieved and developed by Tobiasz Cudnik, available on Google Code and Github)* project documentation:

>phpQuery is a server-side, chainable, CSS3 selector driven Document Object Model (DOM) API based on jQuery JavaScript Library.
>
>Library is written in PHP5 and provides additional Command Line Interface (CLI).

### Example usage

(copied from http://code.google.com/p/phpquery/wiki/Basics)

Complete working example:

```php
<?php
include 'phpQuery-onefile.php';

$file = 'test.html'; // see below for source

// loads the file
// basically think of your php script as a regular HTML page running client side with jQuery.  This loads whatever file you want to be the current page
phpQuery::newDocumentFileHTML($file);

// Once the page is loaded, you can then make queries on whatever DOM is loaded.
// This example grabs the title of the currently loaded page.
$titleElement = pq('title'); // in jQuery, this would return a jQuery object.  I'm guessing something similar is happening here with pq.

// You can then use any of the functionality available to that pq object.  Such as getting the innerHTML like I do here.
$title = $titleElement->html();

// And output the result
echo '<h2>Title:</h2>';
echo '<p>' . htmlentities( $title) . '</p>';

?>
```

====

Source for test.html:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<title>Hello World!</title>
</head>
<body>
</body>
</html>
```

