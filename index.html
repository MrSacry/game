<!DOCTYPE html>
<html>

<head>
    <meta charset=utf-8 />
    <title>Hot and Cold — Find the Hidden Location</title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />

    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.4.0/dist/leaflet.css" />
    <script src="https://unpkg.com/leaflet@1.4.0/dist/leaflet.js"></script>
    <link href='https://fonts.googleapis.com/css?family=Lato:400,700' rel='stylesheet' type='text/css'>

    <style>
        *, *::before, *::after { box-sizing: border-box; }

        body {
            margin: 0;
            padding: 0;
            background: #1a1a2e;
            font-family: Lato, sans-serif;
            color: #e0e0e0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        header {
            padding: 12px 5%;
            background: linear-gradient(135deg, #16213e, #0f3460);
            display: flex;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.4);
        }

        header h1 {
            margin: 0 16px 0 0;
            font-size: 1.8em;
            color: #e94560;
            text-shadow: 0 0 10px rgba(233,69,96,0.5);
            flex-shrink: 0;
        }

        /* ── Controls ── */
        #controls {
            display: flex;
            align-items: center;
            gap: 8px;
            flex-wrap: wrap;
        }

        button {
            padding: 8px 16px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-family: Lato, sans-serif;
            font-size: 0.9em;
            font-weight: 700;
            transition: transform 0.1s, box-shadow 0.1s, background 0.2s;
        }
        button:hover { transform: translateY(-1px); box-shadow: 0 4px 10px rgba(0,0,0,0.3); }
        button:active { transform: translateY(0); }

        #resetBtn {
            background: #e94560;
            color: #fff;
        }
        #resetBtn:hover { background: #c73652; }

        #toggleInstructions {
            background: #0f3460;
            color: #a0c4ff;
            border: 1px solid #a0c4ff44;
        }
        #toggleInstructions:hover { background: #16458a; }

        /* ── Stats panel ── */
        #stats {
            margin: 0 5%;
            padding: 10px 16px;
            background: #16213e;
            border-left: 4px solid #e94560;
            border-radius: 0 6px 6px 0;
            display: flex;
            align-items: center;
            gap: 20px;
            flex-wrap: wrap;
            font-size: 0.95em;
        }
        .stat-item { display: flex; align-items: center; gap: 6px; }
        .stat-label { color: #888; }
        .stat-value { font-weight: 700; color: #e0e0e0; font-size: 1.05em; }

        /* ── Temperature / progress bar ── */
        #temp-bar-wrap {
            flex: 1 1 180px;
            min-width: 120px;
        }
        #temp-label {
            font-size: 0.8em;
            color: #888;
            margin-bottom: 3px;
        }
        #temp-bar-bg {
            height: 10px;
            border-radius: 5px;
            background: linear-gradient(to right, #4a90e2, #f5a623, #e94560);
            position: relative;
            overflow: visible;
        }
        #temp-cursor {
            position: absolute;
            top: -3px;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background: #fff;
            border: 2px solid #333;
            transform: translateX(-50%);
            transition: left 0.4s ease;
            left: 0%;
        }

        /* ── Instructions panel ── */
        #instructions {
            margin: 0 5%;
            padding: 12px 16px;
            background: #0f3460;
            border-radius: 6px;
            font-size: 0.9em;
            line-height: 1.6;
            color: #c8d8e8;
            display: none;
        }
        #instructions.open { display: block; }
        #instructions strong { color: #a0c4ff; }

        /* ── Map ── */
        #map {
            flex: 1;
            min-height: 460px;
            margin: 10px 5%;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 20px rgba(0,0,0,0.5);
            transition: background 0.6s;
        }

        /* ── Win overlay ── */
        #win-overlay {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.65);
            z-index: 9999;
            align-items: center;
            justify-content: center;
        }
        #win-overlay.show { display: flex; }
        #win-box {
            background: #16213e;
            border: 2px solid #e94560;
            border-radius: 12px;
            padding: 36px 48px;
            text-align: center;
            max-width: 420px;
            width: 90%;
            box-shadow: 0 8px 32px rgba(0,0,0,0.6);
        }
        #win-box h2 { color: #e94560; font-size: 2em; margin: 0 0 12px; }
        #win-box p  { color: #c8d8e8; font-size: 1.05em; margin: 6px 0; }
        #win-box button { margin-top: 20px; padding: 12px 28px; font-size: 1em; background: #e94560; color: #fff; border-radius: 8px; }

        /* ── Footer ── */
        footer {
            padding: 10px 5%;
            font-size: 0.8em;
            color: #555;
            text-align: center;
        }

        /* ── Mobile ── */
        @media (max-width: 600px) {
            header h1 { font-size: 1.3em; }
            #stats { gap: 12px; font-size: 0.85em; }
            #map { margin: 8px 2%; min-height: 360px; }
        }
    </style>
</head>

<body>
    <header>
        <h1>🌡️ Hot and Cold</h1>
        <div id="controls">
            <button id="resetBtn">🔄 Reset Game</button>
            <button id="toggleInstructions">📖 Instructions</button>
        </div>
    </header>

    <div id="stats">
        <div class="stat-item">
            <span class="stat-label">Clicks:</span>
            <span class="stat-value" id="clickCount">0</span>
        </div>
        <div class="stat-item">
            <span class="stat-label">Last distance:</span>
            <span class="stat-value" id="distDisplay">—</span>
        </div>
        <div class="stat-item" id="temp-bar-wrap">
            <div>
                <div id="temp-label">Temperature</div>
                <div id="temp-bar-bg"><div id="temp-cursor"></div></div>
            </div>
        </div>
    </div>

    <div id="instructions">
        <strong>How to play:</strong> A secret location is hidden somewhere on the map.
        Click anywhere to drop a marker — the popup will tell you how <em>hot</em> or <em>cold</em>
        you are based on your distance from the target. 🔵 Blue markers mean you're far away (cold);
        🔴 red markers mean you're close (hot). The game auto-zooms as you get warmer.
        Find the hidden location in as few clicks as possible!
    </div>

    <div id="map"></div>

    <div id="win-overlay">
        <div id="win-box">
            <h2>🎉 You Found It!</h2>
            <p>You've arrived at the <strong>Henry Doorly Zoo and Aquarium</strong>!</p>
            <p id="win-clicks"></p>
            <button id="winResetBtn">Play Again</button>
        </div>
    </div>

    <footer>
        <p>Map authored by x &nbsp;|&nbsp; Click the map to search for the hidden location.</p>
    </footer>

    <script>
        /* ── Constants ── */
        var TARGET = L.latLng(41.224727, -95.928568);
        var WIN_RADIUS_MILES  = 10;
        var MAX_DISTANCE_MILES = 12500;
        var INITIAL_CENTER = [20, 0];
        var INITIAL_ZOOM   = 2;

        /* ── State ── */
        var clickCount = 0;
        var gameWon    = false;

        /* ── Map setup ── */
        var map = L.map('map', { center: INITIAL_CENTER, zoom: INITIAL_ZOOM });

        L.tileLayer('https://{s}.basemaps.cartocdn.com/dark_all/{z}/{x}/{y}{r}.png', {
            attribution: '©OpenStreetMap, ©CartoDB',
            subdomains: 'abcd',
            maxZoom: 19
        }).addTo(map);

        var markers = L.layerGroup().addTo(map);
        var winMarker = null;

        /* ── Utility: distance in miles ── */
        function calcDistance(a, b) {
            return a.distanceTo(b) / 1609.34;
        }

        /* ── Utility: interpolate colour blue→orange→red based on 0–1 heat ── */
        function heatColor(t) {
            // t = 0 → cold (blue), t = 1 → hot (red)
            var r, g, b;
            if (t < 0.5) {
                var u = t * 2;
                r = Math.round(74  + (245 - 74)  * u);
                g = Math.round(144 + (166 - 144) * u);
                b = Math.round(226 + (35  - 226) * u);
            } else {
                var u = (t - 0.5) * 2;
                r = Math.round(245 + (233 - 245) * u);
                g = Math.round(166 + (69  - 166) * u);
                b = Math.round(35  + (96  - 35)  * u);
            }
            return 'rgb(' + r + ',' + g + ',' + b + ')';
        }

        /* ── Utility: heat value 0–1 from miles ── */
        function heatFactor(miles) {
            return Math.max(0, Math.min(1, 1 - miles / MAX_DISTANCE_MILES));
        }

        /* ── Custom circular marker ── */
        function makeMarkerIcon(miles) {
            var t   = heatFactor(miles);
            var col = heatColor(t);
            var opacity = 0.5 + t * 0.5;
            var size = 14 + Math.round(t * 10);

            var svg = '<svg xmlns="http://www.w3.org/2000/svg" width="' + size + '" height="' + size + '">'
                    + '<circle cx="' + (size/2) + '" cy="' + (size/2) + '" r="' + (size/2 - 1) + '" '
                    + 'fill="' + col + '" fill-opacity="' + opacity + '" stroke="#fff" stroke-width="1.5"/>'
                    + '</svg>';

            return L.divIcon({
                className: '',
                html: svg,
                iconSize:   [size, size],
                iconAnchor: [size/2, size/2],
                popupAnchor:[0, -size/2]
            });
        }

        /* ── Update stats panel ── */
        function updateStats(miles) {
            document.getElementById('clickCount').textContent = clickCount;
            document.getElementById('distDisplay').textContent =
                miles !== null ? Math.round(miles).toLocaleString() + ' mi' : '—';
            if (miles !== null) {
                var t = heatFactor(miles);
                document.getElementById('temp-cursor').style.left = (t * 100) + '%';
            }
        }

        /* ── Popup message with emoji ── */
        function popupMessage(miles) {
            if (miles > 8000)  return '🥶 Freezing cold!';
            if (miles > 5000)  return '❄️ Very cold…';
            if (miles > 1000)  return '🌬️ Still cold, but getting warmer';
            if (miles > 500)   return '🌤️ Getting warmer!';
            if (miles > 100)   return '🔆 Much warmer — keep going!';
            if (miles > 50)    return '🔥 Very warm!';
            return '🌋 Scorching hot — almost there!';
        }

        /* ── Auto-zoom thresholds ── */
        function autoZoom(miles) {
            if      (miles < 50)   map.flyTo(TARGET, Math.max(map.getZoom(), 10), {duration:1});
            else if (miles < 200)  map.flyTo(TARGET, Math.max(map.getZoom(), 7),  {duration:1});
            else if (miles < 500)  map.flyTo(TARGET, Math.max(map.getZoom(), 5),  {duration:1});
            else if (miles < 1000) map.flyTo(TARGET, Math.max(map.getZoom(), 4),  {duration:1});
        }

        /* ── Win condition ── */
        function triggerWin() {
            gameWon = true;
            markers.clearLayers();

            winMarker = L.marker(TARGET).addTo(map);
            winMarker.bindPopup(
                "<b>🎉 You found it!</b><br>Henry Doorly Zoo and Aquarium"
            ).openPopup();

            map.flyTo(TARGET, 13, { duration: 1.5 });

            document.getElementById('win-clicks').textContent =
                'You found it in ' + clickCount + ' click' + (clickCount === 1 ? '' : 's') + '!';
            document.getElementById('win-overlay').classList.add('show');
        }

        /* ── Reset game ── */
        function resetGame() {
            clickCount = 0;
            gameWon    = false;

            markers.clearLayers();
            if (winMarker) { winMarker.remove(); winMarker = null; }

            map.setView(INITIAL_CENTER, INITIAL_ZOOM);
            updateStats(null);
            document.getElementById('temp-cursor').style.left = '0%';
            document.getElementById('win-overlay').classList.remove('show');
        }

        /* ── Map click handler ── */
        map.on('click', function(e) {
            if (gameWon) return;

            clickCount++;
            var clickCoord = e.latlng;
            var miles = calcDistance(TARGET, clickCoord);

            markers.clearLayers();

            if (miles < WIN_RADIUS_MILES) {
                updateStats(miles);
                triggerWin();
                return;
            }

            var marker = L.marker(clickCoord, { icon: makeMarkerIcon(miles) });
            marker.addTo(markers);
            marker.bindPopup(
                '<b>' + popupMessage(miles) + '</b><br><small>' +
                Math.round(miles).toLocaleString() + ' miles away</small>'
            ).openPopup();

            updateStats(miles);
            autoZoom(miles);
        });

        /* ── Button listeners ── */
        document.getElementById('resetBtn').addEventListener('click', resetGame);
        document.getElementById('winResetBtn').addEventListener('click', resetGame);

        document.getElementById('toggleInstructions').addEventListener('click', function() {
            var panel = document.getElementById('instructions');
            panel.classList.toggle('open');
            this.textContent = panel.classList.contains('open') ? '📖 Hide Instructions' : '📖 Instructions';
        });

        /* ── Initial stats ── */
        updateStats(null);
    </script>

</body>
</html>
