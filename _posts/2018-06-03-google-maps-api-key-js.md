---
ID: 1327
post_title: Google maps API key js
author: admin
post_excerpt: ""
layout: post
permalink: >
  https://coding-banana.com/google-maps-api-key-js/
published: true
post_date: 2018-06-03 17:18:46
---
Resources:
<ul>
 	<li>https://developers.google.com/maps/documentation/javascript/tutorial</li>
 	<li>https://developers.google.com/maps/documentation/javascript/examples/map-simple</li>
 	<li>https://stackoverflow.com/questions/7891736/how-to-join-all-markers-with-paths-in-google-maps?utm_medium=organic&amp;utm_source=google_rich_qa&amp;utm_campaign=google_rich_qa</li>
 	<li>https://stackoverflow.com/questions/15773388/how-to-connect-two-points-in-google-map?utm_medium=organic&amp;utm_source=google_rich_qa&amp;utm_campaign=google_rich_qa</li>
</ul>
&nbsp;

&nbsp;

<p> PRE-MAP TEXT </p>

<div id="map" style="height: 100%;"></div>
<script>
  var map;
  function initMap() {
    map = new google.maps.Map(document.getElementById('map'), {
      center: {lat: -34.397, lng: 150.644},
      zoom: 8
    });
  }
</script>
<script src="https://maps.googleapis.com/maps/api/js?key=AIzaSyD4Igr90SBMkV97afx6mHosO7vxoGu62CA&callback=initMap" async defer></script>

<p> POST-MAP TEXT </p>