<!DOCTYPE html>
<html lang="uk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Фотограф | Лендінг</title>
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&display=swap" rel="stylesheet">
<style>
body {
    font-family: 'Montserrat', sans-serif;
    margin: 0;
    background-color: #fdf9f4;
    color: #222;
    overflow-x: hidden;
    scroll-behavior: smooth;
}
h1,h2,h3 { margin: 0; }
h1 { font-size: 2.8rem; font-weight: 700; color: #333; text-align: center; margin-bottom: 0.5rem; }
h2 { font-size: 2rem; font-weight: 600; color: #333; text-align: center; margin-bottom: 1rem; }
h3 { font-size: 1.5rem; font-weight: 600; color: #b85c38; margin-bottom: 10px; }
p { color: #555; font-weight: 500; margin: 5px 0; }
.subtitle { text-align: center; color: #666; font-size: 1rem; margin-bottom: 2rem; }

/* Анімації */
.fade-in { opacity: 0; transform: translateY(20px) scale(0.95); transition: all 0.8s ease; }
.fade-in.show { opacity: 1; transform: translateY(0) scale(1); }

/* Паралакс */
.parallax { position: relative; transition: transform 0.2s ease-out; }

/* Галерея */
.gallery { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; padding: 0 20px; max-width: 1200px; margin: 0 auto 4rem; }
.gallery-item { background: white; border-radius: 12px; overflow: hidden; text-align: center; box-shadow: 0 6px 20px rgba(0,0,0,0.1); transition: transform 0.5s ease, box-shadow 0.5s ease; }
.gallery-item img { width: 100%; display: block; border-bottom: 1px solid #eee; transition: transform 0.5s ease; }
.gallery-item:hover img { transform: scale(1.08) rotate(1deg); }
.gallery-item p { padding: 12px; }

/* Пакети */
.packages { background-color: #fff; padding: 3rem 20px; max-width: 1200px; margin: auto; border-radius: 12px; box-shadow: 0 8px 25px rgba(0,0,0,0.05); }
.packages-list { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 25px; margin-top: 2rem; }
.package { background: linear-gradient(145deg, #fff6f0, #fff9f7); border-radius: 15px; padding: 25px 20px; text-align: center; box-shadow: 0 6px 18px rgba(0,0,0,0.08); transition: transform 0.4s ease, box-shadow 0.4s ease; }
.package:hover { transform: translateY(-8px); box-shadow: 0 12px 30px rgba(0,0,0,0.15); }
.package button { margin-top: 15px; padding: 12px 25px; border: none; background-color: #b85c38; color: white; font-weight: 600; border-radius: 50px; cursor: pointer; font-size: 1rem; transition: all 0.3s ease; }
.package button:hover { background-color: #993f24; transform: translateY(-2px); box-shadow: 0 6px 15px rgba(0,0,0,0.2); }

/* Відгуки */
.reviews { padding: 3rem 20px; max-width: 1200px; margin: auto; }
.reviews-list { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 25px; margin-top: 2rem; }
.review { background: #fff; border-radius: 15px; padding: 25px 20px; box-shadow: 0 6px 20px rgba(0,0,0,0.1); text-align: center; transition: transform 0.3s ease, box-shadow 0.3s ease; }
.review:hover { transform: translateY(-5px); box-shadow: 0 12px 30px rgba(0,0,0,0.15); }
.review img { width: 80px; height: 80px; border-radius: 50%; margin-bottom: 12px; object-fit: cover; }

/* Про мене */
.about { background-color: #fff6f0; padding: 4rem 20px; border-radius: 12px; margin: 3rem auto; max-width: 1200px; display: flex; flex-wrap: wrap; align-items: center; gap: 25px; }
.about img { width: 250px; border-radius: 15px; object-fit: cover; box-shadow: 0 6px 20px rgba(0,0,0,0.1); }
.about-text { flex: 1; min-width: 250px; }
.about-text h2 { text-align: left; }
.about-text p { font-size: 1rem; color: #555; }

/* Модальне вікно */
.modal { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); display: none; justify-content: center; align-items: center; opacity: 0; transition: opacity 0.3s ease; z-index: 10000; }
.modal.show { display: flex; opacity: 1; }
.modal-content { background: #fff; padding: 30px 25px; border-radius: 15px; width: 90%; max-width: 450px; text-align: center; box-shadow: 0 12px 35px rgba(0,0,0,0.25); }
.modal-content h3 { color: #b85c38; margin-bottom: 20px; }
.modal-content input, .modal-content button { width: 100%; margin: 10px 0; padding: 12px; font-size: 1rem; border-radius: 8px; border: 1px solid #ccc; outline: none; }
.modal-content button { background-color: #b85c38; color: white; border: none; cursor: pointer; font-weight: 600; transition: all 0.3s ease; }
.modal-content button:hover { background-color: #993f24; transform: translateY(-2px); box-shadow: 0 6px 15px rgba(0,0,0,0.2); }

/* Соцмережі */
.socials { display: flex; justify-content: center; gap: 15px; margin-top: 15px; }
.socials a { text-decoration: none; color: #fff; padding: 10px 14px; border-radius: 50%; background-color: #b85c38; display: flex; align-items: center; justify-content: center; transition: all 0.3s ease; }
.socials a:hover { background-color: #993f24; transform: scale(1.1); }

/* Плаваюча кнопка */
.contact-btn { position: fixed; bottom: 25px; right: 25px; background: #b85c38; color: white; border: none; padding: 14px 28px; border-radius: 50px; cursor: pointer; box-shadow: 0 6px 15px rgba(0,0,0,0.15); font-size: 1rem; font-weight: 600; transition: all 0.3s ease; z-index: 1000; }
.contact-btn:hover { background: #993f24; transform: translateY(-2px); box-shadow: 0 8px 20px rgba(0,0,0,0.2); }
</style>
</head>
<body>

<h1 class="fade-in parallax">Довіряйте не словам, а світлинам</h1>
<p class="subtitle fade-in parallax">Емоційно та щиро — без зайвих слів</p>

<div class="gallery fade-in parallax">
    <div class="gallery-item"><img src="img1.jpg" loading="lazy"><p>Затьєвшлюбів рано</p></div>
    <div class="gallery-item"><img src="img2.jpg" loading="lazy"><p>Хочкак оцялка</p></div>
    <div class="gallery-item"><img src="img3.jpg" loading="lazy"><p>Вописана родин</p></div>
    <div class="gallery-item"><img src="img4.jpg" loading="lazy"><p>Зисясь цюмомівєз</p></div>
    <div class="gallery-item"><img src="img5.jpg" loading="lazy"><p>Поодшо нана</p></div>
    <div class="gallery-item"><img src="img6.jpg" loading="lazy"><p>Прооче зтюний</p></div>
</div>

<section class="packages fade-in parallax">
    <h2>Пакети послуг</h2>
    <div class="packages-list">
        <div class="package">
            <h3>Міні</h3>
            <p>30 хв зйомки</p>
            <p>10 фото з ретушшю</p>
            <p><strong>Від 70€</strong></p>
            <button onclick="openModal('Міні')">Обрати пакет</button>
        </div>
        <div class="package">
            <h3>Стандарт</h3>
            <p>1.5 години</p>
            <p>25 фото з ретушшю</p>
            <p><strong>Від 150€</strong></p>
            <button onclick="openModal('Стандарт')">Обрати пакет</button>
        </div>
        <div class="package">
            <h3>Преміум</h3>
            <p>3 години</p>
            <p>50 фото з ретушшю</p>
            <p>Персональна локація</p>
            <button onclick="openModal('Преміум')">Обрати пакет</button>
        </div>
    </div>
</section>

<section class="about fade-in parallax">
    <img src="photographer.jpg" loading="lazy" alt="Про мене">
    <div class="about-text">
        <h2>Про мене</h2>
        <p>Я професійний фотограф, який любить ловити справжні емоції. Моя мета – створювати світлини, які будуть надихати вас ще довгі роки.</p>
        <div class="socials">
            <a href="#" target="_blank">IG</a>
            <a href="#" target="_blank">TikTok</a>
            <a href="#" target="_blank">FB</a>
        </div>
    </div>
</section>

<section class="reviews fade-in parallax">
    <h2>Відгуки клієнтів</h2>
    <div class="reviews-list">
        <div class="review">
            <img src="client1.jpg" loading="lazy">
            <p>Кожен відгук дарує радість!</p>
        </div>
        <div class="review">
            <img src="client2.jpg" loading="lazy">
            <p>Неймовірний досвід!</p>
        </div>
    </div>
</section>

<!-- Модальне вікно -->
<div class="modal" id="modal">
    <div class="modal-content">
        <h3 id="modal-title">Замовити пакет</h3>
        <input type="text" placeholder="Ваше ім'я">
        <input type="tel" placeholder="Телефон">
        <button onclick="closeModal()">Відправити</button>
    </div>
</div>

<button class="contact-btn" onclick="openModal('Контакт')">Зв'язатися</button>

<script>
    // Fade-in анімація
    const fadeEls = document.querySelectorAll('.fade-in');
    const observer = new IntersectionObserver(entries => {
        entries.forEach(entry => { if(entry.isIntersecting) entry.target.classList.add('show'); });
    }, { threshold: 0.2 });
    fadeEls.forEach(el => observer.observe(el));

    // Модальне вікно
    const modal = document.getElementById('modal');
    const modalTitle = document.getElementById('modal-title');
    function openModal(pkg) { modalTitle.textContent = `Замовити пакет "${pkg}"`; modal.classList.add('show'); }
    function closeModal() { modal.classList.remove('show'); }
    modal.addEventListener('click', e => { if(e.target === modal) closeModal(); });

    // Паралакс загальні блоки
    const parallaxEls = document.querySelectorAll('.parallax');
    window.addEventListener('scroll', () => {
        const scrollTop = window.pageYOffset;
        parallaxEls.forEach(el => {
            const speed = 0.3;
            el.style.transform = `translateY(${scrollTop * speed}px)`;
        });

        // Паралакс для галереї з індивідуальною швидкістю і обертанням
        const galleryItems = document.querySelectorAll('.gallery-item img');
        galleryItems.forEach((img, index) => {
            const speed = 0.1 + (index * 0.02);
            img.style.transform = `translateY(${scrollTop * speed}px) rotate(${scrollTop * 0.01 * speed}deg)`;
        });
    });
</script>

</body>
</html>
