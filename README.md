# TwitterPicProfile

Update your twitter profile pic with base64 image

## Installing

`npm install twitter-pic`

## Usage

```
var TwitterPicProfile = require('twitter-pic-profile'),
    request    = require('request')
;

var t = new TwitterPicProfile({
    consumer_key:    'w',
    consumer_secret: 'x',
    token:           'y',
    token_secret:    'z'
});

/* you'll need to already have the img variable defined as a base64 string. 
In my case, I send this via socket.io from Backbone to Node.js, then send to 
Twitter in the callback fn which has the img data */

// details about the params below can be found in
// https://api.twitter.com/1/account/update_profile_background_image.json
t.update({
    status: 'This can be a status',
    media: new Buffer(img, 'base64'),
    // in_reply_to_status_id: 000000,
    // possibly_sensitive: false,
    // lat: 37.7821120598956,
    // long: -122.400612831116,
    // place_id: 'df51dec6f4ee2b2c',
    // display_coordinates: true
},
function (err, result) {
    if (err) {
        return console.error('Nope!', err);
    }

    console.log(result);
});
```
