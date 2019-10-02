# Midia-Indoor
Uma Apresentação de comunicação interna para empresas e escritórios, mas podendo ser usada para mídias externas

<!DOCTYPE html>
<html lang="pt">
<head>
	<link rel="stylesheet" type="text/css" href="css/style.css">
	<link href="https://fonts.googleapis.com/css?family=Open+Sans&display=swap" rel="stylesheet">
	<meta charset="utf-8">
	<meta http-equiv="refresh" content="600">
	<title>Tempo</title>

	<style>

		body{
			background-repeat: no-repeat;
			font-family: 'Comic Sans', sans-serif;
		}

		.img-hg {
			float: left;
			width: 130px;
			margin-left: 10%;
		}

		table, td {
			z-index: auto;
			margin-top: 1%;
			margin-left: 15%;
			background-color: rgba( 0, 0, 0, .2 );
			width: 71.5%;
			height: auto;
			overflow-x: auto;
		}

		.slider {
			margin-left: 7%;

		}

		.logo {
			margin-left: 10%;
		}

		h1 {
			margin-top: 10%;
			margin-left: 10%;
			font-size: 200%;
			color: white;
			line-height: 0.50em;
		}

	</style>

		<header>
		<div class="slider">
		  <img class="foto" src="img.png" width="1120" height="530">
		  <img class="foto" src="img.png"width="1120" height="530">  
		  <img class="foto " src="img.png"width="1120" height="530">
		  <img class="foto " src="img.png"width="1120" height="530">
		  <img class="foto " src="img.png"width="1120" height="530">
		</div>
	</header>

</head>
<body>


	<?php


		$json = file_get_contents('https://api.hgbrasil.com/weather?key=99999999&city_name=Criciuma,SC'); 

		$json_data = json_decode($json, true );  
	?>

	<table id="previsao" cellpadding="12" >
		<td>
			<img class="logo" src="logo.png" width="480"></td>
		</td>
		<td>
			<h1><?php echo $json_data['results']['date']; ?></h1>	
			<h1><?php echo $json_data['results']['time'];?></h1>		
		</td>
		<td>
  			<img src="imagens/<?php echo $json_data['results']['img_id']; ?>.png" class="img-hg"><br>
			<h1><?php echo $json_data['results']['temp']; ?>°C</h1>
		</td>		
	</table>
	
	<script>
		var myIndex = 0;
		carousel();

		function carousel() {
		  var i;
		  var x = document.getElementsByClassName("foto");
		  for (i = 0; i < x.length; i++) {
		    x[i].style.display = "none";  
		  }
		  myIndex++;
		  if (myIndex > x.length) {myIndex = 1}    
		  x[myIndex-1].style.display = "block";  
		  setTimeout(carousel, 2000); // Change image every 2 seconds
		}
	</script>
	
	
</body>
</html>
