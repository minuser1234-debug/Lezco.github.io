# Lezco.github.io

<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>🌍 Чудеса мира</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, Helvetica, sans-serif;
            background:
                linear-gradient(rgba(10, 25, 47, 0.65), rgba(10, 25, 47, 0.65)),
                url("https://images.unsplash.com/photo-1501785888041-af3ef285b470?auto=format&fit=crop&w=2000&q=80")
                center / cover fixed;
            color: #172033;
            min-height: 100vh;
        }

        /* ===== ШАПКА ===== */

        header {
            text-align: center;
            color: white;
            padding: 70px 20px 55px;
        }

        header .globe {
            font-size: 65px;
            margin-bottom: 15px;
        }

        header h1 {
            font-size: clamp(35px, 6vw, 65px);
            margin-bottom: 15px;
            text-shadow: 0 4px 15px rgba(0,0,0,0.4);
        }

        header p {
            font-size: 20px;
            opacity: 0.95;
        }

        /* ===== ОСНОВНОЙ БЛОК ===== */

        .main {
            width: min(1250px, 94%);
            margin: 0 auto 60px;
        }

        .top-panel {
            background: rgba(255,255,255,0.94);
            border-radius: 22px;
            padding: 20px;
            margin-bottom: 30px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.2);
        }

        .search {
            width: 100%;
            padding: 17px 22px;
            border: 2px solid transparent;
            border-radius: 14px;
            font-size: 17px;
            outline: none;
            background: #f0f4f8;
            transition: 0.25s;
        }

        .search:focus {
            border-color: #1683c5;
            background: white;
        }

        /* ===== КАРТОЧКИ ===== */

        .cards {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 25px;
        }

        .card {
            background: white;
            border-radius: 22px;
            overflow: hidden;
            cursor: pointer;
            box-shadow: 0 12px 30px rgba(0,0,0,0.22);
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .card:hover {
            transform: translateY(-9px);
            box-shadow: 0 20px 45px rgba(0,0,0,0.3);
        }

        .photo-box {
            width: 100%;
            height: 245px;
            background: #dfe8ee;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .photo-box img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            background: #e8eef2;
            transition: transform 0.5s;
        }

        .card:hover .photo-box img {
            transform: scale(1.04);
        }

        .card-info {
            padding: 20px;
        }

        .card-info h2 {
            font-size: 22px;
            margin-bottom: 8px;
            color: #142238;
        }

        .country {
            color: #0784bd;
            font-size: 16px;
            font-weight: bold;
        }

        .click {
            display: inline-block;
            margin-top: 15px;
            padding: 8px 13px;
            border-radius: 20px;
            background: #e9f6fc;
            color: #0878aa;
            font-size: 13px;
        }

        /* ===== МОДАЛЬНОЕ ОКНО ===== */

        .modal {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.78);
            display: none;
            align-items: center;
            justify-content: center;
            padding: 20px;
            z-index: 100;
        }

        .modal.show {
            display: flex;
        }

        .modal-box {
            width: min(850px, 100%);
            max-height: 92vh;
            overflow-y: auto;
            background: white;
            border-radius: 25px;
            position: relative;
            animation: popup 0.3s ease;
        }

        @keyframes popup {
            from {
                opacity: 0;
                transform: scale(0.85);
            }

            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        .modal-image {
            height: 430px;
            width: 100%;
            background: #e4ebef;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 25px 25px 0 0;
            overflow: hidden;
        }

        .modal-image img {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }

        .modal-text {
            padding: 35px;
        }

        .modal-text h2 {
            font-size: 35px;
            margin-bottom: 8px;
        }

        .modal-country {
            color: #0784bd;
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 25px;
        }

        .modal-text h3 {
            margin-top: 25px;
            margin-bottom: 8px;
            color: #172033;
        }

        .modal-text p {
            font-size: 17px;
            line-height: 1.7;
            color: #4a5565;
        }

        .close {
            position: absolute;
            right: 18px;
            top: 18px;
            width: 45px;
            height: 45px;
            border: none;
            border-radius: 50%;
            background: rgba(0,0,0,0.65);
            color: white;
            font-size: 30px;
            cursor: pointer;
            z-index: 5;
            transition: 0.2s;
        }

        .close:hover {
            background: #e63946;
            transform: rotate(90deg);
        }

        /* ===== FOOTER ===== */

        footer {
            color: white;
            text-align: center;
            padding: 35px 20px;
            background: rgba(5, 15, 30, 0.85);
        }

        footer p {
            font-size: 16px;
        }

        /* ===== АДАПТАЦИЯ ===== */

        @media (max-width: 950px) {
            .cards {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 600px) {
            header {
                padding: 45px 15px;
            }

            header .globe {
                font-size: 50px;
            }

            .cards {
                grid-template-columns: 1fr;
            }

            .photo-box {
                height: 250px;
            }

            .modal-image {
                height: 270px;
            }

            .modal-text {
                padding: 25px;
            }

            .modal-text h2 {
                font-size: 27px;
            }
        }
    </style>
</head>

<body>

<header>
    <div class="globe">🌍</div>

    <h1>Чудеса мира</h1>

    <p>
        Откройте самые известные достопримечательности нашей планеты
    </p>
</header>


<main class="main">

    <div class="top-panel">

        <input
            class="search"
            id="search"
            type="text"
            placeholder="Поиск достопримечательности или страны..."
        >

    </div>


    <div class="cards" id="cards"></div>

</main>


<!-- МОДАЛЬНОЕ ОКНО -->

<div class="modal" id="modal">

    <div class="modal-box">

        <button class="close" id="close">
            ×
        </button>

        <div class="modal-image">
            <img id="modalImage" src="" alt="">
        </div>

        <div class="modal-text">

            <h2 id="modalTitle"></h2>

            <div class="modal-country" id="modalCountry"></div>

            <h3>📖 О достопримечательности</h3>

            <p id="modalDescription"></p>

            <h3>Интересный факт</h3>

            <p id="modalFact"></p>

        </div>

    </div>

</div>


<footer>

    <p>
         Изучай мир — одно место за другим
    </p>

</footer>


<script>

const places = [

    {
        name: "Эйфелева башня",
        country: "🇫🇷 Франция — Париж",

        image:
        "https://traveldigg.com/wp-content/uploads/2016/06/Eiffel-Tower-Photo.jpg",

        description:
        "Эйфелева башня — металлическая башня в Париже, построенная к Всемирной выставке 1889 года. Она стала одним из главных символов Франции и Парижа.",

        fact:
        "Башня получила название в честь инженера Гюстава Эйфеля."
    },


    {
        name: "Тадж-Махал",
        country: "🇮🇳 Индия — Агра",

        image:
        "https://i.pinimg.com/originals/79/6c/a0/796ca0e248e0946720742ecc5e35aeda.jpg",

        description:
        "Тадж-Махал — мавзолей из белого мрамора в городе Агра. Комплекс был построен по приказу императора Шах-Джахана.",

        fact:
        "Строительство комплекса продолжалось несколько десятилетий и привлекло тысячи мастеров."
    },


    {
        name: "Колизей",
        country: "🇮🇹 Италия — Рим",

        image:
        "https://al-rahhala.com/wp-content/uploads/2024/10/pexels-pixabay-356966-scaled.jpg",

        description:
        "Колизей — огромный древнеримский амфитеатр в центре Рима. В древности здесь проводились различные публичные представления.",

        fact:
        "Колизей является одним из наиболее известных памятников Древнего Рима."
    },


    {
        name: "Статуя Христа-Искупителя",
        country: "🇧🇷 Бразилия — Рио-де-Жанейро",

        image:
        "https://images-bonnier.imgix.net/files/his/production/2023/06/09105118/christus-de-verlosser-rio-de-janeiro-cristo-redentor.jpeg?ar=1.5%3A1&auto=format%2Ccompress&fit=crop&q=80&w=1200",

        description:
        "Монумент Христа-Искупителя расположен на горе Корковаду над Рио-де-Жанейро. С распростёртыми руками статуя возвышается над городом и заливом.",

        fact:
        "Статуя была открыта в 1931 году."
    },


    {
        name: "Великая Китайская стена",
        country: "🇨🇳 Китай",

        image:
        "https://sitecore-cd.shangri-la.com/-/media/Shangri-La/beijing_chinaworld/about/local-guide/explore-beijing/cc.jpg",

        description:
        "Великая Китайская стена — огромная система укреплений, которую строили и перестраивали на протяжении многих веков.",

        fact:
        "Отдельные участки стены проходят по горным хребтам и имеют сложный рельеф."
    },


    {
        name: "Мачу-Пикчу",
        country: "🇵🇪 Перу",

        image:
        "https://media-api.xogrp.com/images/ad14d420-3515-4274-8b62-a1493ec49087~rs_768.h-cr_117.0.2002.1414",

        description:
        "Мачу-Пикчу — древний город инков, расположенный высоко в Андах. Каменные постройки, террасы и горы создают характерный ландшафт этого места.",

        fact:
        "Археологический комплекс расположен на высоте более 2 000 метров над уровнем моря."
    },


    {
        name: "Петра",
        country: "🇯🇴 Иордания",

        image:
        "https://www.petranightstours.com/uploads/images/cms/1656146964_Petra_Treasury_2.jpg",

        description:
        "Петра — древний город на территории современной Иордании. Многие его сооружения были высечены непосредственно в песчаниковых скалах.",

        fact:
        "Одним из самых известных сооружений Петры является Аль-Хазна, или Казна."
    },


    {
        name: "Сиднейский оперный театр",
        country: "🇦🇺 Австралия — Сидней",

        image:
        "https://megaconstrucciones.net/images/edificios-civiles/foto/sydney-opera-house.jpg",

        description:
        "Сиднейский оперный театр расположен на берегу гавани. Его крыши в форме парусов стали одним из самых узнаваемых архитектурных образов Австралии.",

        fact:
        "Здание официально открылось в 1973 году."
    },


    {
        name: "Биг-Бен",
        country: "🇬🇧 Великобритания — Лондон",

        image:
        "https://www.viajaralondres.com/wp-content/uploads/2014/09/BigBen-vertical.jpg",

        description:
        "Биг-Бен — популярное название знаменитой часовой башни Вестминстерского дворца в Лондоне. Башня является одним из символов британской столицы.",

        fact:
        "Название «Биг-Бен» первоначально относилось к большому колоколу внутри башни."
    },


    {
        name: "Саграда Фамилия",
        country: "🇪🇸 Испания — Барселона",

        image:
        "https://media.seafy.com/media/1767951683/sagrada-familia-a-barcellona-in-una-giornata-di-febbraio.png?size=1280x-&webp=",

        description:
        "Саграда Фамилия — знаменитая базилика в Барселоне, созданная по проекту архитектора Антонио Гауди. Её высокие башни и сложные фасады делают здание легко узнаваемым.",

        fact:
        "Архитектура храма сочетает элементы готики и уникальный стиль Гауди."
    }

];


const cards = document.getElementById("cards");

const modal = document.getElementById("modal");

const closeButton = document.getElementById("close");

const search = document.getElementById("search");


/* ===== СОЗДАНИЕ КАРТОЧЕК ===== */

function showCards(list) {

    cards.innerHTML = "";

    if (list.length === 0) {

        cards.innerHTML = `
            <div style="
                grid-column: 1 / -1;
                background:white;
                padding:40px;
                border-radius:20px;
                text-align:center;
                font-size:20px;
            ">
                 Ничего не найдено
            </div>
        `;

        return;
    }


    list.forEach((place) => {

        const card = document.createElement("article");

        card.className = "card";


        card.innerHTML = `

            <div class="photo-box">

                <img
                    src="${place.image}"
                    alt="${place.name}"
                    loading="lazy"
                >

            </div>


            <div class="card-info">

                <h2>
                    ${place.name}
                </h2>

                <div class="country">
                    ${place.country}
                </div>

                <span class="click">
                    Нажмите, чтобы узнать больше →
                </span>

            </div>
        `;


        card.addEventListener("click", () => {

            openModal(place);

        });


        cards.appendChild(card);

    });

}


/* ===== ОТКРЫТИЕ ОКНА ===== */

function openModal(place) {

    document.getElementById("modalImage").src =
        place.image;

    document.getElementById("modalImage").alt =
        place.name;

    document.getElementById("modalTitle").textContent =
        place.name;

    document.getElementById("modalCountry").textContent =
        place.country;

    document.getElementById("modalDescription").textContent =
        place.description;

    document.getElementById("modalFact").textContent =
        place.fact;


    modal.classList.add("show");

    document.body.style.overflow = "hidden";
}


/* ===== ЗАКРЫТИЕ ===== */

function closeModal() {

    modal.classList.remove("show");

    document.body.style.overflow = "auto";
}


closeButton.addEventListener(
    "click",
    closeModal
);


modal.addEventListener(
    "click",
    function(event) {

        if (event.target === modal) {

            closeModal();

        }

    }
);


document.addEventListener(
    "keydown",
    function(event) {

        if (event.key === "Escape") {

            closeModal();

        }

    }
);


/* ===== ПОИСК ===== */

search.addEventListener(
    "input",
    function() {

        const query =
            this.value.toLowerCase().trim();


        const filtered =
            places.filter(place =>

                place.name
                    .toLowerCase()
                    .includes(query)

                ||

                place.country
                    .toLowerCase()
                    .includes(query)

            );


        showCards(filtered);

    }
);


/* ===== ЗАПУСК ===== */

showCards(places);

</script>

</body>
</html>
