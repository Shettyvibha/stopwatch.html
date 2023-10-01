<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta http-equiv="X-UA-Compatible"
		content="IE=edge">
	<meta name="viewport"
		content="width=device-width, initial-scale=1.0">
	<title>Design Stopwatch using HTML CSS and JavaScript</title>
<style>
    body {
	padding: 0;
	margin: 0;
	font-family: verdana;
}

.container {
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	width: 100%;
	height: 100vh;
	background-color: rgb(0, 61, 0);
}

h1 {
	color: rgb(10, 238, 10);
	text-align: center;
}

.digit {
	font-size: 150px;
	color: #fff;
}

.txt {
	font-size: 30px;
	color: #fffcd6;
}

#buttons {
	margin-top: 50px;
}

.btn {
	width: 100px;
	padding: 10px 15px;
	margin: 0px 20px;
	border-top-right-radius: 10px;
	border-bottom-left-radius: 10px;
	border-bottom-right-radius: 4px;
	border-top-left-radius: 4px;
	cursor: pointer;
	font-size: 20px;
	transition: 0.5s;
	color: white;
	font-weight: 500;
}

#start {
	background-color: #009779;
}

#stop {
	background-color: #0e85fc;
}

#reset {
	background-color: #c91400;
}

</style>
</head>

<body>
	<div class="container">
		<h1>Stop Watch</h1>
		<div id="time">
			<span class="digit" id="hr">
				00</span>
			<span class="txt">Hr</span>
			<span class="digit" id="min">
				00</span>
			<span class="txt">Min</span>
			<span class="digit" id="sec">
				00</span>
			<span class="txt">Sec</span>
			<span class="digit" id="count">
				00</span>
		</div>
		<div id="buttons">
			<button class="btn" id="start">
				Start</button>
			<button class="btn" id="stop">
				Stop</button>
			<button class="btn" id="reset">
				Reset</button>
		</div>
	</div>

	<script src="script.js"></script>
</body>
<script>
    let startBtn = document.getElementById('start');
let stopBtn = document.getElementById('stop');
let resetBtn = document.getElementById('reset');

let hour = 00;
let minute = 00;
let second = 00;
let count = 00;

startBtn.addEventListener('click', function () {
	timer = true;
	stopWatch();
});

stopBtn.addEventListener('click', function () {
	timer = false;
});

resetBtn.addEventListener('click', function () {
	timer = false;
	hour = 0;
	minute = 0;
	second = 0;
	count = 0;
	document.getElementById('hr').innerHTML = "00";
	document.getElementById('min').innerHTML = "00";
	document.getElementById('sec').innerHTML = "00";
	document.getElementById('count').innerHTML = "00";
});

function stopWatch() {
	if (timer) {
		count++;

		if (count == 100) {
			second++;
			count = 0;
		}

		if (second == 60) {
			minute++;
			second = 0;
		}

		if (minute == 60) {
			hour++;
			minute = 0;
			second = 0;
		}

		let hrString = hour;
		let minString = minute;
		let secString = second;
		let countString = count;

		if (hour < 10) {
			hrString = "0" + hrString;
		}

		if (minute < 10) {
			minString = "0" + minString;
		}

		if (second < 10) {
			secString = "0" + secString;
		}

		if (count < 10) {
			countString = "0" + countString;
		}

		document.getElementById('hr').innerHTML = hrString;
		document.getElementById('min').innerHTML = minString;
		document.getElementById('sec').innerHTML = secString;
		document.getElementById('count').innerHTML = countString;
		setTimeout(stopWatch, 10);
	}
}

</script>
</html>
