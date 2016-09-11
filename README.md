Emoji Password Mask
===================

Tired of annoying password meters?! This one allows you to replace the characters
with your choice of emoji to represent the strength of the password on a scale
from 0-4. This project was thrown together in a very small period of time sparked
by a conversation I had with []()

Use
====

This depends on [MaskedPassword.js](https://www.sitepoint.com/better-passwords-1-the-masked-password-field/)
from an article on sitepoint, Mathias Bynens' .at polyfill](), dropbox's zxcvbn librarty]() for
password strength.

See the index.html file for a working example.

Once you've got all those dependencies in your browser, just call:

`new MaskedPassword([id-of-element], [emoji-config]);`

A hidden field with the real password will be created.

Example:
=======

```javascript
(function(){
  // a small config of scores : emoji
  // 0 # too guessable: risky password. (guesses < 10^3)
  // 1 # very guessable: protection from throttled online attacks. (guesses < 10^6)
  // 2 # somewhat guessable: protection from unthrottled online attacks. (guesses < 10^8)
  // 3 # safely unguessable: moderate protection from offline slow-hash scenario. (guesses < 10^10)
  // 4 # very unguessable: strong protection from offline slow-hash scenario. (guesses >= 10^10)

  var symbolConfig = {
      "0": "💩",
      "1": "🍑",
      "2": "💨",
      "3": "🌟",
      "4": "👍"
  };


  new MaskedPassword(document.getElementById("pword"), symbolConfig);

})();

```

TODO
=====

[ ] - I haven't actually coded up what happens when the form submits. One would
probably have to swap out some names to get the real value on the server.
[ ] - Make the index.html page pretty.


Resources:
==========

* [MaskedPassword.js](https://www.sitepoint.com/better-passwords-1-the-masked-password-field/) - using alternative masks (via silly hacks for replacing dots)
* [zxcvbn](https://github.com/dropbox/zxcvbn) - password strength
* [emojipedia](http://emojipedia.org/) - for grabbing emoji
* [JavaScript has a Unicode problem](https://mathiasbynens.be/notes/javascript-unicode) - For understanding why JS and Emoji is so hard
* [String.prototype.at](https://github.com/mathiasbynens/String.prototype.at) - Polyfill for CharAt
* [String.prototype.codePointAt](https://github.com/mathiasbynens/String.prototype.codePointAt) - For finding emoji in strings
