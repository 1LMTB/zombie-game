<!DOCTYPE html>
<html>
  <head>
    <style>
      #zombie_map {
        height: 100%;
        width: 100%;
        left: 0;
        position: absolute;
        top: 0;
        background-color: grey;
    }
    </style>
    <title>My page title</title>
  </head>
  <body>
    My zombie map
    <div id="zombie_map"></div>
    <script>
    var zombie_map;
    var all_markers = [];
    var data = `51.747873085471 -1.2377909212956073 zombie.png
51.561925511616266 -0.6101928993806083 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.57344942859936 -0.600236539517327 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.60011395680961 -0.6462417885407645 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.619729053044495 -0.6022964760407645 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.60992256436143 -0.557664518032952 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.576223268679215 -0.549424771939202 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.56000457479747 -0.5501114174470145 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.545915225345055 -0.5816971108063895 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.53523857033819 -0.662034635220452 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.53011288620284 -0.6888138100251395 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.51815071201619 -0.7300125404938895 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.50789491861576 -0.5885635658845145 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.78908589772251 -0.8000482770882522 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.89938059101268 -0.2562250349007522 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.732986672217216 -0.3276361677132522 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.66659769881043 -1.2752069684945022 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.58987396636643 -1.2395014020882522 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.58134109653888 -1.3933099958382522 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.64615072347094 -1.5690912458382522 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
52.24546499805558 0.1502691057242478 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.768694243997615 0.5292974260367478 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.92140710832396 1.0072026994742478 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.57109953737801 0.8533941057242478 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
51.812864514085355 1.1774907854117478 https://github.com/1LMTB/zombie-game/blob/master/zombie.png
24.33307067002869 20.582801447934322 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
27.650433630914154 3.3562389479343224 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
25.766244222046872 28.141395197934322 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
25.449214810445856 42.73123894793432 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
47.13442608526407 31.305457697934322 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
51.155912263935086 10.914832697934322 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
51.81268191293596 17.946082697934322 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
39.61075630091039 -1.2140735520656776 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
44.8137885950212 3.3562389479343224 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
52.352781421727634 -8.421104802065678 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
59.33654452611372 9.332801447934322 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
65.35426052194813 18.649207697934322 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
62.08976551788834 26.910926447934322 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
63.456543217509655 53.27616643675212 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
50.44743596527094 68.04179143675212 https://github.com/1LMTB/zombie-game/blob/master/weapons.png
66.45883085499152 92.01624068669183 https://github.com/1LMTB/zombie-game/blob/master/hospital.png
58.2839833133433 60.55139693669183 https://github.com/1LMTB/zombie-game/blob/master/hospital.png
60.70549004384929 108.2329975157471 https://github.com/1LMTB/zombie-game/blob/master/hospital.png
69.43444036787606 136.5337787657471 https://github.com/1LMTB/zombie-game/blob/master/hospital.png
70.28173322637815 111.7486225157471 https://github.com/1LMTB/zombie-game/blob/master/hospital.png
60.61509747476252 77.51307896218903 https://github.com/1LMTB/zombie-game/blob/master/hospital.png
65.46380924308578 67.49354771218904 https://github.com/1LMTB/zombie-game/blob/master/hospital.png
-21.178341599163375 -54.14155385398133 https://github.com/1LMTB/zombie-game/blob/master/hospital.png
45.66659645389221 -92.11030385398132 https://github.com/1LMTB/zombie-game/blob/master/hospital.png
-1.9898550406154187 27.420946146018668 https://github.com/1LMTB/zombie-game/blob/master/hospital.png
-35.93494122816598 134.29594614601868 https://github.com/1LMTB/zombie-game/blob/master/hospital.png
78.79097096179447 -42.89155385398133 https://github.com/1LMTB/zombie-game/blob/master/hospital.png`;
    var markers = data.split("\n");
    function initMap() {
      zombie_map = new google.maps.Map(document.getElementById('zombie_map'), {
      zoom: 10,
      center: {lat: 51.726937, lng: -0.683729}
        });
        for(var i=0; i < markers.length; i++){
        var marker_data = markers[i].trim();
        marker_data = marker_data.split(" ");
        var latitude = marker_data[0];
        var longitude = marker_data[1];
        var emoji = marker_data[2];
        var marker_position = new google.maps.LatLng(latitude, longitude);
        var marker = new google.maps.Marker({
        position: marker_position,
        map: zombie_map,
        icon: emoji
        });
        all_markers.push(marker);
        }
        if(navigator.geolocation) {
    navigator.geolocation.watchPosition(set_my_position);
}
else {
    alert("Geolocation doesn't work in your browser");
}
        }
  function set_my_position(position){
    var pos = new google.maps.LatLng(position.coords.latitude, position.coords.latitude);
    var marker = new google.maps.Marker({
        position: pos,
        map: zombie_map,
        icon: 'player.png'
        });
    }
</script>
    <script async defer
      src="https://maps.googleapis.com/maps/api/js?key=AIzaSyCTQg0Oz070jw0dEPspC5QTTZIgCm2QmF8&callback=initMap">
    </script>
  </body>
</html>
