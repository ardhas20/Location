<script>
	let latitude = null;
	let longitude = null;
	let accuracy = null;
	let errorMessage = null;

	function getLocation() {
		navigator.geolocation.getCurrentPosition(showPosition, showError);
	}

	function showPosition(position) {
		latitude = position.coords.latitude;
		longitude = position.coords.longitude;
		accuracy = position.coords.accuracy;
		errorMessage = null;
	}

	function showError(error) {
		errorMessage = "Es gibt ein Fehler.";
	}

</script>

<div class="min-h-screen flex items-center justify-center bg-gradient-to-br from-blue-50 to-purple-50">
	<div class="max-w-md w-full bg-white rounded-2xl p-6 shadow-md border">
		<h1 class="text-2xl font-semibold mb-6 text-gray-800 text-center">
			Geolocation
		</h1>

		<div class="flex justify-center">
			<button
				on:click={getLocation}
				class="px-5 py-2 bg-yellow-400 text-gray-900 font-medium rounded-lg shadow-sm hover:bg-yellow-500 transition"
			>
				Standort abrufen
			</button>
		</div>

		{#if errorMessage}
			<p class="mt-4 text-center text-red-600">{errorMessage}</p>
		{/if}

		<ul class="mt-6 space-y-2 text-gray-700">
			<li class="p-2 bg-gray-50 rounded-md"><strong>Breitengrad:</strong> {latitude}</li>
			<li class="p-2 bg-gray-50 rounded-md"><strong>Längengrad:</strong> {longitude}</li>
			<li class="p-2 bg-gray-50 rounded-md"><strong>Genauigkeit (m):</strong> {accuracy}</li>
		</ul>
	</div>
</div>
