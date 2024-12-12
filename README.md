<!DOCTYPE html>
<html>
<head>
  <title>Share Your Location</title>
</head>
<body>
  <h2>Click the button below to share your location:</h2>
  <button onclick="getLocation()">Share Location</button>
  <p id="status"></p>
  <script>
    function getLocation() {
      const status = document.getElementById('status');
      if (navigator.geolocation) {
        status.textContent = "Getting location...";
        navigator.geolocation.getCurrentPosition(
          (position) => {
            const latitude = position.coords.latitude;
            const longitude = position.coords.longitude;
            const link = `https://www.google.com/maps?q=${latitude},${longitude}`;
            status.innerHTML = `Your location: <a href="${link}" target="_blank">${link}</a>`;
            console.log(`Latitude: ${latitude}, Longitude: ${longitude}`);
          },
          (error) => {
            status.textContent = "Unable to retrieve location. Make sure location services are enabled.";
          }
        );
      } else {
        status.textContent = "Geolocation is not supported by your browser.";
      }
    }
  </script>
</body>
</html>
