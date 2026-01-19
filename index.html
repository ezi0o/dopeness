<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <title>Dopeness Player</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        body { background-color: #121212; color: white; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; }
        .spotify-green { color: #1DB954; }
        .bg-spotify-green { background-color: #1DB954; }
        .track-card:active { background-color: #282828; }
        .glass { background: rgba(18, 18, 18, 0.8); backdrop-filter: blur(10px); }
        /* Hide scrollbar */
        ::-webkit-scrollbar { display: none; }
    </style>
</head>
<body class="pb-32">

    <header class="p-6 sticky top-0 glass z-10">
        <h1 class="text-2xl font-bold">Dopeness Selecta</h1>
        <p class="text-gray-400 text-sm" id="status">Loading library...</p>
    </header>

    <main id="track-list" class="px-4 space-y-1">
        </main>

    <footer class="fixed bottom-0 left-0 right-0 glass border-t border-gray-800 p-4 pb-8 z-20">
        <div class="flex flex-col items-center">
            <div class="w-full mb-2">
                <div class="text-sm font-semibold truncate text-center" id="current-title">No track selected</div>
                <div class="text-xs text-gray-400 text-center mb-2">dopenessselecta.free.fr</div>
                <div class="w-full bg-gray-600 h-1 rounded-full overflow-hidden">
                    <div id="progress-bar" class="bg-white h-full w-0"></div>
                </div>
            </div>
            
            <div class="flex items-center space-x-8 mt-2">
                <button onclick="prevTrack()" class="text-xl"><i class="fas fa-step-backward"></i></button>
                <button onclick="togglePlay()" class="text-4xl" id="play-btn"><i class="fas fa-play-circle"></i></button>
                <button onclick="nextTrack()" class="text-xl"><i class="fas fa-step-forward"></i></button>
            </div>
        </div>
    </footer>

    <audio id="audio-player"></audio>

    <script>
        const SOURCE_URL = 'http://dopenessselecta.free.fr/';
        const PROXY_URL = 'https://api.allorigins.win/get?url='; // To bypass CORS
        const trackListElement = document.getElementById('track-list');
        const audioPlayer = document.getElementById('audio-player');
        const playBtn = document.getElementById('play-btn');
        const currentTitle = document.getElementById('current-title');
        const progressBar = document.getElementById('progress-bar');
        const statusText = document.getElementById('status');

        let tracks = [];
        let currentIndex = -1;

        // 1. Fetch and Scrape MP3s
        async function loadTracks() {
            try {
                const response = await fetch(`${PROXY_URL}${encodeURIComponent(SOURCE_URL)}`);
                const data = await response.json();
                const parser = new DOMParser();
                const doc = parser.parseFromString(data.contents, 'text/html');
                const links = Array.from(doc.querySelectorAll('a'));

                tracks = links
                    .map(a => a.getAttribute('href'))
                    .filter(href => href && href.toLowerCase().endsWith('.mp3'))
                    .map(href => ({
                        name: decodeURIComponent(href).replace(/_/g, ' ').replace('.mp3', ''),
                        url: href.startsWith('http') ? href : SOURCE_URL + href
                    }));

                if (tracks.length === 0) {
                    statusText.innerText = "No tracks found.";
                    return;
                }

                renderTracks();
                statusText.innerText = `${tracks.length} tracks found`;
            } catch (error) {
                console.error(error);
                statusText.innerText = "Error loading library.";
            }
        }

        // 2. Render UI
        function renderTracks() {
            trackListElement.innerHTML = tracks.map((track, index) => `
                <div onclick="playTrack(${index})" class="track-card flex items-center p-3 rounded-lg cursor-pointer">
                    <div class="bg-gray-800 w-12 h-12 rounded flex items-center justify-center mr-4">
                        <i class="fas fa-music text-gray-500"></i>
                    </div>
                    <div class="flex-1 overflow-hidden">
                        <div class="text-sm font-medium truncate ${currentIndex === index ? 'text-spotify-green' : 'text-white'}">${track.name}</div>
                        <div class="text-xs text-gray-500 uppercase tracking-widest">MP3</div>
                    </div>
                </div>
            `).join('');
        }

        // 3. Audio Logic
        function playTrack(index) {
            if (index < 0 || index >= tracks.length) return;
            
            currentIndex = index;
            const track = tracks[currentIndex];
            audioPlayer.src = track.url;
            audioPlayer.play();
            
            currentTitle.innerText = track.name;
            playBtn.innerHTML = '<i class="fas fa-pause-circle"></i>';
            renderTracks();
        }

        function togglePlay() {
            if (audioPlayer.paused) {
                if (currentIndex === -1) playTrack(0);
                else audioPlayer.play();
                playBtn.innerHTML = '<i class="fas fa-pause-circle"></i>';
            } else {
                audioPlayer.pause();
                playBtn.innerHTML = '<i class="fas fa-play-circle"></i>';
            }
        }

        function nextTrack() {
            playTrack((currentIndex + 1) % tracks.length);
        }

        function prevTrack() {
            playTrack((currentIndex - 1 + tracks.length) % tracks.length);
        }

        // Progress Bar
        audioPlayer.ontimeupdate = () => {
            const progress = (audioPlayer.currentTime / audioPlayer.duration) * 100;
            progressBar.style.width = `${progress}%`;
        };

        // Auto-next
        audioPlayer.onended = () => nextTrack();

        // Start
        loadTracks();
    </script>
</body>
</html>
