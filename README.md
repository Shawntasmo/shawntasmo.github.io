# shawntasmo.github.io
<!DOCTYPE html>
<html>
<head>
	<title>Storage Calculator</title>
	<link rel="icon" href="img/favicon.png" type="image/png" sizes="16x16">
	<style>
		body {
			background-color: #f2f2f2;
			font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
		}

		.container {
			margin: 0 auto;
			max-width: 600px;
			padding: 20px;
		}

		.form-group {
			margin-bottom: 20px;
		}

		.form-label {
			display: block;
			font-size: 18px;
			margin-bottom: 5px;
		}

		.form-input {
			display: block;
			font-size: 18px;
			padding: 10px;
			width: 100%;
		}

		.button {
			background-color: green;
			border: none;
			color: #fff;
			cursor: pointer;
			font-size: 24px;
			padding: 10px 20px;
			text-align: center;
			text-decoration: none;
			width: 100%;
		}

		.button:hover {
			background-color: darkgreen;
		}
	</style>
</head>
<body>
	<div class="container">
		<form>
			<div class="form-group">
				<label for="volume" class="form-label">Cargo volume (cubic meters):</label>
				<input type="number" id="volume" name="volume" class="form-input">
			</div>

			<div class="form-group">
				<label for="days" class="form-label">Number of days in storage:</label>
				<input type="number" id="days" name="days" class="form-input">
			</div>

			<button type="submit" class="button">Calculate</button>
		</form>
	</div>

	<script>
		function calculateCharges() {
    var volume = document.getElementById("volume").value;
    var days = document.getElementById("days").value;

    var storageCharges;
    if (days <= 10) {
        storageCharges = volume * days * 20;
    } else if (days <= 20) {
        storageCharges = (volume * 10 * 20) + (volume * (days - 10) * 25);
    } else if (days <= 30) {
        storageCharges = (volume * 10 * 20) + (volume * 10 * 25) + (volume * (days - 20) * 30);
    } else if (days <= 40) {
        storageCharges = (volume * 10 * 20) + (volume * 10 * 25) + (volume * 10 * 30) + (volume * (days - 30) * 35);
    } else if (days <= 50) {
        storageCharges = (volume * 10 * 20) + (volume * 10 * 25) + (volume * 10 * 30) + (volume * 10 * 35) + (volume * (days - 40) * 40);
    } else if (days <= 60) {
        storageCharges = (volume * 10 * 20) + (volume * 10 * 25) + (volume * 10 * 30) + (volume * 10 * 35) + (volume * 10 * 40) + (volume * (days - 50) * 45);
    }

    var penaltyFee = storageCharges * 0.25;
    var removalFee = volume * 35;
    var totalCharges = storageCharges + penaltyFee + removalFee;

    alert("Your storage charges are $" + storageCharges.toFixed(2) +
          "\nPenalty fee: $" + penaltyFee.toFixed(2) +
          "\nRemoval fee: $" + removalFee.toFixed(2) +
          "\nTotal charges: $" + totalCharges.toFixed(2));
}


		document.querySelector("form").addEventListener("submit", function(event) {
			event.preventDefault();
			calculateCharges();
		});
	</script>
</body>
</html>
