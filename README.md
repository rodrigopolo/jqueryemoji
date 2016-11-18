# jQueryEmoji

Yet another jQuery emoji parser plug-in, designed differently to be fast, small, simple and scalable.

* Based on the lates (beta) iOS / macOS release with 162 new emojis.
* Faster, regex sorted to match most commonly used emojis.
* Compact, only 15KiB for the JS.
* All PNG images extremely optimized.
* Quick install with Bower.

## Installation

Include jQuery and jQueryEmoji.js in your HTML document.
```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
<script src="js/jQueryEmoji.js"></script>
```

if you want to tweak the image tags, include your stylesheet.
```html
<link href="css/style.css" rel="stylesheet">
```

And select the elements you want to parse with a jQuery selector.
```js
$(function(){
	$('p').Emoji();
});
```

You can set specific settings, like image path, CSS class and the file name extension:
```js
$(function(){
	$('p').Emoji({
		path:  'img/emojione/',
		class: 'emoji',
		ext:   'png'
	});
});
```

#### Bower
```
bower install jqueryemoji
```

#### Demo
http://rodrigopolo.github.io/jqueryemoji/

## Why a different approach?

Other emoji JavaScript libraries try to cope with Unicode Emoji by using complex regular expressions ranges to catch every possible emoji combination, even the ones that haven´t been adopted by big brands and doesn´t have any existent image that represent them, that´s a huge problem.

jQueryEmoji has a different approach for dealing with emoji code points, it doesn´t cope with the complex Unicode regular expressions ranges but instead it uses a regular expression that contains all the existent emojis available on the latest iOS and macOS as they would be typed, by using this approach, you can be certain that every emoji that is matched has an existent image that represent it.

The second greatest thing of jQueryEmoji that make it faster than other libraries is its regular expression order, it is sorted by the most frequenly used emojis based on real users information tracked live from Twitter by www.emojitracker.com, and to make a little step further, the second level of sorting is based on the iOS Emoji keyboard layout order.

And that’s not all, jQueryEmoji  avoids sprites and long CSS sheets, this is mainly because having a 1,767 sprite sheet is just crazy, so it loads every image as needed, which leads us to the next step, all Apple PNG images extracted from the latest macOS emoji font are optimized and squeezed to the maximum, all 1,767 40x40 PNG images weight only 3.02MiB, just about 1.75KiB per emoji, and the big 72x72 PNG images weight just 5.12MiB, an average of 2.96KiB per image without loosing any image quality.  

Bu there’s more, all emoji images have the actual emoji as the alt HTML attribute, if the user copies the text it takes the real emoji character with it, also, jQueryEmoji as a jQuery plug-in have options you can set to make it fit your needs, you can change the image path and use other emojis, you can change the class attribute for the image tag to change the style, you can set the file extension and use SVG files for instance, and you can enable or disable the alt attribute. 

And if all of the above isn’t enough, jQueryEmoji is in Bower, making it easier to install on your projects.

## Other assets

You can use other emoji images other than the ones from Apple, I have made available a bunch of asset generators in [this other repo](https://github.com/rodrigopolo/emoji-assets), but they aren’t up to date, at the moment of this update here are the number of missing images for each library:

* Emoji One: 156
* Twemoji: 156
* Google: 394
* Microsoft: 401

This repo has texts files listing for the missing emoji images for each emoji library, they are located under the image folder, you can use this list to look for replacements or to copy the Apple images to other folder so you can replace the ones missing, there is also a work around using Apache and a file called .htaccess to redirect unexistent image file request to your Apple emoji folder, here are some examples:

```
RewriteEngine On
RewriteCond %{REQUEST_URI} twemoji_svg\/(?:[\w-]+).(?:png|svg)$ [NC]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule twemoji_svg\/([\w-]+).(png|svg)$ ./apple40/$1.png
```

```
RewriteEngine On
RewriteCond %{REQUEST_URI} twemoji\/(?:[\w-]+).(?:png|svg)$ [NC]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule twemoji\/([\w-]+).(png|svg)$ ./apple40/$1.png
```

```
RewriteEngine On
RewriteCond %{REQUEST_URI} microsoft\/(?:[\w-]+).(?:png|svg)$ [NC]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule microsoft\/([\w-]+).(png|svg)$ ./apple40/$1.png
```

```
RewriteEngine On
RewriteCond %{REQUEST_URI} google\/(?:[\w-]+).(?:png|svg)$ [NC]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule google\/([\w-]+).(png|svg)$ ./apple40/$1.png
```

```
RewriteEngine On
RewriteCond %{REQUEST_URI} emojione\/(?:[\w-]+).(?:png|svg)$ [NC]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule emojione\/([\w-]+).(png|svg)$ ./apple40/$1.png
```

-------

### Donations
[PayPal](http://paypal.me/rodrigopolo)


-------

### License

(The MIT License)

Copyright (c) by Rodrigo Polo http://RodrigoPolo.com

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

