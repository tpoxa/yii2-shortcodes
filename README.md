yii2-shortcodes
===============

Wordpress style shorttags for Yii2

Installation
------------
```code
{
	"require": {
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
Add shortcodes component
```code
'components' => array(
        ...
        'shortcodes' => [
            'class' => 'tpoxa\shortcodes\Shortcode',
            'callbacks' => [
                'lastphotos' => ['frontend\widgets\lastPhoto\lastPhoto', 'widget'],
                'anothershortcode'=>function($attrs, $content, $tag){
                ///
                },
                
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
callbacks  - An array of valid PHP callbacks. Keys should contain names of the shortcodes.

lastPhoto example class - common Yii2 widget

```php
namespace frontend\widgets\lastPhoto; // your App class

use yii\base\Widget;
class lastPhoto extends Widget {

    public $limit = 5; // this parameter will be overwritten by 8 

    public function run() {
        // your widget content goes here
    }

}
```
