<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>Aura Care Collective | Holistic Disability & Wellness Support</title>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300..700&display=swap" rel="stylesheet">
    <style>
        /* ----- RESET & VARIABLES (light professional palette) ----- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        :root {
            --primary-bg: #F7FBFF;
            --secondary-bg: #F0FFF0;
            --primary-accent: #95AF9E;
            --secondary-accent: #CDB4CE;
            --text-dark: #2e3a35;
            --white: #ffffff;
            --shadow-soft: 0 15px 30px -12px rgba(0, 0, 0, 0.06);
            --shadow-hover: 0 25px 40px -14px rgba(51, 51, 51, 0.12);
            --radius-card: 28px;
            --transition: all 0.35s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        body {
            font-family: 'Inter', sans-serif;
            background: var(--primary-bg);
            color: var(--text-dark);
            line-height: 1.6;
            overflow-x: hidden;
        }
        h1, h2, h3 {
            font-weight: 600;
            letter-spacing: -0.02em;
        }
        h2 { font-size: 2.5rem; margin-bottom: 1.2rem; }
        .container {
            max-width: 1300px;
            margin: 0 auto;
            padding: 0 2rem;
        }
        section { padding: 6rem 0; }
        @media (max-width: 768px) {
            h2 { font-size: 2rem; }
            section { padding: 4rem 0; }
        }

        /* scroll animations */
        .fade-up {
            opacity: 0;
            transform: translateY(28px);
            transition: opacity 0.8s ease, transform 0.8s ease;
        }
        .fade-up.visible {
            opacity: 1;
            transform: translateY(0);
        }
        @media (prefers-reduced-motion: reduce) {
            .fade-up { transition: none; transform: none; opacity: 1; }
        }

        /* buttons */
        .btn {
            display: inline-block;
            padding: 0.9rem 2.3rem;
            border-radius: 60px;
            font-weight: 600;
            text-decoration: none;
            transition: var(--transition);
            border: 1.5px solid transparent;
            cursor: pointer;
            background: transparent;
            font-size: 1rem;
        }
        .btn-primary {
            background: var(--primary-accent);
            color: white;
            box-shadow: 0 8px 18px rgba(149, 175, 158, 0.2);
        }
        .btn-primary:hover {
            background: #7e9a89;
            transform: translateY(-4px);
            box-shadow: 0 15px 25px rgba(149, 175, 158, 0.35);
        }
        .btn-outline {
            border-color: var(--primary-accent);
            color: var(--primary-accent);
        }
        .btn-outline:hover {
            background: var(--primary-accent);
            color: white;
            transform: translateY(-3px);
        }
        .btn-light {
            background: white;
            color: var(--text-dark);
            box-shadow: var(--shadow-soft);
        }

        /* header */
        header {
            position: fixed;
            top: 0; left: 0; width: 100%;
            z-index: 1000;
            background: rgba(247, 251, 255, 0.8);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(149,175,158,0.2);
        }
        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2.5rem;
            max-width: 1400px;
            margin: 0 auto;
        }
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--text-dark);
        }
        .logo span { color: var(--primary-accent); font-weight: 300; }
        .nav-links {
            display: flex;
            gap: 2.8rem;
            align-items: center;
        }
        .nav-links a {
            text-decoration: none;
            color: var(--text-dark);
            font-weight: 500;
            transition: color 0.2s;
        }
        .nav-links a:hover { color: var(--primary-accent); }
        .mobile-btn {
            display: none;
            background: none;
            border: none;
            font-size: 1.8rem;
            color: var(--text-dark);
            cursor: pointer;
        }
        @media (max-width: 900px) {
            .nav-links {
                position: fixed;
                top: 80px; right: -100%;
                flex-direction: column;
                background: rgba(255,255,255,0.95);
                backdrop-filter: blur(20px);
                width: 280px;
                padding: 2.5rem;
                border-radius: 32px 0 0 32px;
                box-shadow: -5px 20px 30px rgba(0,0,0,0.05);
                transition: right 0.4s;
                gap: 2rem;
                align-items: flex-start;
            }
            .nav-links.active { right: 0; }
            .mobile-btn { display: block; }
        }

        /* hero video */
        .hero {
            position: relative;
            min-height: 90vh;
            display: flex;
            align-items: center;
            padding: 8rem 0 4rem;
            overflow: hidden;
        }
        .hero-video {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            object-fit: cover;
            z-index: -2;
            pointer-events: none;
        }
        .hero-overlay {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(120deg, rgba(247,251,255,0.7) 0%, rgba(240,255,240,0.65) 100%);
            z-index: -1;
        }
        .hero-content { max-width: 720px; }
        .hero h1 { font-size: 4rem; font-weight: 700; line-height: 1.15; margin-bottom: 1.5rem; }
        .hero p { font-size: 1.2rem; margin-bottom: 2.5rem; color: #3f554a; }

        /* cards */
        .services-grid, .wellness-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }
        .service-card {
            background: white;
            padding: 2.5rem 1.8rem;
            border-radius: var(--radius-card);
            box-shadow: var(--shadow-soft);
            transition: var(--transition);
            border: 1px solid rgba(149,175,158,0.15);
            text-align: center;
        }
        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-hover);
            border-color: var(--primary-accent);
        }
        .service-icon {
            font-size: 2.8rem;
            color: var(--primary-accent);
            margin-bottom: 1.5rem;
        }

        .step-card {
            background: var(--secondary-bg);
            padding: 2.5rem 2rem;
            border-radius: 40px;
            flex: 1 1 240px;
            max-width: 300px;
            box-shadow: var(--shadow-soft);
            transition: var(--transition);
            text-align: center;
        }
        .step-number {
            background: var(--secondary-accent);
            color: white;
            width: 60px; height: 60px;
            font-size: 1.8rem; font-weight: 700;
            display: flex; align-items: center; justify-content: center;
            border-radius: 30px;
            margin: 0 auto 1.5rem;
        }

        .value-item {
            background: white;
            padding: 2rem 1.5rem;
            border-radius: 28px;
            box-shadow: var(--shadow-soft);
            text-align: center;
            border-bottom: 4px solid transparent;
            transition: var(--transition);
        }
        .value-item:hover {
            border-bottom-color: var(--primary-accent);
            transform: translateY(-5px);
        }

        .testimonial-card {
            background: white;
            padding: 2.2rem;
            border-radius: 28px;
            box-shadow: var(--shadow-soft);
        }

        /* contact / footer */
        .contact-section {
            background: var(--secondary-bg);
            border-radius: 60px 60px 0 0;
        }
        .contact-flex {
            display: flex; flex-wrap: wrap; gap: 3rem;
        }
        .input-group input, .input-group textarea {
            width: 100%; padding: 1rem 1.5rem;
            border: 1.5px solid #dde9e1;
            border-radius: 50px;
            background: white;
            font-family: inherit;
        }
        .input-group textarea { border-radius: 30px; resize: vertical; }
        .input-group input:focus, .input-group textarea:focus {
            outline: none;
            border-color: var(--primary-accent);
            box-shadow: 0 0 0 4px rgba(149,175,158,0.15);
        }
        .footer-bottom {
            text-align: center; padding-top: 2.5rem; margin-top: 2rem;
            border-top: 1px solid rgba(149,175,158,0.3);
        }

        .section-subtitle {
            color: var(--primary-accent);
            text-transform: uppercase;
            letter-spacing: 2px;
            font-weight: 600;
            font-size: 0.9rem;
        }

        @media (max-width: 600px) {
            .container { padding: 0 1.5rem; }
        }
        html { scroll-behavior: smooth; }
    </style>
</head>
<body>

<header id="header">
    <div class="header-container">
        <div class="logo">Aura Care <span>Collective</span></div>
        <button class="mobile-btn" id="mobileBtn" aria-label="Menu"><i class="fas fa-bars"></i></button>
        <nav class="nav-links" id="navLinks">
            <a href="#home">Home</a>
            <a href="#services">Care</a>
            <a href="#wellness">Wellness</a>
            <a href="#journey">Your Journey</a>
            <a href="#contact">Contact</a>
            <a href="#contact" class="btn btn-outline" style="padding:0.6rem 1.8rem;">Get started</a>
        </nav>
    </div>
</header>

<main>
    <!-- Hero with motion video -->
    <section id="home" class="hero">
        <video class="hero-video" autoplay muted loop playsinline poster="https://images.pexels.com/photos/7551611/pexels-photo-7551611.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2">
            <source src="https://assets.mixkit.co/videos/preview/mixkit-soft-floating-particles-on-a-light-background-45116-large.mp4" type="video/mp4">
        </video>
        <div class="hero-overlay"></div>
        <div class="container hero-content fade-up visible">
            <span class="section-subtitle">Compassion · Growth · Independence</span>
            <h1>Your journey, <br>elevated with care.</h1>
            <p>Combining disability support with holistic wellness — because every person deserves to thrive, not just cope.</p>
            <div class="hero-buttons" style="display: flex; gap: 1rem; flex-wrap: wrap;">
                <a href="#contact" class="btn btn-primary">Talk to a coordinator <i class="fas fa-arrow-right" style="margin-left: 8px;"></i></a>
                <a href="#services" class="btn btn-light">Explore support <i class="fas fa-heart" style="margin-left: 6px; color: var(--primary-accent);"></i></a>
            </div>
        </div>
    </section>

    <!-- Blended intro: Care + Raise Journey -->
    <section id="about">
        <div class="container">
            <div class="fade-up">
                <span class="section-subtitle">More than support — a partnership</span>
                <h2>Where care meets personal growth</h2>
            </div>
            <div style="display: flex; gap: 3rem; flex-wrap: wrap;">
                <div style="flex: 1.5;" class="fade-up">
                    <p style="font-size: 1.2rem; margin-bottom: 1.5rem;">Aura Care Collective was born from two essential truths: disability support should be empowering, and everyone deserves tools to rise.</p>
                    <p>We blend the best of NDIS care coordination, daily living assistance, and community inclusion with evidence‑informed wellness coaching, mental health navigation, and personal development. Whether you need help at home or guidance to rediscover your purpose — we walk beside you.</p>
                </div>
                <div style="flex: 1; background: var(--secondary-bg); border-radius: 40px; padding: 2rem;" class="fade-up">
                    <i class="fas fa-seedling" style="font-size: 2.2rem; color: var(--primary-accent); margin-bottom: 0.8rem;"></i>
                    <h3 style="margin-bottom: 0.8rem;">The Raise Journey™</h3>
                    <p>Inspired by personal transformation, our Raise approach helps you build confidence, set meaningful goals, and navigate life transitions — all while receiving exceptional care.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Combined Services: Disability Support + Wellness & Coaching -->
    <section id="services" style="background: white; border-radius: 60px 60px 0 0;">
        <div class="container">
            <div class="fade-up">
                <span class="section-subtitle">Holistic support spectrum</span>
                <h2>Disability care & beyond</h2>
            </div>
            <div class="services-grid">
                <div class="service-card fade-up">
                    <div class="service-icon"><i class="fas fa-home"></i></div>
                    <h3>In-Home & Personal Care</h3>
                    <p>Assistance with daily tasks, medication, and mobility — respectful, reliable support.</p>
                </div>
                <div class="service-card fade-up">
                    <div class="service-icon"><i class="fas fa-users"></i></div>
                    <h3>Community Participation</h3>
                    <p>Social activities, skill‑building, and meaningful connections in your local area.</p>
                </div>
                <div class="service-card fade-up">
                    <div class="service-icon"><i class="fas fa-compass"></i></div>
                    <h3>NDIS Navigation</h3>
                    <p>Plan management, support coordination, and advocacy to maximise your funding.</p>
                </div>
                <div class="service-card fade-up">
                    <div class="service-icon"><i class="fas fa-brain"></i></div>
                    <h3>Mental Wellness Coaching</h3>
                    <p>One‑on‑one sessions to manage stress, build resilience, and cultivate a positive mindset.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Additional Wellness & Raise Journey offerings (the missing piece) -->
    <section id="wellness" style="background: var(--primary-bg);">
        <div class="container">
            <div class="fade-up">
                <span class="section-subtitle">Beyond basics — thrive</span>
                <h2>Wellness & life elevation</h2>
            </div>
            <div class="wellness-grid">
                <div class="service-card fade-up">
                    <div class="service-icon"><i class="fas fa-spa"></i></div>
                    <h3>Mindfulness & Resilience</h3>
                    <p>Guided practices, breathing techniques, and emotional regulation tools.</p>
                </div>
                <div class="service-card fade-up">
                    <div class="service-icon"><i class="fas fa-person-walking"></i></div>
                    <h3>Goal & Habit Coaching</h3>
                    <p>Set realistic goals and build sustainable routines for independence and joy.</p>
                </div>
                <div class="service-card fade-up">
                    <div class="service-icon"><i class="fas fa-people-group"></i></div>
                    <h3>Peer Connection Groups</h3>
                    <p>Facilitated small groups focused on shared experiences and mutual growth.</p>
                </div>
                <div class="service-card fade-up">
                    <div class="service-icon"><i class="fas fa-book-open"></i></div>
                    <h3>Workshops & Events</h3>
                    <p>From nutrition to self‑advocacy — practical workshops for participants and families.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- The "Raise Journey" process (unique from other site) -->
    <section id="journey" style="background: var(--secondary-bg);">
        <div class="container">
            <div class="fade-up">
                <span class="section-subtitle">Your personalised pathway</span>
                <h2>The Raise Journey™ framework</h2>
                <p style="max-width: 700px; margin-bottom: 3rem;">A proven 4‑step method that blends care coordination with personal development.</p>
            </div>
            <div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 2rem;">
                <div class="step-card fade-up">
                    <div class="step-number">R</div>
                    <h3>Reflect</h3>
                    <p>We listen deeply — your story, strengths, and vision for a fulfilling life.</p>
                </div>
                <div class="step-card fade-up">
                    <div class="step-number">A</div>
                    <h3>Align</h3>
                    <p>Co‑design a plan that integrates care services and personal growth goals.</p>
                </div>
                <div class="step-card fade-up">
                    <div class="step-number">I</div>
                    <h3>Ignite</h3>
                    <p>Activate support, coaching, and community connections that energise you.</p>
                </div>
                <div class="step-card fade-up">
                    <div class="step-number">S</div>
                    <h3>Sustain</h3>
                    <p>Ongoing check‑ins, adjustments, and celebrations of every milestone.</p>
                </div>
                <div class="step-card fade-up">
                    <div class="step-number">E</div>
                    <h3>Evolve</h3>
                    <p>As you grow, your support evolves — because life isn't static.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Values + testimonials combo -->
    <section style="background: white;">
        <div class="container">
            <div class="fade-up">
                <span class="section-subtitle">Our foundation</span>
                <h2>Values we live by</h2>
            </div>
            <div class="services-grid" style="margin-bottom: 4rem;">
                <div class="value-item fade-up"><i class="fas fa-hand-holding-heart value-icon"></i><h3>Compassion</h3><p>Kindness in every interaction.</p></div>
                <div class="value-item fade-up"><i class="fas fa-sun value-icon"></i><h3>Empowerment</h3><p>Your voice, your choice.</p></div>
                <div class="value-item fade-up"><i class="fas fa-shield-alt value-icon"></i><h3>Integrity</h3><p>Transparent and reliable.</p></div>
                <div class="value-item fade-up"><i class="fas fa-arrows-spin value-icon"></i><h3>Growth</h3><p>Always learning, evolving.</p></div>
            </div>

            <div class="fade-up">
                <span class="section-subtitle">Real stories</span>
                <h2>Hear from our community</h2>
            </div>
            <div class="services-grid">
                <div class="testimonial-card fade-up">
                    <i class="fas fa-quote-left" style="color: var(--secondary-accent); opacity: 0.5; margin-bottom: 1rem;"></i>
                    <p class="testimonial-text">“Aura Care helped me navigate NDIS AND find a wellness coach. I now volunteer and feel part of something bigger.”</p>
                    <p class="testimonial-author">— Elena R.</p>
                </div>
                <div class="testimonial-card fade-up">
                    <i class="fas fa-quote-left" style="color: var(--secondary-accent); opacity: 0.5;"></i>
                    <p>“The Raise Journey gave me a framework to rebuild my confidence after my accident. I’m not just surviving, I’m living.”</p>
                    <p class="testimonial-author">— Marcus T.</p>
                </div>
                <div class="testimonial-card fade-up">
                    <i class="fas fa-quote-left" style="color: var(--secondary-accent); opacity: 0.5;"></i>
                    <p>“Their carers are like family, and the wellness workshops are the highlight of my week.”</p>
                    <p class="testimonial-author">— Priya K.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact / Footer -->
    <section id="contact" class="contact-section">
        <div class="container">
            <div class="fade-up">
                <span class="section-subtitle">Begin your Raise Journey</span>
                <h2>Let’s connect and create a plan</h2>
            </div>
            <div class="contact-flex">
                <div class="fade-up" style="flex:1;">
                    <h3><i class="fas fa-comment-dots" style="color:var(--primary-accent); margin-right:10px;"></i> Talk to us</h3>
                    <p style="margin: 1.2rem 0 2rem;">Whether you're exploring disability support or personal growth — we're ready to listen.</p>
                    <p><i class="fas fa-phone-alt" style="color:var(--primary-accent);"></i> 1800 232 762</p>
                    <p><i class="fas fa-envelope"></i> hello@auracarecollective.com</p>
                    <p><i class="fas fa-map-pin"></i> Melbourne / Sydney / Online</p>
                    <div style="margin-top: 2rem;">
                        <a href="#" style="color:var(--primary-accent); margin-right:20px;"><i class="fab fa-facebook fa-xl"></i></a>
                        <a href="#" style="color:var(--primary-accent); margin-right:20px;"><i class="fab fa-instagram fa-xl"></i></a>
                        <a href="#" style="color:var(--primary-accent);"><i class="fab fa-linkedin fa-xl"></i></a>
                    </div>
                </div>
                <div class="fade-up" style="flex:1.2;">
                    <form action="#" method="post">
                        <div class="input-group"><input type="text" placeholder="Full name" required></div>
                        <div class="input-group"><input type="email" placeholder="Email" required></div>
                        <div class="input-group"><textarea rows="3" placeholder="Tell us a bit about what you're looking for..."></textarea></div>
                        <button class="btn btn-primary" style="border:none;">Send message <i class="fas fa-paper-plane"></i></button>
                    </form>
                </div>
            </div>
            <div class="footer-bottom">
                <p>© 2026 Aura Care Collective — ABN 12 345 678 901 <br> Compassion • Empowerment • Growth • Integrity</p>
            </div>
        </div>
    </section>
</main>

<script>
    (function(){
        // Intersection Observer for fade animations
        const fadeEls = document.querySelectorAll('.fade-up');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => { if(entry.isIntersecting) entry.target.classList.add('visible'); });
        }, { threshold: 0.12, rootMargin: '0px 0px -20px 0px' });
        fadeEls.forEach(el => observer.observe(el));
        document.querySelectorAll('.hero .fade-up').forEach(el => el.classList.add('visible'));

        // Mobile menu
        const menuBtn = document.getElementById('mobileBtn');
        const nav = document.getElementById('navLinks');
        menuBtn.addEventListener('click', () => {
            nav.classList.toggle('active');
            const icon = menuBtn.querySelector('i');
            icon.classList.toggle('fa-bars');
            icon.classList.toggle('fa-times');
        });
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', (e) => {
                const href = link.getAttribute('href');
                if(href && href.startsWith('#')) {
                    e.preventDefault();
                    document.querySelector(href)?.scrollIntoView({ behavior: 'smooth' });
                }
                nav.classList.remove('active');
                menuBtn.querySelector('i')?.classList.replace('fa-times','fa-bars');
            });
        });

        // header background
        const header = document.getElementById('header');
        window.addEventListener('scroll', () => {
            header.style.background = window.scrollY > 40 ? 'rgba(247,251,255,0.92)' : 'rgba(247,251,255,0.8)';
        });
    })();
</script>
<style>
    i { margin-right: 6px; }
    .value-icon { font-size: 2.4rem; color: var(--primary-accent); margin-bottom: 0.8rem; }
    .testimonial-author { font-weight: 600; color: var(--primary-accent); margin-top: 1rem; }
    .btn i { margin-left: 6px; margin-right: 0; }
    @media (max-width: 480px) { .hero h1 { font-size: 2.5rem; } }
</style>
</body>
</html>
