Google-Maps-API-v2
==================

Extensively uses Google Maps API v2, to track the location of the user.


function initialize() 
{
/*<!DOCTYPE html>
<html>
  <head>
     <link rel="stylesheet" type="text/css" href="14.css"/>
    <script type="text/javascript" src="jquery-2.0.0.js"></script>
    <script type="text/javascript" src="https://maps.googleapis.com/maps/api/js"></script>
    <script type="text/javascript" src="14.js"></script>
  </head>
  </head>
  <body onload="initialize()">
    <div id="map_canvas" style="width:100%; height:100%"></div>
  </body>
</html>



<?php
	extract($_GET);
	if($data == "bms")
		echo "BMS College of Engineering";
	if($data == "pesse")
		echo "The Other PES college";
?>

*/
	//Map centred on PESU. The latitude and Longitude are that of PESU
	var myLatLng = new google.maps.LatLng(12.9342678, 77.53432629999998);
	
	//Specify the map type
    var mapOptions = {
      center: myLatLng,
      zoom: 12,
      mapTypeId: google.maps.MapTypeId.ROADMAP // There are atleast 4 types of maps
    };
	
	// Draw the map. This will be used to add the markers also.
    var map = new google.maps.Map(document.getElementById("map_canvas"),
        mapOptions);
	
	// Can add some markers now
	
	// THE TEXT FOR THE "TITLE" PROPERTY WILL BE FETCHED FROM A 
	// FILE ON THE SERVER, USING AN AJAX CALL.YOU SHOULD NOT 
	// HARD CODE THE TEXT.
	 
	//PESU - Lat and Long - 12.9342678, 77.53432629999998
	var marker = new google.maps.Marker({
		  position: myLatLng,
		  map: map,
		  title:"PES Institute of Technology, this is where I study"
	  });
	  
	  //RVCE's Lat and Long are - 12.9247501 and 77.49875709999992
	  var myLatLng2 = new google.maps.LatLng(12.9247501, 77.49875709999992);
	  
	  // THE TEXT FOR THE "TITLE" PROPERTY WILL BE FETCHED FROM A 
	  // FILE ON THE SERVER, USING AN AJAX CALL. YOU SHOULD NOT 
	  // HARD CODE THE TEXT.
	  var marker = new google.maps.Marker({
		  position: myLatLng2,
		  map: map,
		  title:"RVCE IS PESU's COMPETITOR"
	  });
	  
	  //ADD TWO MORE MARKERS, ONE FOR BMSCE AND ONE FOR PES(South)
	  // For Latitude and Longitude, see the instructions file.
	  $.ajax({
		  	url:'getTitle.php?data=bms',
		  	type:'get',
		  	success:function(data){ 
		  		var myLatLng3 = new google.maps.LatLng(12.9404973, 77.56568749999997);
			  	marker3 = new google.maps.Marker({
				  position: myLatLng3,
				  map: map,
				  title: data  
			  });
		  }
		});
	  
	  $.ajax({
		  	url:'getTitle.php?data=pesse',
		  	type:'get',
		  	success:function(data){ 
		  		var myLatLng = new google.maps.LatLng(12.8614515, 77.66470809999998);
			  	marker3 = new google.maps.Marker({
				  position: myLatLng,
				  map: map,
				  title: data  
			  });
		  }
		});
}
