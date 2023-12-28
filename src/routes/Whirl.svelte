<script lang="ts">
	let riveInstance = false;
	console.log(riveInstance);
</script>

<div id="tunnel_container">
	<div id="circle"></div>
	<div id="circle_2"></div>
	<div id="circle_3"></div>
	<div id="circle_4"></div>
</div>

<style>
	[id^='circle'] {
		border-radius: 50%;
		position: absolute;
		-webkit-animation-name: rotate;
		-webkit-animation-iteration-count: infinite;
		-webkit-animation-timing-function: linear;
		-moz-animation-name: rotate;
		-moz-animation-iteration-count: infinite;
		-moz-animation-timing-function: linear;
	}

	#circle {
		height: 50px;
		width: 50px;
		-webkit-animation-duration: 1s;
		-moz-animation-duration: 1s;
		top: 50px;
		left: 50px;
		position: absolute;
		left: 50%;
		margin-left: -25px;
		top: 50%;
		margin-top: -25px;
		background: -webkit-linear-gradient(white, rgba(255, 255, 255, 0));
	}
	#circle:after {
		content: '';
		display: block;
		background-color: black;
		width: 46px;
		height: 46px;
		position: absolute;
		border-radius: 50%;
		z-index: 2;
		left: 50%;
		margin-left: -23px;
		top: 50%;
		margin-top: -23px;
	}

	#circle_2 {
		height: 40px;
		width: 40px;
		-webkit-animation-duration: 1.1s;
		-moz-animation-duration: 1.1s;
		display: block;
		background-color: black;
		position: absolute;
		border-radius: 50%;
		z-index: 2;
		left: 50%;
		margin-left: -20px;
		top: 50%;
		margin-top: -20px;
		background: -webkit-linear-gradient(white, rgba(255, 255, 255, 0));
		z-index: 5;
	}
	#circle_2:after {
		content: '';
		display: block;
		background-color: black;
		width: 36px;
		height: 36px;
		position: absolute;
		border-radius: 50%;
		z-index: 10;
		left: 50%;
		margin-left: -18px;
		top: 50%;
		margin-top: -18px;
	}

	#circle_3 {
		height: 30px;
		width: 30px;
		-webkit-animation-duration: 1.2s;
		-moz-animation-duration: 1.2s;
		display: block;
		background-color: black;
		position: absolute;
		border-radius: 50%;
		z-index: 2;
		left: 50%;
		margin-left: -15px;
		top: 50%;
		margin-top: -15px;
		background: -webkit-linear-gradient(white, rgba(255, 255, 255, 0));
		z-index: 5;
	}
	#circle_3:after {
		content: '';
		display: block;
		background-color: black;
		width: 26px;
		height: 26px;
		position: absolute;
		border-radius: 50%;
		z-index: 10;
		left: 50%;
		margin-left: -13px;
		top: 50%;
		margin-top: -13px;
	}

	#circle_4 {
		height: 20px;
		width: 20px;
		-webkit-animation-duration: 1.3s;
		-moz-animation-duration: 1.3s;
		display: block;
		background-color: black;
		position: absolute;
		border-radius: 50%;
		z-index: 2;
		left: 50%;
		margin-left: -10px;
		top: 50%;
		margin-top: -10px;
		background: -webkit-linear-gradient(white, rgba(255, 255, 255, 0));
		z-index: 5;
	}
	#circle_4:after {
		content: '';
		display: block;
		background-color: black;
		width: 16px;
		height: 16px;
		position: absolute;
		border-radius: 50%;
		z-index: 10;
		left: 50%;
		margin-left: -8px;
		top: 50%;
		margin-top: -8px;
	}

	@keyframes rotate {
		from {
			-webkit-transform: rotate(360deg);
		}
		to {
			-webkit-transform: rotate(0deg);
		}
	}
</style>
