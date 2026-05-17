<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grill Masters</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <header class="header">
        <img src="logo.jpg" alt="Grill Masters Logo" class="main-logo">
    </header>

    <main class="container">
        
        <section class="scroll-element slide-left">
            <h2>The Art of the Grill</h2>
            <p>Where smoke meets perfection. We bring premium flavors, intense heat, and master-level execution to every single dish.</p>
        </section>

        <section class="scroll-element slide-right">
            <h2>Our Signature Menu</h2>
            <p>Sizzling legendary burgers, wood-fired masterpieces, and smoked perfection crafted daily with bold, secret recipes.</p>
        </section>

        <section class="scroll-element slide-left">
            <h2>Experience The Flame</h2>
            <p>It's not just food; it's an experience. Step into an atmosphere fueled by passion, elite taste, and burning perfection.</p>
        </section>

    </main>

    <footer class="footer">
        <p>Created by <strong>Karan Verma</strong></p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
/* Core Reset and Black & White Theme */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background-color: #000000; /* Absolute Black */
    color: #ffffff; /* Crisp White */
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    overflow-x: hidden;
}

/* Header Setup */
.header {
    height: 100vh; /* Takes full screen height on load */
    display: flex;
    justify-content: center;
    align-items: center;
    background: radial-gradient(circle, #1a1a1a 0%, #000000 100%);
}

.main-logo {
    max-width: 350px;
    width: 80%;
    height: auto;
    filter: drop-shadow(0 0 20px rgba(255, 68, 0, 0.2)); /* Subtle fiery ambient glow */
}

/* Content Container */
.container {
    max-width: 800px;
    margin: 0 auto;
    padding: 40px 20px 150px 20px;
}

/* Scroll Section Bases */
.scroll-element {
    margin-bottom: 120px;
    padding: 40px;
    border-left: 4px solid #ffffff; /* Sharp white accent line */
    background: #0a0a0a;
    transition: transform 0.8s ease-out, opacity 0.8s ease-out;
    opacity: 0; /* Hidden initially */
}

.scroll-element h2 {
    font-size: 2rem;
    margin-bottom: 15px;
    text-transform: uppercase;
    letter-spacing: 2px;
}

.scroll-element p {
    color: #a0a0a0; /* Muted gray for body text readability */
    line-height: 1.6;
    font-size: 1.1rem;
}

/* Animation Starting States */
.slide-left {
    transform: translateX(-150px);
}

.slide-right {
    transform: translateX(150px);
}

/* Animation Active State (Triggered by JS) */
.scroll-element.scrolled {
    opacity: 1;
    transform: translateX(0);
}

/* Footer Details */
.footer {
    text-align: center;
    padding: 40px 20px;
    border-top: 1px solid #1a1a1a;
    background-color: #000000;
}

.footer p {
    color: #666666;
    font-size: 0.9rem;
    letter-spacing: 1px;
}

.footer strong {
    color: #ffffff;
}
// Grab all sections we want to animate
const scrollElements = document.querySelectorAll(".scroll-element");

const elementInView = (el, dividend = 1) => {
  const elementTop = el.getBoundingClientRect().top;
  return (
    elementTop <= (window.innerHeight || document.documentElement.clientHeight) / dividend
  );
};

const displayScrollElement = (element) => {
  element.classList.add("scrolled");
};

const handleScrollAnimation = () => {
  scrollElements.forEach((el) => {
    if (elementInView(el, 1.25)) {
      displayScrollElement(el);
    }
  });
}

// Trigger check on scroll
window.addEventListener("scroll", () => { 
  handleScrollAnimation();
});

// Run once on load to catch anything already in view
handleScrollAnimation();
