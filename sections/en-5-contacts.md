---
title: en - 5 - Contacts
language: en
order: 5
---
<script>
var map;
var options = {
  placeId: "ChIJ68TmaaTCe0gRy70pZDzQ17U",
  latitude: 53.7153659,
  longitude: -1.8790866,
  title: "Dickies Tiles",
  address: "Aachen Way, Halifax HX1 3ND, United Kingdom"
}

function initialize() {
  var map = new google.maps.Map(document.getElementById("map_canvas"), {
    zoom: 15,
    center: {
      lat: options.latitude,
      lng: options.longitude
    }
  });

  var marker = new MarkerWithLabel({
    position: new google.maps.LatLng(options.latitude, options.longitude),
    map: map,
    title: options.title,
    labelContent: options.title,
    labelAnchor: new google.maps.Point(-13, 15),
    labelClass: "map-label",
    labelStyle: {
      border: 'none',
      textAlign: 'center',
      fontSize: '12px',
      width: 'auto',
      color: '#800000'
    }
  });

  marker.setPlace({
    placeId: options.placeId,
    location: {
      lat: options.latitude,
      lng: options.longitude
    }
  });

  var infowindow = new google.maps.InfoWindow({
    content: '<strong>' + options.title + '</strong><br />' + options.address
  });

  google.maps.event.addListener(marker, 'click', function() {
    infowindow.open(map, marker);
  });
}
google.maps.event.addDomListener(window, "load", initialize);
</script>