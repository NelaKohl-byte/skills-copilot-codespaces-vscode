<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kniha pro Tebe</title>
    <style>
        body {
            margin: 0;
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #f3e6e8, #ffe5d9);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
        }

        .book-container {
            width: 90%;
            max-width: 400px;
            height: 90vh;
            perspective: 2000px;
        }

        .book {
            width: 100%;
            height: 100%;
            position: relative;
            transform-style: preserve-3d;
            transition: transform 0.5s;
        }

        .page {
            position: absolute;
            width: 100%;
            height: 100%;
            background: white;
            border: 1px solid #ddd;
            border-radius: 5px;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
            transform-origin: left;
            backface-visibility: hidden;
            transform: rotateY(0deg);
            overflow: hidden;
        }

        .page-content {
            padding: 20px;
            text-align: center;
        }

        .page h2 {
            color: #ff6f61;
            font-size: 1.5em;
        }

        .page:nth-child(even) {
            transform-origin: right;
        }

        .page:nth-child(odd) {
            background: #fefefe;
        }

        .page.flipped {
            transform: rotateY(-180deg);
        }

        .controls {
            position: absolute;
            bottom: 10px;
            display: flex;
            justify-content: space-between;
            width: 90%;
            max-width: 400px;
        }

        .controls button {
            background: #ff6f61;
            color: white;
            font-size: 1em;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            transition: 0.3s;
        }

        .controls button:hover {
            background: #ff3d2e;
        }

        /* Responsivní design */
        @media (max-width: 480px) {
            .page h2 {
                font-size: 1.2em;
            }

            .page-content {
                padding: 15px;
            }

            .controls button {
                font-size: 0.9em;
                padding: 8px 15px;
            }
        }
    </style>
</head>
<body>
    <div class="book-container">
        <div class="book">
            <!-- Stránka 1 -->
            <div class="page">
                <div class="page-content">
                    <h2>Vítej, lásko</h2>
                    <p>Jsem tak šťastná, že tě mám. Tato knížka je věnována tobě a našim společným okamžikům.</p>
                </div>
            </div>

            <!-- Stránka 2 -->
            <div class="page">
                <div class="page-content">
                    <h2>100 důvodů, proč tě miluji</h2>
                    <ul style="text-align: left; font-size: 0.9em;">
                        <li>Vždy mě rozesměješ.</li>
                        <li>Věříš ve mě i v těžkých chvílích.</li>
                        <li>Jsi laskavý ke všem okolo.</li>
                        <li>Máme stejný smysl pro humor.</li>
                        <li>Tvoje objetí je moje bezpečné místo.</li>
                    </ul>
                </div>
            </div>

            <!-- Stránka 3 -->
            <div class="page">
                <div class="page-content">
                    <h2>Nejkrásnější vzpomínky</h2>
                    <p style="font-size: 0.9em;">
                        1. Naše první rande v kavárně.<br>
                        2. Výlet na hory a ten západ slunce.<br>
                        3. První společné Vánoce.<br>
                        4. Náš tajný piknik na louce.<br>
                        5. Když jsme společně zvládli náš první problém.
                    </p>
                </div>
            </div>

            <!-- Stránka 4 -->
            <div class="page">
                <div class="page-content">
                    <h2>Naše písnička</h2>
                    <p>
                        Tvoje písnička je pro mě navždy <strong>Tereza Kerndlová – Schody z nebe</strong>.
                    </p>
                </div>
            </div>

            <!-- Stránka 5 -->
            <div class="page">
                <div class="page-content">
                    <h2>Oblíbený obrázek</h2>
                    <img src="https://via.placeholder.com/300x200" alt="Oblíbený obrázek" style="width: 100%; border-radius: 10px;">
                </div>
            </div>
        </div>
    </div>

    <div class="controls">
        <button onclick="prevPage()">Předchozí</button>
        <button onclick="nextPage()">Další</button>
    </div>

    <script>
        const book = document.querySelector('.book');
        const pages = document.querySelectorAll('.page');
        let currentPage = 0;

        function updatePages() {
            pages.forEach((page, index) => {
                if (index <= currentPage) {
                    page.classList.add('flipped');
                } else {
                    page.classList.remove('flipped');
                }
            });
        }

        function nextPage() {
            if (currentPage < pages.length - 1) {
                currentPage++;
                updatePages();
            }
        }

        function prevPage() {
            if (currentPage > 0) {
                currentPage--;
                updatePages();
            }
        }
    </script>
</body>
</html>