<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sumit - Portfolio</title>
    <meta name="description" content="Frontend Designer Portfolio showcasing projects and skills">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://unpkg.com/aos@next/dist/aos.css" />
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css">
    <link rel="icon" type="image/png" href="favicon.png">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Poppins', sans-serif;
            line-height: 1.6;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
            color: #e2e8f0;
            overflow-x: hidden;
        }

        /* Preloader */
        .preloader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #0f172a;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            transition: opacity 0.5s ease;
        }

        .preloader.hidden {
            opacity: 0;
            pointer-events: none;
        }

        .loader {
            border: 4px solid #334155;
            border-top: 4px solid #8b5cf6;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Section Styling */
        section {
            padding: 5rem 1rem;
        }

        .section-title {
            font-size: 2.5rem;
            font-weight: 700;
            text-align: center;
            margin-bottom: 3rem;
            color: #e2e8f0;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -12px;
            left: 50%;
            transform: translateX(-50%);
            width: 64px;
            height: 4px;
            background: #8b5cf6;
            border-radius: 2px;
        }

        /* Card Styling */
        .card {
            background: #1e293b;
            border: 1px solid #334155;
            border-radius: 12px;
            padding: 1.5rem;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(139, 92, 246, 0.3);
        }

        /* Navigation */
        .navbar {
            transition: all 0.3s ease;
            background: rgba(15, 23, 42, 0.95);
            border-bottom: 1px solid #334155;
        }

        .navbar.scrolled {
            background: rgba(15, 23, 42, 0.98) !important;
            box-shadow: 0 4px 25px rgba(0, 0, 0, 0.3);
        }

        .nav-link {
            position: relative;
            padding-bottom: 0.5rem;
            transition: all 0.3s ease;
            color: #94a3b8;
        }

        .nav-link:hover {
            color: #8b5cf6;
        }

        .nav-link::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: #8b5cf6;
            transition: width 0.3s ease;
        }

        .nav-link:hover::after {
            width: 100%;
        }

        .nav-link.active {
            color: #8b5cf6;
            font-weight: 600;
        }

        .nav-link.active .active-dot {
            opacity: 1;
            box-shadow: 0 0 8px rgba(139, 92, 246, 0.5);
        }

        /* Home Section */
        .home-section {
            position: relative;
            min-height: 100vh;
            display: flex;
            align-items: center;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
        }

        .home-content h1 {
            font-size: 3.5rem;
            font-weight: 800;
            color: #e2e8f0;
            line-height: 1.2;
            animation: fadeInUp 1s ease;
        }

        .home-content h2 {
            font-size: 1.75rem;
            font-weight: 600;
            color: #8b5cf6;
            margin-top: 1rem;
        }

        .home-content p {
            color: #94a3b8;
            margin-top: 1.5rem;
            max-width: 600px;
            font-size: 1.1rem;
        }

        .cta-buttons .btn-primary {
            background: #8b5cf6;
            color: white;
            transition: all 0.3s ease;
        }

        .cta-buttons .btn-primary:hover {
            background: #7c3aed;
            transform: scale(1.05);
            box-shadow: 0 10px 20px rgba(139, 92, 246, 0.3);
        }

        .cta-buttons .btn-outline {
            border: 2px solid #8b5cf6;
            color: #8b5cf6;
            transition: all 0.3s ease;
        }

        .cta-buttons .btn-outline:hover {
            background: #8b5cf6;
            color: white;
            transform: scale(1.05);
            box-shadow: 0 10px 20px rgba(139, 92, 246, 0.3);
        }

        .home-illustration img {
            border-radius: 1rem;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.3);
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        /* About Section */
        .about-content {
            background: #1e293b;
            border-radius: 1rem;
            padding: 2rem;
        }

        .about-content p {
            color: #94a3b8;
        }

        .profile-image {
            border: 4px solid #334155;
            transition: all 0.3s ease;
        }

        .profile-image:hover {
            border-color: #8b5cf6;
            transform: scale(1.05);
        }

        /* Skills Section */
        .progress-bar {
            height: 8px;
            background: #334155;
            border-radius: 4px;
            overflow: hidden;
        }

        .progress-bar .progress {
            height: 100%;
            background: #8b5cf6;
            border-radius: 4px;
            transition: width 1s ease-in-out;
        }

        /* Projects Section */
        .project-card {
            transition: all 0.3s ease;
        }

        .project-card:hover {
            transform: translateY(-5px);
        }

        .project-image {
            height: 200px;
            overflow: hidden;
            border-radius: 0.5rem;
        }

        .project-image img {
            transition: transform 0.5s ease;
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .project-card:hover .project-image img {
            transform: scale(1.1);
        }

        .project-tech span {
            background: #334155;
            color: #8b5cf6;
            font-size: 0.75rem;
            font-weight: 500;
            padding: 0.25rem 0.75rem;
            border-radius: 9999px;
        }

        /* Experience Section */
        .experience-timeline {
            position: relative;
            padding-left: 2rem;
        }

        .experience-timeline::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            height: 100%;
            width: 2px;
            background: #334155;
        }

        .experience-item {
            position: relative;
            padding-bottom: 2rem;
        }

        .experience-item::before {
            content: '';
            position: absolute;
            left: -2rem;
            top: 0;
            width: 1rem;
            height: 1rem;
            border-radius: 50%;
            background: #8b5cf6;
            transform: translateX(-50%);
        }

        /* Contact Section */
        .contact-form input,
        .contact-form textarea {
            width: 100%;
            padding: 0.75rem 1rem;
            border: 1px solid #334155;
            border-radius: 0.5rem;
            background: #0f172a;
            color: #e2e8f0;
            transition: all 0.3s ease;
        }

        .contact-form input:focus,
        .contact-form textarea:focus {
            border-color: #8b5cf6;
            box-shadow: 0 0 0 3px rgba(139, 92, 246, 0.2);
            outline: none;
        }

        .contact-info .contact-item {
            padding: 1rem;
            border-radius: 0.5rem;
            transition: all 0.3s ease;
        }

        .contact-info .contact-item:hover {
            background: #334155;
        }

        .contact-info .contact-item i {
            background: #334155;
            color: #8b5cf6;
            width: 3rem;
            height: 3rem;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            font-size: 1.25rem;
        }

        .social-links a {
            width: 3rem;
            height: 3rem;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            background: #334155;
            color: #8b5cf6;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            background: #8b5cf6;
            color: white;
            transform: translateY(-3px);
        }

        /* Footer */
        .footer {
            background: #0f172a;
            border-top: 1px solid #334155;
        }

        .footer-links a {
            color: #94a3b8;
            transition: color 0.3s ease;
        }

        .footer-links a:hover {
            color: #8b5cf6;
        }

        /* Scroll to Top */
        .scroll-top-btn {
            width: 3rem;
            height: 3rem;
            background: #8b5cf6;
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3);
        }

        .scroll-top-btn.active {
            opacity: 1;
            visibility: visible;
        }

        .scroll-top-btn:hover {
            background: #7c3aed;
            transform: translateY(-3px);
        }

        /* Modal */
        #project-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
        }

        #project-modal.active {
            opacity: 1;
            visibility: visible;
        }

        .modal-content {
            background: #1e293b;
            border-radius: 1rem;
            width: 90%;
            max-width: 800px;
            padding: 2rem;
            transform: translateY(20px);
            transition: all 0.3s ease;
        }

        #project-modal.active .modal-content {
            transform: translateY(0);
        }

        /* Animations */
        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Responsive Design */
        @media (max-width: 1024px) {
            .home-content h1 {
                font-size: 2.75rem;
            }
            
            .home-content h2 {
                font-size: 1.5rem;
            }
        }

        @media (max-width: 768px) {
            .nav-menu {
                position: fixed;
                top: 0;
                right: -100%;
                width: 80%;
                max-width: 300px;
                height: 100vh;
                background: #1e293b;
                box-shadow: -5px 0 15px rgba(0, 0, 0, 0.3);
                flex-direction: column;
                padding: 2rem;
                transition: right 0.3s ease;
                z-index: 100;
            }

            .nav-menu.active {
                right: 0;
            }

            .nav-toggle {
                display: flex;
                flex-direction: column;
                justify-content: space-between;
                width: 2rem;
                height: 1.5rem;
                position: relative;
                z-index: 101;
            }

            .nav-toggle span {
                display: block;
                width: 100%;
                height: 2px;
                background: #8b5cf6;
                transition: all 0.3s ease;
            }

            .nav-toggle.active span:nth-child(1) {
                transform: rotate(45deg) translate(5px, 5px);
            }

            .nav-toggle.active span:nth-child(2) {
                opacity: 0;
            }

            .nav-toggle.active span:nth-child(3) {
                transform: rotate(-45deg) translate(5px, -5px);
            }

            .home-content h1 {
                font-size: 2.5rem;
            }
            
            .home-content h2 {
                font-size: 1.25rem;
            }

            .section-title {
                font-size: 2rem;
            }

            .about-content {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .profile-image {
                margin: 0 auto;
            }
        }

        @media (max-width: 640px) {
            .home-content h1 {
                font-size: 2rem;
            }
            
            .cta-buttons {
                flex-direction: column;
                gap: 1rem;
            }
            
            .cta-buttons a {
                width: 100%;
                text-align: center;
            }
        }
    </style>
</head>
<body>
    <!-- Preloader -->
    <div class="preloader">
        <div class="loader"></div>
    </div>

    <!-- Navigation -->
    <nav class="navbar fixed top-0 w-full py-4 z-40 bg-opacity-95 backdrop-filter backdrop-blur-xl shadow-sm">
        <div class="container mx-auto flex justify-between items-center px-6">
            <div class="nav-brand text-2xl font-bold text-purple-500">Sumit</div>
            <div class="nav-toggle flex flex-col space-y-1.5 cursor-pointer p-2">
                <span class="block w-8 h-0.5 bg-purple-500 rounded-full transition-all duration-300"></span>
                <span class="block w-8 h-0.5 bg-purple-500 rounded-full transition-all duration-300"></span>
                <span class="block w-8 h-0.5 bg-purple-500 rounded-full transition-all duration-300"></span>
            </div>
            <ul class="nav-menu hidden md:flex space-x-8">
                <li class="relative"><a href="#home" class="nav-link text-lg font-medium active">Home<span class="active-dot absolute -bottom-1 left-1/2 transform -translate-x-1/2 w-2 h-2 bg-purple-500 rounded-full opacity-0 transition-opacity duration-300"></span></a></li>
                <li class="relative"><a href="#about" class="nav-link text-lg font-medium">About<span class="active-dot absolute -bottom-1 left-1/2 transform -translate-x-1/2 w-2 h-2 bg-purple-500 rounded-full opacity-0 transition-opacity duration-300"></span></a></li>
                <li class="relative"><a href="#education" class="nav-link text-lg font-medium">Education<span class="active-dot absolute -bottom-1 left-1/2 transform -translate-x-1/2 w-2 h-2 bg-purple-500 rounded-full opacity-0 transition-opacity duration-300"></span></a></li>
                <li class="relative"><a href="#skills" class="nav-link text-lg font-medium">Skills<span class="active-dot absolute -bottom-1 left-1/2 transform -translate-x-1/2 w-2 h-2 bg-purple-500 rounded-full opacity-0 transition-opacity duration-300"></span></a></li>
                <li class="relative"><a href="#projects" class="nav-link text-lg font-medium">Projects<span class="active-dot absolute -bottom-1 left-1/2 transform -translate-x-1/2 w-2 h-2 bg-purple-500 rounded-full opacity-0 transition-opacity duration-300"></span></a></li>
                <li class="relative"><a href="#experience" class="nav-link text-lg font-medium">Experience<span class="active-dot absolute -bottom-1 left-1/2 transform -translate-x-1/2 w-2 h-2 bg-purple-500 rounded-full opacity-0 transition-opacity duration-300"></span></a></li>
                <li class="relative"><a href="#contact" class="nav-link text-lg font-medium">Contact<span class="active-dot absolute -bottom-1 left-1/2 transform -translate-x-1/2 w-2 h-2 bg-purple-500 rounded-full opacity-0 transition-opacity duration-300"></span></a></li>
            </ul>
        </div>
    </nav>

    <!-- Home Section -->
    <section id="home" class="home-section">
        <div class="container mx-auto px-6">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
                <div class="home-content" data-aos="fade-right">
                    <h1>Hi, I'm Sumit</h1>
                    <h2><span id="typed-text"></span></h2>
                    <p>Cloud Engineer & Frontend Designer blending sleek UI with scalable cloud tech.</p>
                    <div class="cta-buttons mt-8 flex space-x-5">
                        <a href="#contact" class="btn-primary px-7 py-3 rounded-full font-medium">Hire Me</a>
                        <a href="assets/Ravi_CV.pdf" download class="btn-outline px-7 py-3 rounded-full font-medium">Download CV</a>
                    </div>
                </div>
                <div class="home-illustration hidden lg:block" data-aos="fade-left">
                    <img src="photosumit.jpeg" alt="Personal Image" class="w-full max-w-md mx-auto">
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about">
        <div class="container mx-auto px-4">
            <h2 class="section-title" data-aos="fade-up">About Me</h2>
            <div class="about-content grid grid-cols-1 md:grid-cols-2 gap-10 items-center max-w-4xl mx-auto" data-aos="fade-up" data-aos-delay="200">
                <!-- Image Left -->
                <div class="flex justify-center md:justify-end">
                    <div class="profile-image w-48 h-48 rounded-full overflow-hidden">
                        <img src="cloud.png" alt="Ravi" class="w-full h-full object-cover">
                    </div>
                </div>
                <!-- Info Right -->
                <div class="text-left space-y-4">
                    <h3 class="text-2xl font-semibold text-purple-500">Cloud Engineer</h3>
                    <p class="text-lg text-slate-400">I specialize in building scalable, secure, and efficient cloud infrastructure using modern DevOps and cloud-native technologies.</p>
                    <ul class="list-disc list-inside text-slate-400 space-y-2">
                        <li>Strong foundation in <span class="font-medium text-purple-500">cloud architecture</span> principles</li>
                        <li>Experience with <span class="font-medium text-purple-500">AWS, Docker, Kubernetes</span></li>
                        <li>Passionate about <span class="font-medium text-purple-500">automation</span> and <span class="font-medium text-purple-500">design systems</span></li>
                        <li>Focused on creating <span class="font-medium text-purple-500">performance, scalability</span></li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <!-- Education Section -->
    <section id="education">
        <div class="container mx-auto px-4">
            <h2 class="section-title" data-aos="fade-up">Education</h2>
            <div class="education-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                <!-- <div class="education-card card text-center" data-aos="fade-up" data-aos-delay="100">
                    <div class="education-icon w-16 h-16 flex items-center justify-center bg-purple-900 text-purple-500 rounded-full mx-auto mb-4 text-2xl"><i class="fas fa-graduation-cap"></i></div>
                    <h3 class="text-lg font-semibold text-slate-100">Undergraduate B-tech</h3>
                    <p class="text-slate-400">LPU, 2023</p>
                    <p class="education-date text-purple-500">Ongoing</p>
                </div> -->
                <div class="education-card card text-center" data-aos="fade-up" data-aos-delay="200">
                    <div class="education-icon w-16 h-16 flex items-center justify-center bg-purple-900 text-purple-500 rounded-full mx-auto mb-4 text-2xl"><i class="fas fa-building"></i></div>
                    <h3 class="text-lg font-semibold text-slate-100">St.Antony School</h3>
                    <p class="text-slate-400">Class XII, 2020</p>
                </div>
                <div class="education-card card text-center" data-aos="fade-up" data-aos-delay="300">
                    <div class="education-icon w-16 h-16 flex items-center justify-center bg-purple-900 text-purple-500 rounded-full mx-auto mb-4 text-2xl"><i class="fas fa-graduation-cap"></i></div>
                    <h3 class="text-lg font-semibold text-slate-100">Lovely Professional University</h3>
                    <p class="text-slate-400">B.Tech CSE, 2023</p>
                </div>
                <div class="education-card card text-center" data-aos="fade-up" data-aos-delay="400">
                    <div class="education-icon w-16 h-16 flex items-center justify-center bg-purple-900 text-purple-500 rounded-full mx-auto mb-4 text-2xl"><i class="fas fa-certificate"></i></div>
                    <h3 class="text-lg font-semibold text-slate-100">Coursera</h3>
                    <p class="text-slate-400">UX Design, Google UI/UX Certification</p>
                    <p class="education-date text-purple-500">Ongoing</p>
                </div>
                <div class="education-card card text-center" data-aos="fade-up" data-aos-delay="400">
                    <div class="education-icon w-16 h-16 flex items-center justify-center bg-purple-900 text-purple-500 rounded-full mx-auto mb-4 text-2xl"><i class="fas fa-certificate"></i></div>
                    <h3 class="text-lg font-semibold text-slate-100">AWS Accademy</h3>
                    <p class="text-slate-400">AWS</p>
                    <p class="education-date text-purple-500">Complete</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills">
        <div class="container mx-auto px-4">
            <h2 class="section-title" data-aos="fade-up">Skills</h2>
            <div class="skills-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-4xl mx-auto">
                <div class="skill-card card" data-aos="fade-up" data-aos-delay="100">
                    <div class="flex justify-between items-center mb-2">
                        <h3 class="text-lg font-semibold text-slate-100">HTML</h3>
                        <span class="text-purple-500 font-medium">92%</span>
                    </div>
                    <div class="progress-bar rounded-full overflow-hidden">
                        <div class="progress h-full" style="width: 92%;"></div>
                    </div>
                </div>
                <div class="skill-card card" data-aos="fade-up" data-aos-delay="200">
                    <div class="flex justify-between items-center mb-2">
                        <h3 class="text-lg font-semibold text-slate-100">CSS</h3>
                        <span class="text-purple-500 font-medium">88%</span>
                    </div>
                    <div class="progress-bar rounded-full overflow-hidden">
                        <div class="progress h-full" style="width: 88%;"></div>
                    </div>
                </div>
                <div class="skill-card card" data-aos="fade-up" data-aos-delay="300">
                    <div class="flex justify-between items-center mb-2">
                        <h3 class="text-lg font-semibold text-slate-100">JavaScript</h3>
                        <span class="text-purple-500 font-medium">78%</span>
                    </div>
                    <div class="progress-bar rounded-full overflow-hidden">
                        <div class="progress h-full" style="width: 78%;"></div>
                    </div>
                </div>
                <div class="skill-card card" data-aos="fade-up" data-aos-delay="400">
                    <div class="flex justify-between items-center mb-2">
                        <h3 class="text-lg font-semibold text-slate-100">AWS</h3>
                        <span class="text-purple-500 font-medium">84%</span>
                    </div>
                    <div class="progress-bar rounded-full overflow-hidden">
                        <div class="progress h-full" style="width: 84%;"></div>
                    </div>
                </div>
                <div class="skill-card card" data-aos="fade-up" data-aos-delay="500">
                    <div class="flex justify-between items-center mb-2">
                        <h3 class="text-lg font-semibold text-slate-100">UI/UX</h3>
                        <span class="text-purple-500 font-medium">90%</span>
                    </div>
                    <div class="progress-bar rounded-full overflow-hidden">
                        <div class="progress h-full" style="width: 90%;"></div>
                    </div>
                </div>
                <div class="skill-card card" data-aos="fade-up" data-aos-delay="600">
                    <div class="flex justify-between items-center mb-2">
                        <h3 class="text-lg font-semibold text-slate-100">Git</h3>
                        <span class="text-purple-500 font-medium">85%</span>
                    </div>
                    <div class="progress-bar rounded-full overflow-hidden">
                        <div class="progress h-full" style="width: 85%;"></div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects">
        <div class="container mx-auto px-4">
            <h2 class="section-title" data-aos="fade-up">Projects</h2>
            <div class="projects-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <div class="project-card card overflow-hidden" data-aos="fade-up" data-aos-delay="100" data-project-id="1">
                    <div class="project-image">
                        <img src="s3.png" alt="Random Paragraph Generator" class="w-full">
                    </div>
                    <div class="project-content p-6">
                        <h3 class="text-lg font-semibold text-slate-100">Static Website Hosting with S3</h3>
                        <p class="text-slate-400 mt-2">Host a personal static website using Amazon S3, with a custom domain via Route 53 and secure delivery through CloudFront.</p>
                        <div class="project-tech flex flex-wrap gap-2 mt-4">
                            <span>S3</span>
                            <span>IAM</span>
                            <span>CloudFont</span>
                        </div>
                        <div class="project-links flex gap-2 mt-4">
                            <!-- <a href="#" class="bg-purple-500 text-white px-4 py-2 rounded-full text-sm hover:bg-purple-600 transition-colors" target="_blank">Live</a>
                            <a href="#" class="border border-purple-500 text-purple-500 px-4 py-2 rounded-full text-sm hover:bg-purple-500 hover:text-white transition-colors" target="_blank">Code</a> -->
                        </div>
                    </div>
                </div>
                <div class="project-card card overflow-hidden" data-aos="fade-up" data-aos-delay="200" data-project-id="2">
                    <div class="project-image">
                        <img src="personal.png" alt="Zodiac Date Website" class="w-full">
                    </div>
                    <div class="project-content p-6">
                        <h3 class="text-lg font-semibold text-slate-100">Personal Expense Tracker</h3>
                        <p class="text-slate-400 mt-2">Track and manage your daily expenses using a mobile app, with data stored in the cloud and visualized through an analytics dashboard.</p>
                        <div class="project-tech flex flex-wrap gap-2 mt-4">
                            <span>DynamoDB</span>
                            <span>Lambda</span>
                            <span>API Gateway</span>
    
                        </div>
                        <div class="project-links flex gap-2 mt-4">
                            <!-- <a href="#" class="bg-purple-500 text-white px-4 py-2 rounded-full text-sm hover:bg-purple-600 transition-colors" target="_blank">Live</a> -->
                            <!-- <a href="#" class="border border-purple-500 text-purple-500 px-4 py-2 rounded-full text-sm hover:bg-purple-500 hover:text-white transition-colors" target="_blank">Code</a> -->
                        </div>
                    </div>
                </div>
                <div class="project-card card overflow-hidden" data-aos="fade-up" data-aos-delay="300" data-project-id="3">
                    <div class="project-image">
                        <img src="temp.png" alt="Temperature Converter" class="w-full">
                    </div>
                    <div class="project-content p-6">
                        <h3 class="text-lg font-semibold text-slate-100">Temperature Converter</h3>
                        <p class="text-slate-400 mt-2">A simple app to convert temperatures between Celsius, Fahrenheit, and Kelvin.</p>
                        <div class="project-tech flex flex-wrap gap-2 mt-4">
                            <span>HTML</span>
                            <span>CSS</span>
                            <span>JavaScript</span>
                        </div>
                        <div class="project-links flex gap-2 mt-4">
                            <!-- <a href="#" class="bg-purple-500 text-white px-4 py-2 rounded-full text-sm hover:bg-purple-600 transition-colors" target="_blank">Live</a> -->
                            <!-- <a href="#" class="border border-purple-500 text-purple-500 px-4 py-2 rounded-full text-sm hover:bg-purple-500 hover:text-white transition-colors" target="_blank">Code</a> -->
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Experience Section -->
    <section id="experience">
        <div class="container mx-auto px-4">
            <h2 class="section-title" data-aos="fade-up">Experience</h2>
            <div class="experience-timeline relative max-w-3xl mx-auto pt-6">
                <div class="experience-item mb-12" data-aos="fade-up" data-aos-delay="100">
                    <div class="experience-content card p-6 relative">
                        <h3 class="text-lg font-semibold text-slate-100">Google Cloud Virtual Internship</h3>
                        <p class="text-slate-400 mt-2">Completed a 1-month virtual internship focusing on cloud technologies.</p>
                        <div class="text-purple-500 mt-2 font-medium">2023</div>
                    </div>
                </div>
                <div class="experience-item mb-12" data-aos="fade-up" data-aos-delay="200">
                    <div class="experience-content card p-6 relative">
                        <h3 class="text-lg font-semibold text-slate-100">AWS</h3>
                        <p class="text-slate-400 mt-2">I have an experience in AWS</p>
                        <div class="text-purple-500 mt-2 font-medium">2023 - Present</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact">
        <div class="container mx-auto px-4">
            <h2 class="section-title" data-aos="fade-up">Contact Me</h2>
            <div class="contact-content grid grid-cols-1 md:grid-cols-3 gap-8 max-w-4xl mx-auto">
                <div class="contact-info flex flex-col space-y-4 card" data-aos="fade-right">
                    <div class="contact-item flex items-center">
                        <i class="fas fa-envelope mr-4"></i>
                        <p class="text-slate-100">rajsumit1228@gmail.com</p>
                    </div>
                    <div class="contact-item flex items-center">
                        <i class="fas fa-map-marker-alt mr-4"></i>
                        <p class="text-slate-100">India</p>
                    </div>
                    <div class="social-links flex space-x-4 mt-4">
                        <a href="https://github.com/Sumitraj28" target="_blank" class="social-link" aria-label="GitHub"><i class="fab fa-github"></i></a>
                        <a href="https://www.linkedin.com/in/sumit-raj-verma-944890283/" target="_blank" class="social-link" aria-label="LinkedIn"><i class="fab fa-linkedin"></i></a>
                        <a href="https://x.com/SumitRaj1824651" target="_blank" class="social-link" aria-label="Twitter"><i class="fab fa-twitter"></i></a>
                    </div>
                </div>
                <div class="contact-form card md:col-span-2" data-aos="fade-left">
                    <form id="contact-form" action="#" method="POST">
                        <div class="form-group mb-4">
                            <input type="text" name="name" id="name" class="w-full" placeholder="Your Name" required>
                        </div>
                        <div class="form-group mb-4">
                            <input type="email" name="email" id="email" class="w-full" placeholder="Your Email" required>
                        </div>
                        <div class="form-group mb-4">
                            <input type="text" name="subject" id="subject" class="w-full" placeholder="Subject" required>
                        </div>
                        <div class="form-group mb-4">
                            <textarea name="message" id="message" class="w-full" placeholder="Your Message" rows="5" required></textarea>
                        </div>
                        <button type="submit" class="bg-purple-500 text-white px-6 py-3 rounded-full hover:bg-purple-600 transition-colors w-full">Send Message</button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer py-12 text-center">
        <div class="container mx-auto px-4">
            <div class="footer-content">
                <p class="text-slate-400">© 2025 Raj. All rights reserved.</p>
                <div class="footer-links flex justify-center gap-6 my-4">
                    <a href="#home" class="hover:text-purple-500 transition-colors">Home</a>
                    <a href="#about" class="hover:text-purple-500 transition-colors">About</a>
                    <a href="#contact" class="hover:text-purple-500 transition-colors">Contact</a>
                </div>
                <p class="text-purple-500 mt-4">Designed with ❤️ by Raj</p>
            </div>
        </div>
    </footer>

    <!-- Scroll to Top Button -->
    <button id="scroll-top" class="scroll-top-btn" aria-label="Scroll to top">
        <i class="fas fa-arrow-up"></i>
    </button>

    <!-- Project Modal -->
    <div id="project-modal">
        <div class="modal-content">
            <h3 id="modal-title" class="text-xl font-semibold text-slate-100 mb-4"></h3>
            <img id="modal-image" src="" alt="Project Image" class="w-full rounded-lg mb-4">
            <p id="modal-description" class="text-slate-400 mb-4"></p>
            <div id="modal-tech" class="flex flex-wrap gap-2 mb-4"></div>
            <div class="flex gap-4">
                <a id="modal-live" href="#" class="bg-purple-500 text-white px-4 py-2 rounded-full text-sm hover:bg-purple-600 transition-colors" target="_blank">Live</a>
                <a id="modal-code" href="#" class="border border-purple-500 text-purple-500 px-4 py-2 rounded-full text-sm hover:bg-purple-500 hover:text-white transition-colors" target="_blank">Code</a>
                <button id="modal-close" class="bg-gray-600 text-white px-4 py-2 rounded-full text-sm hover:bg-gray-700 transition-colors">Close</button>
            </div>
        </div>
    </div>

    <!-- Scripts -->
    <script src="https://unpkg.com/aos@next/dist/aos.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/typed.js@2.0.12"></script>
    <script>
        // Preloader Logic with Timeout
        document.addEventListener('DOMContentLoaded', () => {
            const preloader = document.querySelector('.preloader');
            const hidePreloader = () => {
                preloader.classList.add('hidden');
            };

            // Hide preloader after window load or after 5 seconds
            window.addEventListener('load', hidePreloader);
            setTimeout(hidePreloader, 5000);
        });

        // Initialize AOS
        if (typeof AOS !== 'undefined') {
            AOS.init({ duration: 800, once: true });
        }

        // Navbar Toggle
        const navToggle = document.querySelector('.nav-toggle');
        const navMenu = document.querySelector('.nav-menu');
        navToggle.addEventListener('click', () => {
            navMenu.classList.toggle('active');
            navToggle.classList.toggle('active');
        });

        // Smooth Scroll and Active Link
        const navLinks = document.querySelectorAll('.nav-menu a');
        const sections = document.querySelectorAll('section');

        window.addEventListener('scroll', () => {
            let current = '';
            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                const sectionHeight = section.clientHeight;
                if (pageYOffset >= sectionTop - sectionHeight / 3) {
                    current = section.getAttribute('id');
                }
            });

            navLinks.forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('href') === `#${current}`) {
                    link.classList.add('active');
                }
            });
        });

        document.querySelectorAll('.nav-menu a, .footer-links a').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                document.querySelector(targetId).scrollIntoView({ behavior: 'smooth' });
                navMenu.classList.remove('active');
                navToggle.classList.remove('active');
            });
        });

        // Scroll to Top
        const scrollTopBtn = document.getElementById('scroll-top');
        window.addEventListener('scroll', () => {
            scrollTopBtn.classList.toggle('active', window.scrollY > 300);
        });
        scrollTopBtn.addEventListener('click', () => {
            window.scrollTo({ top: 0, behavior: 'smooth' });
        });

        // Typed.js
        if (typeof Typed !== 'undefined') {
            const typed = new Typed('#typed-text', {
                strings: ['AWS', 'Docker', 'Kubernetes', 'Frontend Designer', 'Cloud Engineer'],
                typeSpeed: 50,
                backSpeed: 30,
                backDelay: 2000,
                loop: true
            });
        }

        // Navbar Scroll Effect
        window.addEventListener('scroll', () => {
            document.querySelector('.navbar').classList.toggle('scrolled', window.scrollY > 50);
        });

        // Project Modal
        const projectCards = document.querySelectorAll('.project-card');
        const modal = document.getElementById('project-modal');
        const modalTitle = document.getElementById('modal-title');
        const modalImage = document.getElementById('modal-image');
        const modalDescription = document.getElementById('modal-description');
        const modalTech = document.getElementById('modal-tech');
        const modalLive = document.getElementById('modal-live');
        const modalCode = document.getElementById('modal-code');
        const modalClose = document.getElementById('modal-close');

        projectCards.forEach(card => {
            card.addEventListener('click', () => {
                const title = card.querySelector('h3').textContent;
                const image = card.querySelector('img').src;
                const description = card.querySelector('p').textContent;
                const techs = card.querySelectorAll('.project-tech span');
                const liveLink = card.querySelector('.project-links a:nth-child(1)').href;
                const codeLink = card.querySelector('.project-links a:nth-child(2)').href;

                modalTitle.textContent = title;
                modalImage.src = image;
                modalDescription.textContent = description;
                modalTech.innerHTML = '';
                techs.forEach(tech => {
                    const span = document.createElement('span');
                    span.textContent = tech.textContent;
                    span.className = 'bg-gray-700 text-purple-500 font-semibold px-2 py-1 rounded-full text-sm';
                    modalTech.appendChild(span);
                });
                modalLive.href = liveLink;
                modalCode.href = codeLink;

                modal.classList.add('active');
            });
        });

        modalClose.addEventListener('click', () => {
            modal.classList.remove('active');
        });

        modal.addEventListener('click', (e) => {
            if (e.target === modal) {
                modal.classList.remove('active');
            }
        });

        // Form Validation
        const form = document.getElementById('contact-form');
        form.addEventListener('submit', (e) => {
            e.preventDefault();
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const subject = document.getElementById('subject').value;
            const message = document.getElementById('message').value;

            if (name && email && subject && message) {
                alert('Form submitted successfully!');
                form.reset();
            } else {
                alert('Please fill in all fields.');
            }
        });
    </script>
</body>
</html>
