<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RestWellCollective | Blog & Initiative</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Lato:wght@300;400;700&display=swap" rel="stylesheet">

    <style>
        /* --- CSS VARIABLES & RESET --- */
        :root {
            /* TWEAKED: Custom theme based on RestWellCollective logo */
            --primary-theme: #A8D5BA; /* Soft mint/cyan from the logo */
            --secondary-theme: #E8E5A8; /* Soft yellow/cream from the logo */
            --accent-blue: #7EC4CF; /* Light blue accent */
            --secondary-bg: #f9fdf9;
            --text-color: #2d3e3f;
            --light-text: #fff;
            --font-heading: 'Playfair Display', serif;
            --font-body: 'Lato', sans-serif;
            --transition-speed: 0.4s;
            /* TWEAKED: Soft theme colors derived from logo palette */
            --primary-soft: rgba(168, 213, 186, 0.15);
            --secondary-soft: rgba(232, 229, 168, 0.15);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: var(--font-body);
            color: var(--text-color);
            line-height: 1.6;
            background-color: #fff;
            overflow-x: hidden;
            transition: background-color 0.6s ease;
        }

        /* --- NAVIGATION --- */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            background: rgba(255, 255, 255, 0.90);
            backdrop-filter: blur(15px);
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(168, 213, 186, 0.1);
            transition: all 0.3s ease;
            border-bottom: 1px solid rgba(168, 213, 186, 0.2);
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 15px;
            z-index: 1001; /* RESPONSIVE: Keep logo above hamburger */
        }

        #site-logo {
            height: 50px;
            width: auto;
            object-fit: contain;
            transition: transform 0.3s ease;
        }
        
        #site-logo:hover {
            transform: scale(1.05) rotate(-2deg);
        }

        .brand-name {
            font-family: var(--font-heading);
            font-weight: 700;
            font-size: 1.5rem;
            color: var(--primary-theme);
            transition: color 0.6s ease;
        }

        /* RESPONSIVE: Hamburger Menu */
        .hamburger {
            display: none; /* Hidden on desktop */
            flex-direction: column;
            gap: 5px;
            cursor: pointer;
            z-index: 1001;
            padding: 10px;
        }

        .hamburger span {
            width: 25px;
            height: 3px;
            background: var(--primary-theme);
            border-radius: 3px;
            transition: all 0.3s ease;
        }

        .hamburger.active span:nth-child(1) {
            transform: rotate(45deg) translate(7px, 7px);
        }

        .hamburger.active span:nth-child(2) {
            opacity: 0;
        }

        .hamburger.active span:nth-child(3) {
            transform: rotate(-45deg) translate(7px, -7px);
        }

        .nav-links {
            display: flex;
            align-items: center;
        }

        .nav-links a, .nav-links span {
            text-decoration: none;
            color: var(--text-color);
            margin-left: 30px;
            font-weight: 700;
            transition: color 0.3s, transform 0.3s;
            cursor: pointer;
            display: inline-block;
        }

        .nav-links a:hover, .nav-links span:hover {
            color: var(--primary-theme);
            transform: translateY(-2px);
        }

        /* --- HERO SECTION --- */
        header.hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
            background: radial-gradient(ellipse at top left, var(--primary-soft) 0%, #ffffff 50%, var(--secondary-soft) 100%);
            position: relative;
            transition: background 0.8s ease;
        }

        header h1 {
            font-family: var(--font-heading);
            font-size: 4rem;
            margin-bottom: 20px;
            color: var(--text-color);
            opacity: 0;
            transform: translateY(30px);
        }

        header p {
            font-size: 1.2rem;
            max-width: 600px;
            margin-bottom: 40px;
            color: #5a6c6d;
            opacity: 0;
            transform: translateY(30px);
        }

        .btn {
            display: inline-block;
            padding: 15px 35px;
            background: linear-gradient(135deg, var(--primary-theme) 0%, var(--accent-blue) 100%);
            color: var(--light-text);
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275), box-shadow 0.3s, background 0.6s ease, opacity 0.3s, color 0.6s ease; 
            opacity: 0;
            transform: translateY(30px);
            cursor: pointer;
            border: none;
            min-width: 180px; 
            text-align: center;
            vertical-align: middle;
            position: relative;
            top: 0;
            box-shadow: 0 4px 15px rgba(168, 213, 186, 0.3);
        }   

        .btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(168, 213, 186, 0.4);
            filter: brightness(1.08);
        }

        /* --- ACCORDION SECTION (The Enclosed List) --- */
        .info-section {
            padding: 100px 10%;
            background-color: #fff;
        }

        .section-title {
            text-align: center;
            font-family: var(--font-heading);
            font-size: 2.5rem;
            margin-bottom: 50px;
            background: linear-gradient(135deg, var(--primary-theme) 0%, var(--accent-blue) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            transition: all 0.6s ease;
        }

        .accordion {
            max-width: 800px;
            margin: 0 auto;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 15px 40px rgba(168, 213, 186, 0.08);
        }

        .accordion-item {
            border-bottom: 1px solid rgba(168, 213, 186, 0.2);
            background: white;
        }

        .accordion-header {
            width: 100%;
            padding: 25px;
            text-align: left;
            background: none;
            border: none;
            outline: none;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 1.2rem;
            font-family: var(--font-heading);
            font-weight: 700;
            color: var(--text-color);
            transition: background 0.3s;
        }

        .accordion-header:hover {
            background: linear-gradient(90deg, var(--primary-soft) 0%, transparent 100%);
        }

        .accordion-header::after {
            content: '+';
            font-size: 1.5rem;
            color: var(--primary-theme);
            transition: transform 0.3s, color 0.6s ease;
            flex-shrink: 0; /* RESPONSIVE: Prevent icon from shrinking */
            margin-left: 10px;
        }

        .accordion-header.active::after {
            transform: rotate(45deg);
            color: var(--accent-blue);
        }

        .accordion-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.5s cubic-bezier(0, 1, 0, 1);
            background: linear-gradient(180deg, var(--primary-soft) 0%, #ffffff 100%);
        }

        .accordion-content p {
            padding: 25px;
            color: #5a6c6d;
        }

        /* --- BLOG SECTION --- */
        .blog-section {
            padding: 100px 5%;
            background: linear-gradient(180deg, #ffffff 0%, var(--secondary-soft) 50%, var(--primary-soft) 100%);
        }

        .blog-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 40px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .blog-card {
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 20px rgba(168, 213, 186, 0.1);
            transition: transform 0.4s cubic-bezier(0.165, 0.84, 0.44, 1), box-shadow 0.4s;
            opacity: 0;
            transform: translateY(50px);
            border: 1px solid rgba(168, 213, 186, 0.15);
        }

        .blog-card:hover {
            transform: translateY(-12px);
            box-shadow: 0 20px 40px rgba(168, 213, 186, 0.2);
            border-color: var(--primary-theme);
        }

        .blog-image {
            height: 220px;
            background-color: var(--primary-soft);
            background-size: cover;
            background-position: center;
            transition: transform 0.5s ease;
            position: relative;
        }
        
        .blog-image::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(180deg, transparent 0%, rgba(168, 213, 186, 0.1) 100%);
            transition: opacity 0.3s ease;
        }
        
        .blog-card:hover .blog-image {
            transform: scale(1.05);
        }
        
        .blog-card:hover .blog-image::after {
            opacity: 0;
        }

        .blog-content {
            padding: 25px;
        }

        .blog-date {
            font-size: 0.85rem;
            color: #7EC4CF;
            margin-bottom: 10px;
            display: block;
            font-weight: 600;
        }

        .blog-title {
            font-family: var(--font-heading);
            font-size: 1.4rem;
            margin-bottom: 10px;
            color: var(--text-color);
        }

        .blog-excerpt {
            font-size: 0.95rem;
            color: #5a6c6d;
            margin-bottom: 20px;
        }

        .read-more {
            color: var(--primary-theme);
            text-decoration: none;
            font-weight: bold;
            text-transform: uppercase;
            font-size: 0.8rem;
            letter-spacing: 1px;
            transition: letter-spacing 0.3s, color 0.3s ease;
            position: relative;
            padding-bottom: 2px;
        }
        
        .read-more::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--primary-theme) 0%, var(--accent-blue) 100%);
            transition: width 0.3s ease;
        }
        
        .read-more:hover {
            letter-spacing: 2px;
            color: var(--accent-blue);
        }
        
        .read-more:hover::after {
            width: 100%;
        }

        /* --- BLOG READER STYLES --- */
        #blog-reader {
            display: none;
            padding: 120px 10%;
            min-height: 100vh;
            background: #fff;
        }

        #blog-reader.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        .back-btn {
            cursor: pointer;
            color: var(--primary-theme);
            font-weight: bold;
            display: inline-block;
            margin-bottom: 30px;
            text-transform: uppercase;
            transition: transform 0.3s, color 0.6s ease;
        }
        
        .back-btn:hover {
            transform: translateX(-5px);
            color: var(--accent-blue);
        }

        #reader-content h1 {
            font-family: var(--font-heading);
            font-size: 3rem;
            margin-bottom: 20px;
            background: linear-gradient(135deg, var(--primary-theme) 0%, var(--accent-blue) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        #reader-body {
            font-size: 1.1rem;
            line-height: 1.8;
            color: #444;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* --- CONTACT MODAL (POPUP) --- */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(45, 62, 63, 0.6);
            display: none; 
            justify-content: center;
            align-items: center;
            z-index: 2000;
            backdrop-filter: blur(8px);
            padding: 20px; /* RESPONSIVE: Prevent edge touching */
        }

        .modal-card {
            background: #fff;
            padding: 40px;
            border-radius: 25px;
            width: 90%;
            max-width: 450px;
            position: relative;
            box-shadow: 0 30px 60px rgba(168, 213, 186, 0.3);
            animation: slideDown 0.5s cubic-bezier(0.165, 0.84, 0.44, 1);
            transition: all 0.3s ease-in-out;
            border: 2px solid var(--primary-soft);
        }

        .modal-card h3 {
            font-family: var(--font-heading);
            font-size: 1.8rem;
            margin-bottom: 20px;
            background: linear-gradient(135deg, var(--primary-theme) 0%, var(--accent-blue) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            transition: all 0.6s ease;
        }

        .modal-card input {
            width: 100%;
            padding: 12px 15px;
            margin-bottom: 15px;
            border: 2px solid rgba(168, 213, 186, 0.3);
            border-radius: 10px;
            font-family: var(--font-body);
            font-size: 1rem;
            background: #fdfdfd;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
        }

        .modal-card input:focus {
            outline: none;
            border-color: var(--primary-theme);
            box-shadow: 0 0 0 3px var(--primary-soft);
        }

        .close-modal {
            position: absolute;
            top: 20px;
            right: 20px;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--primary-theme);
            transition: color 0.3s, transform 0.3s;
        }

        .close-modal:hover { 
            color: var(--accent-blue); 
            transform: rotate(90deg); 
        }

        @keyframes slideDown {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        /* --- FOOTER --- */
        footer {
            background: linear-gradient(135deg, #1a2e2e 0%, #2d3e3f 100%);
            color: #A8D5BA;
            padding: 80px 5%;
            text-align: center;
            border-top: 3px solid var(--primary-theme);
        }

        .footer-logo {
            font-family: var(--font-heading);
            font-size: 2rem;
            margin-bottom: 20px;
            display: block;
            color: #E8E5A8;
        }
        
        footer p {
            color: #7EC4CF;
        }

        /* --- UTILITIES FOR ANIMATION --- */
        .fade-in-up {
            animation: fadeInUp 1s cubic-bezier(0.22, 1, 0.36, 1) forwards;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Canvas for color extraction (hidden) */
        #color-canvas {
            display: none;
        }

        /* ========================================
           RESPONSIVE MEDIA QUERIES
           ======================================== */

        /* TABLET (768px and below) */
        @media (max-width: 768px) {
            /* Navigation becomes mobile menu */
            .hamburger {
                display: flex;
            }

            .nav-links {
                position: fixed;
                top: 0;
                right: -100%; /* Hidden off-screen */
                height: 100vh;
                width: 70%;
                max-width: 300px;
                background: rgba(255, 255, 255, 0.98);
                backdrop-filter: blur(20px);
                flex-direction: column;
                justify-content: center;
                align-items: center;
                box-shadow: -5px 0 20px rgba(0, 0, 0, 0.1);
                transition: right 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
                z-index: 999;
            }

            .nav-links.active {
                right: 0;
            }

            .nav-links a, .nav-links span {
                margin: 20px 0;
                margin-left: 0;
                font-size: 1.3rem;
            }

            .brand-name {
                font-size: 1.2rem;
            }

            #site-logo {
                height: 40px;
            }

            /* Hero Section */
            header h1 {
                font-size: 2.5rem;
            }

            header p {
                font-size: 1rem;
            }

            /* Sections */
            .info-section, .blog-section {
                padding: 60px 5%;
            }

            .section-title {
                font-size: 2rem;
            }

            /* Accordion */
            .accordion-header {
                font-size: 1rem;
                padding: 20px;
            }

            .accordion-content p {
                padding: 20px;
            }

            /* Blog Grid */
            .blog-grid {
                grid-template-columns: 1fr;
                gap: 30px;
            }

            /* Blog Reader */
            #blog-reader {
                padding: 100px 5%;
            }

            #reader-content h1 {
                font-size: 2rem;
            }

            /* Modal */
            .modal-card {
                padding: 30px;
                width: 95%;
            }

            .modal-card h3 {
                font-size: 1.5rem;
            }

            /* Footer */
            footer {
                padding: 60px 5%;
            }

            .footer-logo {
                font-size: 1.5rem;
            }
        }

        /* MOBILE (480px and below) */
        @media (max-width: 480px) {
            nav {
                padding: 15px 5%;
            }

            .brand-name {
                font-size: 1rem;
            }

            #site-logo {
                height: 35px;
            }

            header h1 {
                font-size: 2rem;
            }

            header p {
                font-size: 0.95rem;
            }

            .btn {
                padding: 12px 25px;
                min-width: 150px;
                font-size: 0.9rem;
            }

            .section-title {
                font-size: 1.8rem;
                margin-bottom: 30px;
            }

            .accordion-header {
                font-size: 0.95rem;
                padding: 18px;
            }

            .accordion-header::after {
                font-size: 1.3rem;
            }

            .accordion-content p {
                padding: 18px;
                font-size: 0.9rem;
            }

            .blog-image {
                height: 180px;
            }

            .blog-content {
                padding: 20px;
            }

            .blog-title {
                font-size: 1.2rem;
            }

            .blog-excerpt {
                font-size: 0.9rem;
            }

            #reader-content h1 {
                font-size: 1.8rem;
            }

            #reader-body {
                font-size: 1rem;
            }

            .modal-card {
                padding: 25px;
            }

            .modal-card h3 {
                font-size: 1.3rem;
            }

            .modal-card input {
                padding: 10px 12px;
                font-size: 0.95rem;
            }

            footer {
                padding: 50px 5%;
            }

            .footer-logo {
                font-size: 1.3rem;
            }

            footer p {
                font-size: 0.9rem;
            }
        }

        /* LARGE DESKTOP (1440px and above) */
        @media (min-width: 1440px) {
            header h1 {
                font-size: 5rem;
            }

            header p {
                font-size: 1.4rem;
            }

            .section-title {
                font-size: 3rem;
            }

            .blog-grid {
                max-width: 1400px;
            }
        }

        /* LANDSCAPE MOBILE FIX */
        @media (max-height: 500px) and (orientation: landscape) {
            header.hero {
                height: auto;
                min-height: 100vh;
                padding: 100px 20px 60px;
            }

            header h1 {
                font-size: 2rem;
                margin-bottom: 15px;
            }

            header p {
                font-size: 0.9rem;
                margin-bottom: 25px;
            }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo-container">
            <img src="restwellcollective.png" id="site-logo" alt="RestWellCollective Logo">
            <span class="brand-name">RestWellCollective</span>
        </div>
        
        <!-- RESPONSIVE: Hamburger Menu -->
        <div class="hamburger" onclick="toggleMenu()">
            <span></span>
            <span></span>
            <span></span>
        </div>

        <div class="nav-links" id="navLinks">
            <a href="#about" onclick="closeArticle(); closeMenu()">About</a>
            <a href="#blog" onclick="closeArticle(); closeMenu()">Blog</a>
            <span onclick="openContactModal(); closeMenu()">Contact</span>
        </div>
    </nav>

    <div id="main-site-content">
        <header class="hero">
            <h1 class="animate-on-load" style="animation-delay: 0.2s;">Rest well. Live better.</h1>
            <p class="animate-on-load" style="animation-delay: 0.4s;">We are a collective dedicated to improving mental and physical restoration through community impact.</p>
            <a href="#blog" class="btn animate-on-load" style="animation-delay: 0.6s;">Read Our Stories</a>
        </header>

        <section id="about" class="info-section">
            <h2 class="section-title scroll-trigger">Who We Are</h2>
            
            <div class="accordion scroll-trigger">
                
                <div class="accordion-item">
                    <button class="accordion-header">Our Goal</button>
                    <div class="accordion-content">
                        <p>Our primary goal is to ensure that wellness resources are accessible to everyone, regardless of their background. We strive to create a world where rest is prioritized as a fundamental human right.</p>
                    </div>
                </div>

                <div class="accordion-item">
                    <button class="accordion-header">Our Impact</button>
                    <div class="accordion-content">
                        <p>Since our inception, we have helped over 500 individuals find better sleep hygiene and mental peace through our workshops and online resources. Our metrics show a 40% increase in reported daily energy among members.</p>
                    </div>
                </div>

                <div class="accordion-item">
                    <button class="accordion-header">Our Community</button>
                    <div class="accordion-content">
                        <p>We are a diverse group of dreamers, thinkers, and doers. Our community spans across 12 countries, connected by the shared belief that a well-rested mind creates a better world.</p>
                    </div>
                </div>

                <div class="accordion-item">
                    <button class="accordion-header">Our Members</button>
                    <div class="accordion-content">
                        <p>Our members range from sleep scientists to yoga instructors, and everyday people looking for balance. Membership is open to all who wish to join the collective journey.</p>
                    </div>
                </div>

                <div class="accordion-item">
                    <button class="accordion-header">Our Initiative</button>
                    <div class="accordion-content">
                        <p>The RestWell Initiative is our flagship outreach program, partnering with local community centers to provide "Rest Zones"—safe, quiet spaces designed for decompression and mental reset.</p>
                    </div>
                </div>

            </div>
        </section>

        <section id="blog" class="blog-section">
            <h2 class="section-title scroll-trigger">Latest From The Collective</h2>
            
            <div class="blog-grid">
                
                <article class="blog-card scroll-trigger">
                    <div class="blog-image" style="background-image: url('https://images.unsplash.com/photo-1544367563-12123d896889?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80');"></div>
                    <div class="blog-content">
                        <span class="blog-date">September 26th, 2025</span>
                        <h3 class="blog-title">Infographic Flyer Distribution</h3>
                        <p class="blog-excerpt">Learn how RestWellCollective distributed fylers throughout parts and recreational areas.</p>
                        <a href="javascript:void(0)" class="read-more" onclick="openArticle('The Science of Deep Rest', 'October 15, 2025', 'On this day, we partnered with North Lake Ranch Park in Irving, TX, where families and adults gather during the day, giving us a great opportunity to share why sleep is important by handing out our flyers. During breaks like Thanksgiving and winter, when the weather wasn’t too cold, people were able to stop, read, and learn simple ways to improve their sleep health. Our team created easy-to-read infographic posters and brochures, citing sources such as the National Medical Library and Harvard studies to add credibility. We also chose this park because at night, many people from underserved communities use the rest areas for shelter, so we made sure to post our materials there as well, ensuring people of all economic backgrounds could access helpful and simple steps to improve their sleep.')">Read Article</a>
                    </div>
                </article>
                <article class="blog-card scroll-trigger">
                    <div class="blog-image" style="background-image: url('https://images.unsplash.com/photo-1511632765486-a01980e01a18?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80');"></div>
                    <div class="blog-content">
                        <span class="blog-date">October 10, 2025</span>
                        <h3 class="blog-title">Community Spotlight: Sarah's Journey</h3>
                        <p class="blog-excerpt">How one member used the RestWell Initiative to transform her work-life balance.</p>
                        <a href="javascript:void(0)" class="read-more" onclick="openArticle('Community Spotlight: Sarah\'s Journey', 'October 10, 2025', 'Sarah joined the collective back in 2023. This is her story about rest.')">Read Article</a>
                    </div>
                </article>

                <article class="blog-card scroll-trigger">
                    <div class="blog-image" style="background-image: url('https://images.unsplash.com/photo-1470252649378-9c29740c9fa8?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80');"></div>
                    <div class="blog-content">
                        <span class="blog-date">October 01, 2025</span>
                        <h3 class="blog-title">Meditation for Beginners</h3>
                        <p class="blog-excerpt">Simple techniques to quiet the mind before bed without feeling overwhelmed.</p>
                        <a href="javascript:void(0)" class="read-more" onclick="openArticle('Meditation for Beginners', 'October 01, 2025', 'Meditation doesn\'t have to be hard. Start with 5 minutes of breathing.')">Read Article</a>
                    </div>
                </article>

                <article class="blog-card scroll-trigger">
                    <div class="blog-image" style="background-image: url('https://images.unsplash.com/photo-1470252649378-9c29740c9fa8?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80');"></div>
                    <div class="blog-content">
                        <span class="blog-date">October 01, 2025</span>
                        <h3 class="blog-title">Meditation for Beginners</h3>
                        <p class="blog-excerpt">Simple techniques to quiet the mind before bed without feeling overwhelmed.</p>
                        <a href="javascript:void(0)" class="read-more" onclick="openArticle('Meditation for Beginners (Part 2)', 'October 01, 2025', 'The continuation of our guide to quiet minds.')">Read Article</a>
                    </div>
                </article>

            </div>
        </section>
    </div>

    <section id="blog-reader">
        <div class="back-btn" onclick="closeArticle()">← Back to Home</div>
        <div id="reader-content">
            <h1 id="reader-title">Post Title</h1>
            <div id="reader-meta" style="margin-bottom: 40px; color: #888;"></div>
            <div id="reader-body">
                </div>
        </div>
    </section>

    <div class="modal-overlay" id="contact-modal" onclick="closeModalOverlay(event)">
        <div class="modal-card">
            <span class="close-modal" onclick="closeContactModal()">&times;</span>
            <h3>Connect With Us</h3>
            <form id="contact-form" action="#" method="POST">
                <input type="text" name="firstname" placeholder="First Name" required>
                <input type="text" name="lastname" placeholder="Last Name" required>
                <input type="email" name="email" placeholder="Email Address" required>
                <button type="submit" class="btn" style="opacity:1; width:100%; border-radius:10px; transform: none;">Send Message</button>
            </form>
        </div>
    </div>

    <footer id="contact">
        <span class="footer-logo">RestWellCollective</span>
        <p>&copy; 2025 RestWellCollective. All rights reserved.</p>
        <p>www.restwellcollective.com</p>
    </footer>

    <canvas id="color-canvas"></canvas>

    <script>
        // --- 1. MOBILE MENU TOGGLE (RESPONSIVE) ---
        function toggleMenu() {
            const navLinks = document.getElementById('navLinks');
            const hamburger = document.querySelector('.hamburger');
            navLinks.classList.toggle('active');
            hamburger.classList.toggle('active');
        }

        function closeMenu() {
            const navLinks = document.getElementById('navLinks');
            const hamburger = document.querySelector('.hamburger');
            navLinks.classList.remove('active');
            hamburger.classList.remove('active');
        }

        // RESPONSIVE: Close menu when clicking outside
        document.addEventListener('click', function(event) {
            const navLinks = document.getElementById('navLinks');
            const hamburger = document.querySelector('.hamburger');
            const isClickInsideNav = navLinks.contains(event.target) || hamburger.contains(event.target);
            
            if (!isClickInsideNav && navLinks.classList.contains('active')) {
                closeMenu();
            }
        });

        // --- 2. ACCORDION LOGIC ---
        const accordions = document.querySelectorAll('.accordion-header');

        accordions.forEach(acc => {
            acc.addEventListener('click', function() {
                this.classList.toggle('active');
                const panel = this.nextElementSibling;
                if (panel.style.maxHeight) {
                    panel.style.maxHeight = null;
                } else {
                    panel.style.maxHeight = panel.scrollHeight + "px";
                }
            });
        });

        // --- 3. SCROLL ANIMATIONS ---
        const observerOptions = { threshold: 0.1 };
        const observer = new IntersectionObserver((entries, observer) => {
            entries.forEach(entry => {
                if(entry.isIntersecting) {
                    entry.target.classList.add('fade-in-up');
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);

        const scrollElements = document.querySelectorAll('.scroll-trigger');
        scrollElements.forEach(el => observer.observe(el));

        const loadElements = document.querySelectorAll('.animate-on-load');
        loadElements.forEach(el => el.classList.add('fade-in-up'));


        // --- 4. DYNAMIC THEME ENGINE (PRESERVED - Still functional if you want to switch logos) ---
        window.onload = function() {
            const img = document.getElementById('site-logo');
            const canvas = document.getElementById('color-canvas');
            const ctx = canvas.getContext('2d');

            if (img.complete) {
                img.decode().then(detectColor).catch(detectColor);
            } else {
                img.addEventListener('load', () => {
                    img.decode().then(detectColor).catch(detectColor);
                });
            }


            function applyThemeSafe(r, g, b) {
                const primary = `rgb(${r}, ${g}, ${b})`;
                const soft = `rgba(${r}, ${g}, ${b}, 0.12)`;

                document.documentElement.style.setProperty('--primary-theme', primary);
                document.documentElement.style.setProperty('--primary-soft', soft);

                const luminance = (0.299*r + 0.587*g + 0.114*b) / 255;
                document.documentElement.style.setProperty(
                    '--light-text',
                    luminance > 0.6 ? '#222' : '#ffffff'
                );
                
                const focusShadow = `rgba(${r}, ${g}, ${b}, 0.1)`;
                document.documentElement.style.setProperty('--focus-shadow', focusShadow);
                
                const styleTag = document.createElement('style');
                styleTag.id = 'dynamic-focus-style';
                const existingStyle = document.getElementById('dynamic-focus-style');
                if (existingStyle) existingStyle.remove();
                
                styleTag.textContent = `
                    .modal-card input:focus {
                        box-shadow: 0 0 0 3px ${focusShadow} !important;
                    }
                `;
                document.head.appendChild(styleTag);
            }


            function detectColor() {
                try {
                    canvas.width = img.naturalWidth;
                    canvas.height = img.naturalHeight;
                    ctx.drawImage(img, 0, 0);

                    const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
                    const data = imageData.data;

                    let colors = [];
                    
                    for (let i = 0; i < data.length; i += 20) {
                        const r = data[i];
                        const g = data[i + 1];
                        const b = data[i + 2];
                        const a = data[i + 3];

                        if (a < 200) continue;

                        const brightness = (r + g + b) / 3;
                        const saturation = Math.max(r, g, b) - Math.min(r, g, b);

                        if (brightness > 240 || brightness < 20 || saturation < 20) continue;

                        colors.push({ r, g, b, saturation, brightness });
                    }

                    if (!colors.length) return;

                    colors.sort((a, b) => {
                        const scoreA = a.saturation * 0.7 + (150 - Math.abs(a.brightness - 150)) * 0.3;
                        const scoreB = b.saturation * 0.7 + (150 - Math.abs(b.brightness - 150)) * 0.3;
                        return scoreB - scoreA;
                    });
                    
                    let { r, g, b } = colors[0];

                    const targetBrightness = 140;
                    const currentBrightness = (r + g + b) / 3;
                    const brightnessRatio = targetBrightness / currentBrightness;
                    
                    r = Math.min(220, Math.max(40, Math.round(r * brightnessRatio)));
                    g = Math.min(220, Math.max(40, Math.round(g * brightnessRatio)));
                    b = Math.min(220, Math.max(40, Math.round(b * brightnessRatio)));

                    const primary = `rgb(${r}, ${g}, ${b})`;
                    document.documentElement.style.setProperty('--primary-theme', primary);
                    applyThemeSafe(r, g, b);

                    const luminance = (0.299*r + 0.587*g + 0.114*b) / 255;
                    const textColor = luminance > 0.6 ? '#222' : '#ffffff';

                    document.documentElement.style.setProperty('--text-color', '#333');
                    document.documentElement.style.setProperty('--light-text', textColor);
                    
                    console.log(`🎨 Theme color detected: rgb(${r}, ${g}, ${b})`);

                } catch (e) {
                    console.log("Theme color fallback active - using RestWellCollective brand colors.");
                    applyThemeSafe(168, 213, 186);
                }
            }

        };
        
        // --- 5. BLOG CONTENT LOGIC ---
        function openArticle(title, date, content) {
            document.getElementById('main-site-content').style.display = 'none';
            document.getElementById('reader-title').innerText = title;
            document.getElementById('reader-meta').innerText = "Published on " + date;
            document.getElementById('reader-body').innerHTML = `<p>${content}</p>`;
            const reader = document.getElementById('blog-reader');
            reader.classList.add('active');
            window.scrollTo(0, 0);
            closeMenu(); // RESPONSIVE: Close mobile menu when opening article
        }

        function closeArticle() {
            document.getElementById('main-site-content').style.display = 'block';
            document.getElementById('blog-reader').classList.remove('active');
            window.scrollTo(0, 0);
        }

        // --- 6. CONTACT MODAL LOGIC (ADD-ON) ---
        function openContactModal() {
            document.getElementById('contact-modal').style.display = 'flex';
            document.body.style.overflow = 'hidden'; // RESPONSIVE: Prevent scrolling when modal is open
        }

        function closeContactModal() {
            document.getElementById('contact-modal').style.display = 'none';
            document.body.style.overflow = 'auto'; // RESPONSIVE: Re-enable scrolling
        }

        // RESPONSIVE: Close modal when clicking outside the card
        function closeModalOverlay(event) {
            if (event.target === document.getElementById('contact-modal')) {
                closeContactModal();
            }
        }

        // Handle Form Submission (Polished & Smooth)
        document.getElementById('contact-form').addEventListener('submit', function(e) {
            e.preventDefault(); 
            const btn = this.querySelector('button');
            
            const currentWidth = btn.offsetWidth;
            const currentHeight = btn.offsetHeight;
            btn.style.width = currentWidth + 'px';
            btn.style.height = currentHeight + 'px';
            
            btn.style.pointerEvents = "none";
            btn.style.opacity = "0.7";
            
            setTimeout(() => {
                btn.innerText = "Success!";
                btn.style.background = "linear-gradient(135deg, #2ecc71 0%, #27ae60 100%)";
                btn.style.opacity = "1";
                
                setTimeout(() => {
                    closeContactModal();
                    
                    setTimeout(() => {
                        btn.innerText = "Send Message";
                        btn.style.background = ""; 
                        btn.style.width = "";
                        btn.style.height = "";
                        btn.style.pointerEvents = "auto";
                        this.reset();
                    }, 400); 
                }, 1500);
            }, 200);
        });

        // RESPONSIVE: Prevent accordion content from jumping when window resizes
        window.addEventListener('resize', function() {
            document.querySelectorAll('.accordion-content').forEach(panel => {
                if (panel.style.maxHeight) {
                    panel.style.maxHeight = panel.scrollHeight + "px";
                }
            });
        });
    </script>
</body>
</html>
