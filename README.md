## Slack Dark Mode

An easy way to implement dark mode in Slack on Mac OS. Requires High Sierra or later. Adapted from https://dev.to/changoman/easy-dark-mode-for-slack-1mmn.

On a Mac, navigate to this directory:

```
cd /Applications/Slack.app/Contents/Resources/app.asar.unpacked/src/static
```

Edit the file ssb-interop.js with a text editor.

Add this code to the very bottom (*edited thanks to amerritt14 for code support):

```javascript
//SLACK DARK MODE
document.addEventListener('DOMContentLoaded', function() {
 $.ajax({
   url: 'https://github.com/spiggott/slack-dark-mode/blob/master/black.css',
   
   success: function(css) {
     let overrides = `
     code { background-color: #535353; color: #85c5ff; } /* Change color: to whatever font color you want */
     .c-mrkdwn__pre, .c-mrkdwn__quote { background: #535353 !important; background-color: #535353 !important; }
     `
     $("<style></style>").appendTo('head').html(css + overrides);
   }
 });
});
```

Save the file and restart Slack. Dark Mode should be enabled!
