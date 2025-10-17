# Blind Map Quiz - HTML Project

## ✅ Purpose

Create a geography quiz using a **blank map** where students:
- Are given a place name (e.g. "Paris")
- Click on the map to guess where it is
- Get feedback on distance from the correct location
- Do **not** see any map labels (no city or country names)

---

## 🧱 Tech Stack

- HTML + JS
- [Leaflet.js](https://leafletjs.com/) for mapping
- Minimal/no external dependencies

---

## 🔧 Setup

1. Create an `index.html` file
2. Paste the following code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Blind Map Quiz</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <link
    rel="stylesheet"
    href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
  />
  <style>
    html, body { margin: 0; height: 100%; }
    #map { height: 100vh; }
    .info-box {
      position: absolute;
      top: 10px;
      left: 10px;
      background: white;
      padding: 8px 12px;
      z-index: 1000;
      border: 1px solid #ccc;
      font-family: sans-serif;
    }
  </style>
</head>
<body>
  <div id="map"></div>
  <div class="info-box" id="info">Guess the location: <strong>Paris</strong></div>

  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

  <script>
    // ========== SETUP ==========
    const map = L.map('map').setView([20, 0], 2);

    // Use NO LABELS tile layer
    L.tileLayer('https://cartodb-basemaps-a.global.ssl.fastly.net/light_nolabels/{z}/{x}/{y}.png', {
      attribution: '',
    }).addTo(map);

    const correctLocation = {
      name: "Paris",
      lat: 48.8566,
      lng: 2.3522
    };

    let hasGuessed = false;

    // ========== CLICK HANDLER ==========
    map.on('click', function(e) {
      if (hasGuessed) return;

      const userLat = e.latlng.lat;
      const userLng = e.latlng.lng;

      const distance = getDistanceFromLatLonInKm(userLat, userLng, correctLocation.lat, correctLocation.lng);

      // Add user marker
      L.marker([userLat, userLng], { title: "Your Guess" }).addTo(map);

      // Add correct marker
      L.marker([correctLocation.lat, correctLocation.lng], {
        title: "Correct Location",
        icon: L.icon({
          iconUrl: 'https://cdn-icons-png.flaticon.com/512/684/684908.png',
          iconSize: [30, 30],
          iconAnchor: [15, 30]
        })
      }).addTo(map);

      // Draw line between guess and correct
      L.polyline([
        [userLat, userLng],
        [correctLocation.lat, correctLocation.lng]
      ], { color: 'red' }).addTo(map);

      // Feedback
      const infoBox = document.getElementById('info');
      infoBox.innerHTML = `You guessed ${distance.toFixed(1)} km from the correct location.`;

      hasGuessed = true;
    });

    // ========== DISTANCE FUNCTION ==========
    function getDistanceFromLatLonInKm(lat1, lon1, lat2, lon2) {
      const R = 6371; // Radius of Earth in km
      const dLat = deg2rad(lat2 - lat1);
      const dLon = deg2rad(lon2 - lon1);
      const a =
        Math.sin(dLat / 2) * Math.sin(dLat / 2) +
        Math.cos(deg2rad(lat1)) * Math.cos(deg2rad(lat2)) *
        Math.sin(dLon / 2) * Math.sin(dLon / 2);
      const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
      return R * c;
    }

    function deg2rad(deg) {
      return deg * (Math.PI / 180);
    }
  </script>
</body>
</html>

