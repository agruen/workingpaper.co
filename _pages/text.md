---
title: Contact
subtitle: Have a problem to solve?  Want to work together? Get in touch.
description: Use this to quickly message.
featured_image: "/images/gradients/orange-red.png"
---

<script type="text/javascript">
// This function parses the query string and returns the value for the specified key
function getQueryStringValue(key) {
  const queryString = window.location.search;
  const urlParams = new URLSearchParams(queryString);
  return urlParams.get(key);
}

// This function creates the SMS link and opens it
function sendSMS() {
  // Get the phone number from the URL parameter 'phone'
  const phoneNumber = getQueryStringValue('phone');
  if (phoneNumber) {
    // Construct the SMS link
    const smsLink = `sms:${phoneNumber}`;
    // Open the SMS app with the link
    window.location.href = smsLink;
  } else {
    // Handle the error case where the phone number is not provided
    alert('Phone number is missing from the URL parameters.');
  }
}

// Call the sendSMS function when the window is finished loading
window.onload = function() {
  sendSMS();
};
</script>

  <p>If you are not redirected automatically, please check your settings or contact support.</p>
