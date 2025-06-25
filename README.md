<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Radhika - Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            margin-top: 20px;
            margin-bottom: 20px;
            backdrop-filter: blur(10px);
        }

        .header {
            text-align: center;
            padding: 40px 0;
            background: linear-gradient(135deg, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 40px;
        }

        .header h1 {
            font-size: 3.5em;
            font-weight: bold;
            margin-bottom: 10px;
            animation: fadeInUp 1s ease-out, float 3s ease-in-out infinite 2s;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .header h1:hover {
            animation: bounce 1s ease-in-out;
            text-shadow: 0 0 20px rgba(255, 107, 107, 0.5);
        }

        .header .subtitle {
            font-size: 1.3em;
            color: #666;
            animation: fadeInUp 1s ease-out 0.2s both;
        }

        .section {
            margin-bottom: 50px;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 0.8s ease-out forwards;
        }

        .section:nth-child(2) { animation-delay: 0.1s; }
        .section:nth-child(3) { animation-delay: 0.2s; }
        .section:nth-child(4) { animation-delay: 0.3s; }
        .section:nth-child(5) { animation-delay: 0.4s; }

        .section-title {
            font-size: 2.5em;
            color: #2c3e50;
            margin-bottom: 20px;
            position: relative;
            padding-bottom: 10px;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 60px;
            height: 4px;
            background: linear-gradient(135deg, #ff6b6b, #4ecdc4);
            border-radius: 2px;
            animation: slideInLeft 0.8s ease-out 0.5s both;
        }

        .section-title:hover::after {
            width: 120px;
            transition: width 0.3s ease;
        }

        .about-text {
            font-size: 1.2em;
            line-height: 1.8;
            text-align: justify;
            margin-bottom: 20px;
            color: #555;
        }

        .experience-item, .education-item {
            background: #f8f9fa;
            padding: 25px;
            margin-bottom: 20px;
            border-radius: 15px;
            border-left: 5px solid #4ecdc4;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
        }

        .experience-item:hover, .education-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
        }

        .job-title, .degree-title {
            font-size: 1.4em;
            font-weight: bold;
            color: #2c3e50;
            margin-bottom: 5px;
        }

        .company, .institution {
            font-size: 1.1em;
            color: #3498db;
            margin-bottom: 10px;
        }

        .job-description {
            color: #666;
            line-height: 1.6;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .skill-category {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            padding: 25px;
            border-radius: 15px;
            color: white;
            text-align: center;
            transition: transform 0.3s ease;
        }

        .skill-category:hover {
            transform: translateY(-10px) scale(1.02);
            animation: pulse 0.6s ease-in-out;
        }

        .skill-category:nth-child(odd) {
            animation: slideInLeft 0.8s ease-out;
        }

        .skill-category:nth-child(even) {
            animation: slideInRight 0.8s ease-out;
        }

        .skill-category h3 {
            font-size: 1.3em;
            margin-bottom: 15px;
        }

        .skill-list {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 8px;
        }

        .skill-tag {
            background: rgba(255, 255, 255, 0.2);
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.9em;
            backdrop-filter: blur(5px);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .skill-tag:hover {
            background: rgba(255, 255, 255, 0.4);
            transform: scale(1.1) rotate(5deg);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .project-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            padding: 30px;
            border-radius: 20px;
            color: white;
            text-align: center;
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .project-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.5s;
        }

        .project-card:hover {
            transform: translateY(-10px) rotateY(5deg);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
            animation: float 2s ease-in-out infinite;
        }

        .project-card:hover::before {
            left: 100%;
        }

        .project-card h3 {
            font-size: 1.5em;
            margin-bottom: 15px;
        }

        .contact-section {
            text-align: center;
            padding: 40px;
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            border-radius: 15px;
            margin-top: 40px;
        }

        .contact-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
            flex-wrap: wrap;
        }

        .contact-link {
            background: white;
            color: #333;
            padding: 12px 25px;
            text-decoration: none;
            border-radius: 25px;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .contact-link:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
            background: #333;
            color: white;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-100px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(100px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes rotate360 {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        @keyframes bounce {
            0%, 20%, 53%, 80%, 100% { transform: translate3d(0,0,0); }
            40%, 43% { transform: translate3d(0,-20px,0); }
            70% { transform: translate3d(0,-10px,0); }
            90% { transform: translate3d(0,-4px,0); }
        }

        @media (max-width: 768px) {
            .header h1 {
                font-size: 2.5em;
            }
            
            .section-title {
                font-size: 2em;
            }
            
            .container {
                margin: 10px;
                padding: 15px;
            }
            
            .skills-grid, .projects-grid {
                grid-template-columns: 1fr;
            }
            
            .contact-links {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="header">
            <h1>Hi, I'm Radhika</h1>
            <p class="subtitle">Software Engineer & Data Analytics Enthusiast</p>
        </header>

        <section class="section">
            <h2 class="section-title">About</h2>
            <p class="about-text">
                Driven by curiosity and fueled by a passion for engineering, I thrive on solving complex, real-world problems. As a quick starter, I excel at turning challenges into opportunities and delivering innovative solutions.
            </p>
            <p class="about-text">
                Experienced IT professional with expertise in software engineering and data analytics. Over [X] years of success delivering high-quality solutions across diverse domains. Currently contributing to innovative projects, leveraging system programming, data analytics, and design thinking. Skilled in multiple programming languages, machine learning, system software programming, data visualization, and database systems. Proven track record of meeting client needs and driving innovation.
            </p>
            <p class="about-text">
                Exploring challenging opportunities in Software Engineering where I can apply my expertise and foster both professional development and personal growth through engaging experiences.
            </p>
        </section>

        <section class="section">
            <h2 class="section-title">Experience</h2>
            
            <div class="experience-item">
                <div class="job-title">Senior Software Engineer</div>
                <div class="company">Current Company • 2023 - Present</div>
                <div class="job-description">
                    • Designed end-to-end workflow and architecture for a self-serving AI chatbot on data visualization platforms, enhancing employee experience and business profit<br>
                    • Created real-time dashboards for analysis and visualization of critical project metrics, including sales and marketing data<br>
                    • Successfully led cross-functional teams from diverse global locations, resulting in a 50% boost in employee efficiency<br>
                    • Tools: Python, JIRA, ThoughtSpot, Google Looker, Power BI
                </div>
            </div>

            <div class="experience-item">
                <div class="job-title">Software Engineer</div>
                <div class="company">Previous Company • 2020 - 2023</div>
                <div class="job-description">
                    • Spearheaded data-driven decision-making initiatives by implementing ML techniques, achieving 20% boost in accuracy<br>
                    • Leveraged programming expertise in multiple languages to drive innovation in software engineering<br>
                    • Developed end-to-end Robotic Process Automation solutions, contributing to 25% increase in actionable insights<br>
                    • Tools: Python, JavaScript, Java, C, C++, C#, MySQL
                </div>
            </div>

            <div class="experience-item">
                <div class="job-title">Quality Assurance Engineer</div>
                <div class="company">Tech Company • 2019 - 2020</div>
                <div class="job-description">
                    • Achieved 25% decrease in bug count and 20% improvement in product quality through KPI tracking and process optimization<br>
                    • Developed Test metrics based on KPIs and built Linear Regression model for QA targeting<br>
                    • Improved data transfer pipeline efficiency by 60% through re-engineering and migration strategies<br>
                    • Tools: Python, JavaScript, Java, JIRA
                </div>
            </div>
        </section>

        <section class="section">
            <h2 class="section-title">Projects</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <h3>🔍 Data Mining & Clustering</h3>
                    <p>Implementing Data Mining using the Unsupervised learning method of Cluster analysis for pattern recognition and insights.</p>
                </div>
                
                <div class="project-card">
                    <h3>🤖 NLP Sentiment Analysis</h3>
                    <p>An NLP-based Sentimental Analysis project using Python, leveraging natural language processing for emotion detection.</p>
                </div>
                
                <div class="project-card">
                    <h3>📊 Real-time Dashboard</h3>
                    <p>Interactive dashboard for real-time analysis of project metrics, sales data, and team performance indicators.</p>
                </div>

                <div class="project-card">
                    <h3>🤖 AI Chatbot System</h3>
                    <p>End-to-end AI chatbot architecture for data visualization platforms with self-serving capabilities.</p>
                </div>
            </div>
        </section>

        <section class="section">
            <h2 class="section-title">Skills</h2>
            <div class="skills-grid">
                <div class="skill-category">
                    <h3>Languages</h3>
                    <div class="skill-list">
                        <span class="skill-tag">Python</span>
                        <span class="skill-tag">Java</span>
                        <span class="skill-tag">JavaScript</span>
                        <span class="skill-tag">C/C++</span>
                        <span class="skill-tag">C#</span>
                        <span class="skill-tag">HTML/CSS</span>
                        <span class="skill-tag">Bash</span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3>Databases</h3>
                    <div class="skill-list">
                        <span class="skill-tag">MySQL</span>
                        <span class="skill-tag">PostgreSQL</span>
                        <span class="skill-tag">MongoDB</span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3>Frameworks</h3>
                    <div class="skill-list">
                        <span class="skill-tag">Flask</span>
                        <span class="skill-tag">Django</span>
                        <span class="skill-tag">Node.js</span>
                        <span class="skill-tag">TensorFlow</span>
                        <span class="skill-tag">PyTorch</span>
                        <span class="skill-tag">Bootstrap</span>
                        <span class="skill-tag">.NET</span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3>Tools & Technologies</h3>
                    <div class="skill-list">
                        <span class="skill-tag">Git</span>
                        <span class="skill-tag">Docker</span>
                        <span class="skill-tag">AWS</span>
                        <span class="skill-tag">JIRA</span>
                        <span class="skill-tag">Tableau</span>
                        <span class="skill-tag">Power BI</span>
                    </div>
                </div>
            </div>
        </section>

        <section class="section">
            <h2 class="section-title">Education</h2>
            
            <div class="education-item">
                <div class="degree-title">Master of Science in Information Technology</div>
                <div class="institution">Worcester Polytechnic Institute • Massachusetts, USA</div>
                <div class="job-description">
                    <strong>GPA: 4.0/4.0</strong><br>
                    Relevant Coursework: Statistics, Data Analytics, Business Intelligence, Machine Learning, User Experience Design, Project Management
                </div>
            </div>

            <div class="education-item">
                <div class="degree-title">Bachelor of Technology in Computer Science</div>
                <div class="institution">Your University • Your Location</div>
                <div class="job-description">
                    Relevant Coursework: Data Structures and Algorithms, Database Management System, Operating Systems, Computer Programming, Electronic System Design, Cyber Security
                </div>
            </div>
        </section>

        <section class="contact-section">
            <h2 class="section-title">Let's Connect!</h2>
            <p>I'm always interested in hearing about new opportunities and exciting projects.</p>
            <div class="contact-links">
                <a href="mailto:your.email@example.com" class="contact-link">📧 Email</a>
                <a href="https://linkedin.com/in/yourprofile" class="contact-link">💼 LinkedIn</a>
                <a href="https://github.com/rads30" class="contact-link">🐙 GitHub</a>
                <a href="tel:+1234567890" class="contact-link">📱 Phone</a>
            </div>
        </section>
    </div>

    <script>
        // Add smooth scrolling and interactive effects
        document.addEventListener('DOMContentLoaded', function() {
            // Animate sections on scroll
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            }, { threshold: 0.1 });

            document.querySelectorAll('.section').forEach(section => {
                observer.observe(section);
            });

            // Add click effects to project cards
            document.querySelectorAll('.project-card').forEach(card => {
                card.addEventListener('click', function() {
                    this.style.transform = 'scale(0.95)';
                    setTimeout(() => {
                        this.style.transform = 'translateY(-10px) rotateY(5deg)';
                    }, 150);
                });
            });

            // Add typing effect to the header
            const subtitle = document.querySelector('.subtitle');
            const text = subtitle.textContent;
            subtitle.textContent = '';
            let i = 0;
            
            const typeWriter = () => {
                if (i < text.length) {
                    subtitle.textContent += text.charAt(i);
                    i++;
                    setTimeout(typeWriter, 100);
                }
            };
            
            setTimeout(typeWriter, 1000);

            // Interactive particle background effect
            createParticles();

            // Add mouse follow effect for header
            const header = document.querySelector('.header h1');
            document.addEventListener('mousemove', (e) => {
                const x = (e.clientX / window.innerWidth) * 100;
                const y = (e.clientY / window.innerHeight) * 100;
                header.style.textShadow = `${x/10}px ${y/10}px 20px rgba(255, 107, 107, 0.3)`;
            });

            // Add skill tag click animations
            document.querySelectorAll('.skill-tag').forEach(tag => {
                tag.addEventListener('click', function() {
                    this.style.animation = 'rotate360 0.6s ease-in-out';
                    setTimeout(() => {
                        this.style.animation = '';
                    }, 600);
                });
            });

            // Add experience item hover counter
            document.querySelectorAll('.experience-item').forEach((item, index) => {
                item.addEventListener('mouseenter', function() {
                    this.style.borderLeft = `5px solid ${getRandomColor()}`;
                    this.style.transform = 'translateX(10px) scale(1.02)';
                });
                
                item.addEventListener('mouseleave', function() {
                    this.style.borderLeft = '5px solid #4ecdc4';
                    this.style.transform = 'translateX(0) scale(1)';
                });
            });

            // Add section title click effect
            document.querySelectorAll('.section-title').forEach(title => {
                title.addEventListener('click', function() {
                    this.style.animation = 'bounce 0.6s ease-in-out';
                    setTimeout(() => {
                        this.style.animation = '';
                    }, 600);
                });
            });

            // Add contact links animation on page load
            setTimeout(() => {
                document.querySelectorAll('.contact-link').forEach((link, index) => {
                    setTimeout(() => {
                        link.style.opacity = '0';
                        link.style.transform = 'translateY(20px)';
                        link.style.transition = 'all 0.5s ease';
                        setTimeout(() => {
                            link.style.opacity = '1';
                            link.style.transform = 'translateY(0)';
                        }, 100);
                    }, index * 200);
                });
            }, 2000);
        });

        // Helper function for random colors
        function getRandomColor() {
            const colors = ['#ff6b6b', '#4ecdc4', '#45b7d1', '#96ceb4', '#ffeaa7', '#dda0dd', '#98d8c8'];
            return colors[Math.floor(Math.random() * colors.length)];
        }

        // Create floating particles effect
        function createParticles() {
            const particleCount = 20;
            const body = document.body;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.style.position = 'fixed';
                particle.style.width = Math.random() * 4 + 2 + 'px';
                particle.style.height = particle.style.width;
                particle.style.background = getRandomColor();
                particle.style.borderRadius = '50%';
                particle.style.opacity = '0.1';
                particle.style.pointerEvents = 'none';
                particle.style.zIndex = '-1';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                
                body.appendChild(particle);

                animateParticle(particle);
            }
        }

        function animateParticle(particle) {
            const duration = Math.random() * 3000 + 2000;
            const startX = parseFloat(particle.style.left);
            const startY = parseFloat(particle.style.top);
            const endX = Math.random() * 100;
            const endY = Math.random() * 100;

            particle.animate([
                { left: startX + '%', top: startY + '%', opacity: 0.1 },
                { left: endX + '%', top: endY + '%', opacity: 0.3 },
                { left: Math.random() * 100 + '%', top: Math.random() * 100 + '%', opacity: 0.1 }
            ], {
                duration: duration,
                iterations: Infinity,
                easing: 'ease-in-out'
            });
        }

        // Add scroll progress indicator
        window.addEventListener('scroll', () => {
            const scrollTop = document.documentElement.scrollTop;
            const scrollHeight = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrollPercent = (scrollTop / scrollHeight) * 100;
            
            // Create progress bar if it doesn't exist
            let progressBar = document.querySelector('.scroll-progress');
            if (!progressBar) {
                progressBar = document.createElement('div');
                progressBar.className = 'scroll-progress';
                progressBar.style.cssText = `
                    position: fixed;
                    top: 0;
                    left: 0;
                    width: 0%;
                    height: 4px;
                    background: linear-gradient(135deg, #ff6b6b, #4ecdc4);
                    z-index: 1000;
                    transition: width 0.1s ease;
                `;
                document.body.appendChild(progressBar);
            }
            
            progressBar.style.width = scrollPercent + '%';
        });
    </script>
</body>
</html>
