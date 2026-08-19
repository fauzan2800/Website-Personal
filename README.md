# Website-Personal
web
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Batu Kertas Gunting</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #2563eb, #7c3aed);
            color: white;
            text-align: center;
            min-height: 100vh;
        }

        .slide {
            display: none;
            min-height: 100vh;
            padding: 80px 20px;
        }

        .aktif {
            display: block;
        }

        .box {
            max-width: 600px;
            margin: auto;
            background: rgba(0,0,0,0.3);
            padding: 30px;
            border-radius: 20px;
        }

        h1 {
            font-size: 45px;
        }

        button {
            border: none;
            border-radius: 15px;
            padding: 15px 25px;
            margin: 10px;
            font-size: 20px;
            cursor: pointer;
            transition: 0.2s;
        }

        button:hover {
            transform: scale(1.08);
        }

        .mulai {
            background: #22c55e;
            color: white;
        }

        .pilihan {
            background: white;
            font-size: 45px;
            width: 120px;
            height: 100px;
        }

        .kembali {
            background: #64748b;
            color: white;
        }

        #hasil {
            font-size: 25px;
            margin: 25px;
            min-height: 60px;
        }

        .skor {
            font-size: 25px;
            margin: 20px;
        }
    </style>
</head>

<body>

    <!-- SLIDE 1 -->
    <section id="slide1" class="slide aktif">
        <div class="box">
            <h1>🎮</h1>
            <h1>Batu Kertas Gunting</h1>
            <p>Siap melawan komputer?</p>

            <button class="mulai" onclick="keGame()">
                ▶ MULAI GAME
            </button>
        </div>
    </section>


    <!-- SLIDE 2 -->
    <section id="slide2" class="slide">
        <div class="box">

            <h1>🕹️ Pilih!</h1>

            <div class="skor">
                Kamu: <span id="skorKamu">0</span>
                &nbsp; - &nbsp;
                Komputer: <span id="skorKomputer">0</span>
            </div>

            <div>
                <button class="pilihan" onclick="main('batu')">
                    🪨
                </button>

                <button class="pilihan" onclick="main('kertas')">
                    📄
                </button>

                <button class="pilihan" onclick="main('gunting')">
                    ✂️
                </button>
            </div>

            <div id="hasil">
                Pilih salah satu!
            </div>

            <button class="kembali" onclick="keMenu()">
                ← Menu
            </button>

            <button class="mulai" onclick="resetGame()">
                🔄 Reset
            </button>

        </div>
    </section>


    <script>
        let skorKamu = 0;
        let skorKomputer = 0;

        function tampilkanSlide(nomor) {
            document.querySelectorAll(".slide").forEach(slide => {
                slide.classList.remove("aktif");
            });

            document
                .getElementById("slide" + nomor)
                .classList.add("aktif");
        }

        function keGame() {
            tampilkanSlide(2);
        }

        function keMenu() {
            tampilkanSlide(1);
        }

        function main(pilihanKamu) {

            const pilihan = ["batu", "kertas", "gunting"];

            const pilihanKomputer =
                pilihan[Math.floor(Math.random() * 3)];

            let hasil = "";

            if (pilihanKamu === pilihanKomputer) {
                hasil = "🤝 SERI!";
            }

            else if (
                (pilihanKamu === "batu" && pilihanKomputer === "gunting") ||
                (pilihanKamu === "kertas" && pilihanKomputer === "batu") ||
                (pilihanKamu === "gunting" && pilihanKomputer === "kertas")
            ) {
                skorKamu++;
                hasil = "🎉 KAMU MENANG!";
            }

            else {
                skorKomputer++;
                hasil = "😢 KOMPUTER MENANG!";
            }

            document.getElementById("hasil").innerHTML =
                "Kamu: " + emoji(pilihanKamu) +
                " &nbsp; VS &nbsp; " +
                "Komputer: " + emoji(pilihanKomputer) +
                "<br><br>" +
                hasil;

            document.getElementById("skorKamu").textContent =
                skorKamu;

            document.getElementById("skorKomputer").textContent =
                skorKomputer;
        }

        function emoji(pilihan) {

            if (pilihan === "batu") {
                return "🪨";
            }

            if (pilihan === "kertas") {
                return "📄";
            }

            return "✂️";
        }

        function resetGame() {
            skorKamu = 0;
            skorKomputer = 0;

            document.getElementById("skorKamu").textContent = 0;
            document.getElementById("skorKomputer").textContent = 0;

            document.getElementById("hasil").innerHTML =
                "Pilih salah satu!";
        }
    </script>

</body>
</html>
```
