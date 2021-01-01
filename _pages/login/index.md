---
permalink: /login/
title: "Login to owenboffey.com! 🔒"
excerpt: "Login to owenboffey.com"
author_profile: false
redirect_from: 
  - /private
---

Enter your password to continue.

<html xmlns="http://www.w3.org/1999/xhtml">
<head>

<meta name="viewport" content="width=device-width, initial-scale=1.0">

</head>

<style>

body {

	background-image: url('https://cdn.joecollyer.com/image/fejka.png');
	background-attachment: fixed;
	color: #333;
}

.box {
	border-radius: 3px;
	background: rgba(101, 101, 101, 0.7); margin: auto; padding: 12px;
}

.lightbox {
	zoom: 1.5;
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background: rgba(10, 10, 10, 0.8);
	text-align: center;
	margin: auto;

}

div.horizontal {
	display: flex;
	justify-content: center;
	height: 100%;
}

div.vertical {
	display: flex;
	flex-direction: column;
	justify-content: center;
	width: 100%;
}

::-webkit-input-placeholder {
   color: #955;
   text-align: center;
}

::-moz-placeholder {
   color: #955;
   text-align: center;
}

:-ms-input-placeholder {
   color: #955;
   text-align: center;
}

.lbutton {
  background-color: white;
  border: 1px solid black;
  color: black;
  padding: 3px 6px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  border-radius: 3px;
}

.lbutton:hover {
  background-color: #e5e5e5;
  color: black;

</style>

<body>

	<div id="loginbox" class="" >
		<div class="horizontal">
			<div class="vertical">
				<div class="">
					<p></p>
					<input style="text-align: left;" id="password" type="password" placeholder="Password" /> <br />
          <p></p>
					<button class="lbutton" id="loginbutton" type="button">Login</button>
					<p id="wrongPassword" style="display: none">Incorrect Password</p>
				</div>
			</div>
		</div>
	</div>



	<script type="text/javascript" src="https://code.jquery.com/jquery-1.12.0.min.js"></script>


	 <script type="text/javascript" src="https://rawcdn.githack.com/chrisveness/crypto/7067ee62f18c76dd4a9d372a00e647205460b62b/sha1.js"></script>

	<script type="text/javascript">
	"use strict";


	function loadPage(pwd) {

		var hash= pwd;
		hash= Sha1.hash(pwd);
		var url= hash;

		$.ajax({
			url : url,
			dataType : "html",
			success : function(data) {

				window.location= url;

			},
			error : function(xhr, ajaxOptions, thrownError) {


				parent.location.hash= hash;

				//$("#wrongPassword").show();
				$("#password").attr("placeholder","Incorrect Password");
				$("#password").val("");
			}
		});
	}


	$("#loginbutton").on("click", function() {
		loadPage($("#password").val());
	});
	$("#password").keypress(function(e) {
		if (e.which == 13) {

			loadPage($("#password").val());
		}
	});
	$("#password").focus();

	</script>

</body>
</html>
