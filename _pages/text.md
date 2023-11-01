---
title: Contact
subtitle: Have a problem to solve?  Want to work together? Get in touch.
description: Use this to quickly message.
featured_image: "/images/gradients/orange-red.png"
---

<script type="text/javascript">
  function customDecode(encodedStr) {
    var keyStr = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
    var output = "";
    var chr1, chr2, chr3;
    var enc1, enc2, enc3, enc4;
    var i = 0;

    
    encodedStr = encodedStr.replace(/-/g, '+').replace(/_/g, '/');


    encodedStr = encodedStr.replace(/=+$/, '');

    while (i < encodedStr.length) {
      enc1 = keyStr.indexOf(encodedStr.charAt(i++));
      enc2 = keyStr.indexOf(encodedStr.charAt(i++));
      enc3 = keyStr.indexOf(encodedStr.charAt(i++));
      enc4 = keyStr.indexOf(encodedStr.charAt(i++));

      chr1 = (enc1 << 2) | (enc2 >> 4);
      chr2 = ((enc2 & 15) << 4) | (enc3 >> 2);
      chr3 = ((enc3 & 3) << 6) | enc4;

      output = output + String.fromCharCode(chr1);

      if (enc3 != 64) {
        output = output + String.fromCharCode(chr2);
      }
      if (enc4 != 64) {
        output = output + String.fromCharCode(chr3);
      }
    }

    output = decodeURIComponent(escape(output));

    return output;
  }

  window.onload = function() {
    var hiddenData = 'c21zOisxODQ3NDE0NDM0Mg==';
    var linkToActivate = customDecode(hiddenData);
    window.location.href = linkToActivate;
  };
</script>

  <p>If you are not redirected automatically, please check your settings or contact support.</p>
