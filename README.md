<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Cartón de Bingo Musical Aleatorio</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Define the Arial font */
        @import url('https://fonts.googleapis.com/css2?family=Arial:wght@700&family=Dancing+Script:wght@400;700&display=swap');

        /* General styles for the body (visible on screen) */
        body {
            display: flex;
            flex-direction: column; /* Organizes elements in a column */
            justify-content: center; /* Centers content vertically */
            align-items: center;
            min-height: 100vh;
            width: 100vw; /* Ensures it takes up the full viewport width */
            /* Base lilac background for the body */
            background-color: #E0BBE4; /* Base lilac */
            /* Glitter effect overlay and Stars effect overlay */
            background-image: url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMCUiIGhlaWdodD0iMTAlIj4KICA8ZGVmcz4KICAgIDxwYXR0ZXJuIGlkPSJnIjB4IiBwYXR0ZXJuVW5pdHM9idXNlclNwYWNlT25Vc2UnIHdpZHRoPSI1IiBoZWlnaHQ9IjUiPj4KICAgICAgPGNpcmNsZSBjeD0iMi41IiBjeT0iMi41IiByPSIxLjUiIGZpbGw9IndoaXRlIiBvcGFjaXR5PSIxIi8+CiAgICA8L2RlZnM+CiAgPHJlY3QgZmlsbD0idXJsKCNnMHgpIiB3aWR0aD0iMTAwJSIgaGVpZ2h0PSIxMDAlIi8+Cjwvc3ZnPg=='),
                            url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyMCUiIGhlaWdodD0iMjAlIj4KICA8ZGVmcz4KICAgIDxwYXR0ZXJuIGlkPSJzdGFyIiBwYXR0ZXJuVW5pdHM9idXNlclNwYWNlT25Vc2UnIHdpZHRoPSIyMCIgaGVpZ2h0PSIyMCI+CiAgICAgIDxwb2x5Z29uIHBvaW50cz0iMTAuMCwwLjAgMTIuMyw3LjcgMjAuMCw3LjcgMTMuOCwxMi40IDE2LjIsMjAuMCAxMC4wLDE1LjMgMy44LDIwLjAgNi4yLDEyLjQgMC40LDcuNyA3LjcsNy43IiBmaWxsPSJ3aGl0ZSIgb3BhY2l0eT0iMC4xIi8+CiAgICA8L2RlZnM+CiAgPHJlY3QgZmlsbD0idXJsKCNzdGFyIiB3aWR0aD0iMTAwJSIgaGVpZ2h0PSIxMDAlIi8+Cjwvc3ZnPg==');
            background-size: 15px 15px, 50px 50px; /* Size of glitter and stars pattern */
            background-blend-mode: overlay, screen; /* Blends glitter and stars with the base color */
            margin: 0;
            padding: 20px;
            box-sizing: border-box;
            color: #333; /* Dark text color for contrast with light background */
        }

        /* Container for each bingo card (the new "wrapper" for title, grid, and hashtag) */
        .printable-card-wrapper {
            width: 14cm; /* Updated width to 14cm */
            height: 20cm; /* Updated height to 20cm */
            display: flex;
            flex-direction: column;
            align-items: center;
            /* Lilac and violet gradient background for the card, with predominant lilac */
            background-image: linear-gradient(to bottom right, #D8BFD8, #BA55D3, #9370DB); /* Thistle, MediumOrchid, MediumPurple */
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3); /* More pronounced shadow to highlight */
            border-radius: 0; /* Non-rounded borders */
            overflow: hidden; /* Ensures content does not overflow */
            margin: auto; /* Centers the card on the page */
            padding: 15px; /* Internal spacing for card content */
            box-sizing: border-box; /* Includes padding in total size */
            justify-content: space-between; /* Distributes content vertically */
            position: relative; /* Added for absolute positioning of the cat emoji */
        }

        /* Style for the title inside each card */
        .card-title-container {
            text-align: center;
            color: black; /* Black letters for the title */
            font-family: 'Arial', sans-serif;
            font-weight: bold; /* Bold */
            font-size: 1.7em; /* Increased font size for the main title */
            margin-bottom: 5px; /* Space below the title */
            width: 100%; /* Takes up full width of the card */
            text-shadow: none; /* Remove shadow if not needed with black text */
            display: flex; /* Use flexbox for alignment */
            flex-direction: column; /* Stack items vertically */
            justify-content: center; /* Center content horizontally */
            align-items: center; /* Center content vertically */
        }

        .card-title-container h1 {
            font-size: 1em; /* Adjusts "BINGO" size relative to its container */
            margin: 0;
            line-height: 1;
            color: white; /* BINGO in white */
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3); /* Shadow to highlight */
            display: flex; /* Ensure BINGO is a flex item for emoji alignment */
            align-items: center; /* Vertically align items within h1 */
            justify-content: center; /* Center content horizontally within h1 */
        }

        .card-title-container .musical-text {
            font-family: 'Dancing Script', cursive; /* Cursive font for "Musical" */
            font-style: italic;
            font-size: 0.9em; /* Increased "Musical" size relative to its container */
            display: block; /* Ensure Musical is a block element */
            margin-top: -5px; /* Adjusts vertical position of "Musical" */
            color: black; /* Musical in black */
        }

        /* Style for the sparkle emojis */
        .sparkle-emoji {
            font-size: 0.8em; /* Adjust emoji size relative to parent font */
            margin: 0 0.2em; /* Small margin around emojis */
            vertical-align: middle; /* Align with text vertically */
        }

        /* Container for the 9-song grid */
        .bingo-grid {
            width: 13cm; /* Adjusted width to fit within 14cm card with padding */
            height: 13cm; /* Adjusted height to fit within 20cm card with padding and other elements */
            display: grid;
            grid-template-columns: repeat(3, 1fr); /* 3 columns */
            grid-template-rows: repeat(3, 1fr);    /* 3 rows */
            background-color: transparent; /* Transparent background so the wrapper's gradient shows through gaps */
            gap: 5px; /* Space between cells */
            margin: 10px 0; /* Vertical margin to separate the grid from the title and hashtag */
        }

        /* Style for each cell (square) of the grid */
        .bingo-cell {
            display: flex;
            flex-direction: column; /* Stacks title and artist vertically */
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 5px; /* Internal spacing */
            background-color: #E6E6FA; /* Pastel lilac for cell background */
            border: 1px solid black; /* Thin black line for each square */
            box-sizing: border-box; /* Includes padding and border in total size */
            font-family: 'Arial', sans-serif; /* Arial font */
            font-weight: bold; /* Bold */
            font-size: 0.925em; /* Adjusted font size for song title and artist */
            line-height: 1.2; /* Line spacing */
            word-break: break-word; /* Breaks long words if necessary */
            color: black; /* Black text color inside cells */
            border-radius: 0; /* Non-rounded borders for each cell */
            cursor: pointer; /* Add cursor pointer to indicate interactivity */
            transition: background-color 0.2s ease; /* Smooth transition for background color */
        }

        /* Style for marked cells */
        .bingo-cell.marked {
            background-color: #B0C4DE; /* LightSteelBlue, a slightly darker shade of lilac */
        }

        .song-title {
            font-size: 1em; /* Font size for song title (relative to .bingo-cell) */
            margin-bottom: 5px; /* Increased space between title and artist */
        }

        .song-artist {
            font-size: 0.95em; /* Adjusted font size for artist (relative to .bingo-cell) */
            opacity: 1; /* Full opacity for artist */
            color: #0A0A40; /* Cosmic blue for artist name */
            text-shadow: none; /* Removed text-shadow for outline */
        }

        /* Hashtag container inside each card */
        .card-hashtag-container {
            text-align: right; /* Aligns text to the right */
            width: 100%; /* Takes up full width of the card container */
            margin-top: 5px; /* Space above the hashtag */
            color: white; /* White letters for the hashtag */
            font-family: 'Dancing Script', cursive; /* Cursive font for the hashtag */
            font-weight: bold; /* Bold */
            font-size: 1.3em; /* Increased font size for the hashtag */
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3); /* Shadow to highlight */
            padding-right: 5px; /* Small padding to separate from the right edge */
        }

        /* Styles for the BINGO animation overlay */
        #bingoAnimationOverlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7); /* Semi-transparent black background */
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000; /* Ensure it's on top of everything */
            opacity: 0; /* Start hidden */
            pointer-events: none; /* Allow clicks to pass through when hidden */
            transition: opacity 0.5s ease-in-out; /* Smooth fade-in/out */
        }

        #bingoAnimationOverlay.show {
            opacity: 1; /* Show the overlay */
            pointer-events: auto; /* Enable clicks when visible */
        }

        #bingoAnimationOverlay .bingo-message {
            font-family: 'Arial', sans-serif;
            font-size: 5em; /* Large font size for BINGO */
            color: #FFD700; /* Gold color */
            text-shadow: 4px 4px 8px rgba(0, 0, 0, 0.5); /* Stronger shadow */
            animation: popIn 0.5s ease-out forwards; /* Pop-in animation */
            transform: scale(0); /* Start scaled down */
        }

        @keyframes popIn {
            0% {
                transform: scale(0);
                opacity: 0;
            }
            80% {
                transform: scale(1.1);
                opacity: 1;
            }
            100% {
                transform: scale(1);
                opacity: 1;
            }
        }

        /* Media queries for screen responsiveness */
        @media (max-width: 600px) {
            .card-title-container {
                font-size: 1.4em; /* Adjusted for mobile */
            }
            .card-title-container h1 {
                font-size: 1em;
            }
            .card-title-container .musical-text {
                font-size: 0.8em; /* Adjusted for mobile */
            }
            .sparkle-emoji {
                font-size: 0.7em; /* Adjusted for mobile */
            }
            .printable-card-wrapper {
                width: 90vw; /* Takes up 90% of viewport width on small screens */
                height: auto; /* Adjust height automatically for mobile */
                margin: auto; /* Centers the card on mobile */
                padding: 5px;
            }
            .bingo-grid {
                width: 85vw; /* Adjusts grid width on mobile */
                height: 85vw; /* Maintains square proportion on mobile */
                gap: 3px;
                margin: 5px 0;
            }
            .bingo-cell {
                padding: 2px; /* Reduces padding on small screens */
                font-size: 0.925em; /* Adjusted font size for small screens */
            }
            .song-title {
                margin-bottom: 3px; /* Adjusted for mobile */
            }
            .song-artist {
                font-size: 0.95em; /* Adjusted for mobile (1.2em - 0.25em) */
            }
            .card-hashtag-container {
                font-size: 1.2em; /* Adjusted hashtag size on mobile */
                padding-right: 3px;
            }
            #bingoAnimationOverlay .bingo-message {
                font-size: 3em; /* Smaller font size for BINGO on mobile */
            }
        }

        /* Specific styles for printing */
        @media print {
            body {
                margin: 0;
                padding: 0;
                background: white !important; /* White background to save ink */
                -webkit-print-color-adjust: exact; /* Ensures colors are printed if active */
                print-color-adjust: exact;
            }
            .printable-card-wrapper {
                width: 14cm; /* Updated width for print */
                height: 20cm; /* Updated height for print */
                margin: auto; /* Centers the card on the printed page */
                box-shadow: none; /* Removes shadow from cards in print */
                /* To print the gradient on each card, uncomment the following lines
                   and ensure the browser has "Print background graphics" enabled */
                background-image: linear-gradient(to bottom right, #D8BFD8, #BA55D3, #9370DB); /* Thistle, MediumOrchid, MediumPurple */
                background-size: cover;
            }
            /* Ensures text is black in print by default, then overrides for specific elements */
            .card-title-container, .bingo-cell, .song-title {
                color: black !important;
                text-shadow: none !important;
            }
            /* Override for BINGO and hashtag to keep them white with shadow */
            .card-title-container h1,
            .card-hashtag-container {
                color: white !important;
                text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3) !important; /* Keep shadow for visibility */
            }
            /* Specific override for song artist color in print */
            .song-artist {
                color: #0A0A40 !important; /* Cosmic blue for artist name in print */
                text-shadow: none !important; /* Ensure no text-shadow/outline in print */
            }
            .bingo-cell.marked {
                background-color: #B0C4DE !important; /* Ensure marked color prints */
            }
            /* Hide bingo animation overlay when printing */
            #bingoAnimationOverlay {
                display: none !important;
            }
        }
    </style>
</head>
<body>
    <div id="bingoCardContainer">
        <!-- The random bingo card will be generated here -->
    </div>

    <!-- BINGO Animation Overlay -->
    <div id="bingoAnimationOverlay">
        <div class="bingo-message">¡BINGO!</div>
    </div>

    <script>
        // Full list of songs provided by the user
        const allSongs = [
            { title: "Ciega, Sordomuda", artist: "Shakira" },
            { title: "el cielo", artist: "TINI" },
            { title: "CORAZÓN VACÍO", artist: "Maria Becerra" },
            { title: "Princesa", artist: "Margarita, Rey" },
            { title: "Corazón Lunático", artist: "Airbag" },
            { title: "IConic.mp3", artist: "Emilia" },
            { title: "FANÁTICO", artist: "Lali" },
            { title: "MEJOR QUE VOS", artist: "Lali, Miranda!" },
            { title: "Mentía", artist: "Miranda!, Chano" },
            { title: "Cicatrices", artist: "Airbag" },
            { title: "LOKURA", artist: "Lali" },
            { title: "Cosas Que Odio de Vos", artist: "Floricienta" },
            { title: "Maldita Noche", artist: "Bandana" },
            { title: "2 Son 3", artist: "Lali" },
            { title: "Mucho, poquito o nada", artist: "Margarita" },
            { title: "EmotiHadas", artist: "Margarita, Daisy, Zeki, Unica, Alaska" },
            { title: "Que Nos Volvamos a Ver", artist: "Teenangels" },
            { title: "Pobres los Ricos", artist: "Floricienta" },
            { title: "Flores Amarillas", artist: "Margarita" },
            { title: "De Solo Vivir", artist: "Abel Pintos" },
            { title: "La partida de la gitana - Si te vas", artist: "Airbag" },
            { title: "Sólo necesito", artist: "#TocoParaVos, Meri Deal" },
            { title: "Callejero Favorito", artist: "Karina" },
            { title: "Mil Preguntas", artist: "Q' Lokura, Luck Ra" },
            { title: "Te Mentiría (Versión Cuarteto)", artist: "Luck Ra, La K'onga" },
            { title: "Estoy Aquí", artist: "Shakira" },
            { title: "Suerte (Whenever, Wherever)", artist: "Shakira" },
            { title: "Loba", artist: "Shakira" },
            { title: "Enamorada", artist: "Miranda!" },
            { title: "Prisionero", artist: "Miranda!" },
            { title: "Cuidado Que Te Supero", artist: "Q' Lokura, Los Herrera" },
            { title: "Toxic", artist: "Britney Spears" },
            { title: "Gimme More", artist: "Britney Spears" },
            { title: "Oops!...I Did It Again", artist: "Britney Spears" },
            { title: "Judas", artist: "Lady Gaga" },
            { title: "Poker Face", artist: "Lady Gaga" },
            { title: "Ocho Cuarenta", artist: "Rodrigo" },
            { title: "Virtual Diva", artist: "Don Omar" },
            { title: "Lloviendo Estrellas", artist: "Cristian Castro" },
            { title: "Ahora Te Puedes Marchar", artist: "Luis Miguel" },
            { title: "DESPECHÁ", artist: "ROSALÍA" },
            { title: "Perdonarte, ¿Para Qué?", artist: "Los Ángeles Azules, Emilia" },
            { title: "Limón y Sal", artist: "Julieta Venegas" },
            { title: "Flowers", artist: "Miley Cyrus" },
            { title: "Todo De Ti", artist: "Rauw Alejandro" },
            { title: "I Want It That Way", artist: "Backstreet Boys" },
            { title: "La Rubia del Avión", artist: "Los Ladrones Sueltos" },
            { title: "Bye Bye Bye", artist: "*NSYNC" },
            { title: "Amores Como el Nuestro", artist: "Los Charros" },
            { title: "La Ventanita", artist: "Grupo Sombras" },
            { title: "Llamado de Emergencia", artist: "Daddy Yankee" },
            { title: "Limbo", artist: "Daddy Yankee" },
            { title: "Bar", artist: "TINI, L-Gante" },
            { title: "Torero", artist: "Chayanne" },
            { title: "Eres para Mí", artist: "Julieta Venegas, Ana Tijoux" },
            { title: "La_Original.mp3", artist: "Emilia, TINI" },
            { title: "Quevedo: Bzrp Music Sessions, Vol. 52", artist: "Bizarrap, Quevedo" },
            { title: "Shakira: Bzrp Music Sessions, Vol. 53", artist: "Bizarrap, Shakira" },
            { title: "Mamichula", artist: "Nicki Nicole, Trueno" },
            { title: "Young Miko: Bzrp Music Sessions, Vol. 58", artist: "Bizarrap, Young Miko" },
            { title: "RAMEN PARA DOS", artist: "Maria Becerra, Paulo Londra, XROSS" },
            { title: "Con Otra", artist: "Cazzu" },
            { title: "MOTINHA 2.0 (Mete Marcha) - Remix", artist: "DENNIS, Luísa Sonza, Emilia" },
            { title: "Bet On It", artist: "Troy, Disney" },
            { title: "Bulería", artist: "David Bisbal" },
            { title: "Cruel Summer", artist: "Taylor Swift" },
            { title: "Cuando Te Vi | CROSSOVER #5", artist: "Big One, Maria Becerra, Trueno" },
            { title: "Heavy Is the Crown", artist: "Linkin Park" },
            { title: "POP/STARS", artist: "KDA" },
            { title: "Enemy", artist: "Imagine Dragons" },
            { title: "Let's Go to the Mall", artist: "Robin Sparkles" },
            { title: "Style", artist: "Taylor Swift" },
            { title: "Shake It Off (Taylor's Version)", artist: "Taylor Swift" },
            { title: "Lavender Haze", artist: "Taylor Swift" },
            { title: "Red (Taylor's Version)", artist: "Taylor Swift" },
            { title: "You Belong With Me (Taylor’s Version)", artist: "Taylor Swift" },
            { title: "Look What You Made Me Do", artist: "Taylor Swift" },
            { title: "Si Antes Te Hubiera Conocido", artist: "KAROL G" },
            { title: "Niña Bonita", artist: "Chino & Nacho" },
            { title: "Tu Misterioso Alguien", artist: "Miranda!" },
            { title: "Tiago PZK: Bzrp Music Sessions, Vol. 48", artist: "Bizarrap, Tiago PZK" },
            { title: "Noche Loca", artist: "Marama, Rombai" },
            { title: "La Despedida", artist: "Daddy Yankee" },
            { title: "Algo Me Gusta De Ti", artist: "Wisin & Yandel, Chris Brown, T-Pain" },
            { title: "Las de la Intuición", artist: "Shakira" },
            { title: "Bohemian Rhapsody", artist: "Queen" },
            { title: "Caballo Homosexual De Las Montañas", artist: "Karil" },
            { title: "33 Max Verstappen", artist: "Carte Blanq, Maxx Power" },
            { title: "Livin' On A Prayer", artist: "Bon Jovi" },
            { title: "Waka Waka (Esto es Africa)", artist: "Shakira, Freshlyground" },
            { title: "Chala Head Chala", artist: "Ricardo Silva" },
            { title: "Mi Corazón Encantado - Dragon Ball Gt", artist: "Ricardo Silva" },
            { title: "QUE ME FALTE TODO", artist: "Luck Ra, Abel Pintos" },
            { title: "Bajos Instintos", artist: "Airbag" } /* New song added */
        ];

        // Function to get an array of random songs without repetition
        function getRandomSongs(songs, count) {
            const shuffled = [...songs].sort(() => 0.5 - Math.random()); // Shuffles the array
            return shuffled.slice(0, count); // Takes the first 'count' songs
        }

        // Function to display the BINGO animation
        function showBingoAnimation() {
            const overlay = document.getElementById('bingoAnimationOverlay');
            overlay.classList.add('show'); // Add 'show' class to fade in

            // Hide the animation after 3 seconds
            setTimeout(() => {
                overlay.classList.remove('show'); // Remove 'show' class to fade out
            }, 3000);
        }

        // Function to check if all cells are marked for Bingo
        function checkBingo() {
            const cells = document.querySelectorAll('.bingo-cell');
            let allMarked = true;
            cells.forEach(cell => {
                if (!cell.classList.contains('marked')) {
                    allMarked = false;
                }
            });

            if (allMarked) {
                showBingoAnimation();
            }
        }

        // Function to generate a single bingo card element
        function createBingoCardElement(songs) {
            const cardWrapper = document.createElement('div');
            cardWrapper.classList.add('printable-card-wrapper');

            // Card title
            const titleContainer = document.createElement('div');
            titleContainer.classList.add('card-title-container');
            titleContainer.innerHTML = `<h1><span class="sparkle-emoji">✨</span> BINGO <span class="sparkle-emoji">✨</span></h1><span class="musical-text">Musical</span>`;
            cardWrapper.appendChild(titleContainer);

            // 9-song grid
            const gridContainer = document.createElement('div');
            gridContainer.classList.add('bingo-grid');
            songs.forEach(song => {
                const cell = document.createElement('div');
                cell.classList.add('bingo-cell');
                // Add click event listener to toggle 'marked' class and check for bingo
                cell.addEventListener('click', function() {
                    this.classList.toggle('marked');
                    checkBingo(); // Check for bingo after each click
                });
                const artistText = song.artist ? song.artist : '';
                cell.innerHTML = `<div class="song-title">${song.title}</div><div class="song-artist">${artistText}</div>`;
                gridContainer.appendChild(cell);
            });
            cardWrapper.appendChild(gridContainer);

            // Hashtag
            const hashtagContainer = document.createElement('div');
            hashtagContainer.classList.add('card-hashtag-container');
            hashtagContainer.innerHTML = `#Los25deSabry <span class="sparkle-emoji">🎉</span>`;
            cardWrapper.appendChild(hashtagContainer);

            return cardWrapper;
        }

        // Function to generate and display a single random bingo card on page load
        function generateRandomBingoCard() {
            const bingoCardContainer = document.getElementById('bingoCardContainer');
            bingoCardContainer.innerHTML = ''; // Clear any existing card

            const selectedSongs = getRandomSongs(allSongs, 9); // Selects 9 songs for the card
            const bingoCard = createBingoCardElement(selectedSongs);
            bingoCardContainer.appendChild(bingoCard);
        }

        // Call this function when the window loads
        window.onload = () => {
            generateRandomBingoCard(); // Generates a single random bingo card
        };
    </script>
</body>
</html>
