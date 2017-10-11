# no-avatar
Express middleware to generate dummy avatar with name initials


## Install 
npm i -S no-avatar

## Install GraphicsMagick
http://www.graphicsmagick.org/download.html

> test installation by running `gm -version`


## use as express middleware
```
const { middleware } = require('no-avatar');
app.get('/avatar.png', middleware);
```

> Accessing `/avatar.png` route will return a png image. You can configure image by adding options in query parameters as below.


## create avatar manually

```
const fs = require('fs');
const { make } = require('no-avatar');

make(options, function(err, buffer){
	if(err) return console.log(err);
			return fs.writeFileSync(__dirname + '/avatar.png', buffer);
});
```


## options (also query object)
- width (integer) : pixel image width. Default 150.
- height (integer) : pixel image height. Default 150.
- text (string) : name initials. You can pass name as well, initials will be created automatically. By default, 'NO' is used.
- bgColor (hex color code) : Background color of image. No need to add pound (#) sing, will be added automatically. By default, background color is chosen randomly from a pallet.
- fontColor (hex color code) : Text (font) color. No need to add pound (#) sing, will be added automatically. By default, font color is `ffffff` (white).
- fontSize (integer) : Text (font) size.

***

## middleware test
node demo/server.js and visit `http://localhost:3000/avatar.png?text=UH&fontSize=80`

## manually creating test
node demo/create.js and check `avatar.png` in that folder.