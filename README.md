// script.js
document.addEventListener('DOMContentLoaded', () => {
    // Função para o Slider de Imagem
    let currentSlide = 0;
    const slides = document.querySelectorAll('.slider img');
    const totalSlides = slides.length;

    function showSlide(index) {
        slides.forEach((slide, i) => {
            slide.style.display = i === index ? 'block' : 'none';
        });
    }

    function nextSlide() {
        currentSlide = (currentSlide + 1) % totalSlides;
        showSlide(currentSlide);
    }

    function previousSlide() {
        currentSlide = (currentSlide - 1 + totalSlides) % totalSlides;
        showSlide(currentSlide);
    }

    // Inicializar o slider
    showSlide(currentSlide);
    setInterval(nextSlide, 5000); // Muda de slide a cada 5 segundos

    // Função para validação do formulário
    const form = document.querySelector('form');
    form.addEventListener('submit', (event) => {
        const nome = document.getElementById('nome').value;
        const email = document.getElementById('email').value;
        const mensagem = document.getElementById('mensagem').value;

        if (!nome || !email || !mensagem) {
            alert('Todos os campos são obrigatórios.');
            event.preventDefault();
        }
    });

    // Função para Scroll Suave
    const menuLinks = document.querySelectorAll('nav a[href^="#"]');
    menuLinks.forEach(link => {
        link.addEventListener('click', (event) => {
            event.preventDefault();
            const targetId = link.getAttribute('href').substring(1);
            const targetElement = document.getElementById(targetId);

            if (targetElement) {
                targetElement.scrollIntoView({
                    behavior: 'smooth'
                });
            }
        });
    });
});
