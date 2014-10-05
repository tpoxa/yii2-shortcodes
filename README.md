yii2-shortcodes
===============

Wordpress style shorttags for Yii2

Installation
------------
```code
{
	"require": 
	{
  		"tpoxa/shortcodes": "dev-master"
	}
}
```
Configuration
-------------
In config file
```code
/config/main.php
```
Add image component
```code
'components' => array(
        ...
        'shortcodes' => [
            'class' => 'tpoxa\shortcodes\Shortcode',
            'callbacks' => [
                'lastphotos' => ['frontend\widgets\lastPhoto\lastPhoto', 'widget'],
            ]
        ],
```
Usage
-----
```php

echo \Yii::$app->shortcodes->parse('
            <div><b>some content</b>  [lastphotos limit=8]  ></div>
    ')

```

Additional
----
callbacks array on any valid PHP callbacks
lastPhoto example class - Yii2 widget

```php
namespace frontend\widgets\lastPhoto; // your app class

use yii\base\Widget;
class lastPhoto extends Widget {

    public $limit = 5; // this parameter will be overwritten by 8 

    public function run() {
        // your widget content goes here
    }

}
```
