# Movie-stream-pro
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MovieStream Pro - Premium Movie Platform</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0c0c0c 0%, #1a1a2e 50%, #16213e 100%);
            color: #fff;
            overflow-x: hidden;
        }

        /* Header */
        .header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(0, 0, 0, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 1rem 0;
            transition: all 0.3s ease;
        }

        .nav-container {
            max-width: 1400px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
        }

        .logo {
            font-size: 2rem;
            font-weight: bold;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .nav-menu {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-menu a {
            color: #fff;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-menu a:hover {
            color: #4ecdc4;
        }

        .auth-buttons {
            display: flex;
            gap: 1rem;
        }

        .btn {
            padding: 0.8rem 1.5rem;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
            text-decoration: none;
            display: inline-block;
        }

        .btn-primary {
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            color: white;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(255, 107, 107, 0.4);
        }

        .btn-secondary {
            background: transparent;
            color: #fff;
            border: 2px solid #4ecdc4;
        }

        .btn-secondary:hover {
            background: #4ecdc4;
            transform: translateY(-2px);
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.7)),
                        url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 600"><rect fill="%23000" width="1200" height="600"/><circle fill="%23ff6b6b" opacity="0.1" cx="200" cy="150" r="100"/><circle fill="%234ecdc4" opacity="0.1" cx="1000" cy="400" r="150"/><rect fill="%23ffd93d" opacity="0.05" x="400" y="300" width="200" height="100"/></svg>');
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
        }

        .hero-content h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, #fff, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-content p {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            opacity: 0.9;
        }

        /* Subscription Cards */
        .subscription-section {
            padding: 5rem 2rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .section-title {
            text-align: center;
            font-size: 3rem;
            margin-bottom: 4rem;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .subscription-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .subscription-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 2.5rem;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .subscription-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3);
            border-color: #4ecdc4;
        }

        .subscription-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transition: left 0.5s;
        }

        .subscription-card:hover::before {
            left: 100%;
        }

        .plan-name {
            font-size: 1.5rem;
            font-weight: bold;
            margin-bottom: 1rem;
        }

        .price {
            font-size: 3rem;
            font-weight: bold;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 1rem;
        }

        .features {
            list-style: none;
            margin-bottom: 2rem;
        }

        .features li {
            padding: 0.5rem 0;
            opacity: 0.8;
        }

        .features li i {
            color: #4ecdc4;
            margin-right: 0.5rem;
        }

        /* Movie Grid */
        .movies-section {
            padding: 5rem 2rem;
            background: rgba(0, 0, 0, 0.3);
        }

        .movies-grid {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1.5rem;
        }

        .movie-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            overflow: hidden;
            transition: all 0.3s;
            cursor: pointer;
            position: relative;
        }

        .movie-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
        }

        .movie-poster {
            width: 100%;
            height: 350px;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            color: rgba(255, 255, 255, 0.1);
        }

        .movie-info {
            padding: 1.5rem;
        }

        .movie-title {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .movie-year, .movie-quality {
            color: #4ecdc4;
            font-size: 0.9rem;
            margin-bottom: 0.3rem;
        }

        .quality-badge {
            display: inline-block;
            background: #ff6b6b;
            color: white;
            padding: 0.2rem 0.8rem;
            border-radius: 15px;
            font-size: 0.8rem;
            font-weight: bold;
        }

        /* Upload Section */
        .upload-section {
            padding: 5rem 2rem;
            max-width: 800px;
            margin: 0 auto;
        }

        .upload-form {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            padding: 3rem;
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .form-group {
            margin-bottom: 2rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 1rem;
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            color: #fff;
            font-size: 1rem;
        }

        .form-group input::placeholder, .form-group textarea::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.9);
            z-index: 2000;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            padding: 3rem;
            border-radius: 20px;
            max-width: 500px;
            width: 90%;
            text-align: center;
        }

        .close {
            position: absolute;
            top: 1rem;
            right: 1.5rem;
            font-size: 2rem;
            cursor: pointer;
            color: #fff;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-menu {
                display: none;
            }

            .hero-content h1 {
                font-size: 2.5rem;
            }

            .subscription-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .fade-in-up {
            animation: fadeInUp 0.8s ease forwards;
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="header" id="header">
        <nav class="nav-container">
            <div class="logo">MovieStream Pro</div>
            <ul class="nav-menu">
                <li><a href="#home">Home</a></li>
                <li><a href="#movies">Movies</a></li>
                <li><a href="#upload">Upload</a></li>
                <li><a href="#subscription">Subscribe</a></li>
            </ul>
            <div class="auth-buttons">
                <a href="#" class="btn btn-secondary" onclick="showLoginModal()">Login</a>
                <a href="#" class="btn btn-primary" onclick="showRegisterModal()">Get Premium</a>
            </div>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-content fade-in-up">
            <h1>Watch Latest Movies in 4K</h1>
            <p>Unlimited streaming with Premium subscription. Upload your own movies and reach millions.</p>
            <a href="#subscription" class="btn btn-primary" style="font-size: 1.2rem; padding: 1rem 2rem;">Start Free Trial</a>
        </div>
    </section>

    <!-- Subscription Section -->
    <section class="subscription-section" id="subscription">
        <h2 class="section-title">Choose Your Plan</h2>
        <div class="subscription-grid">
            <div class="subscription-card">
                <div class="plan-name">Basic</div>
                <div class="price">$0<span style="font-size: 1rem;">/month</span></div>
                <ul class="features">
                    <li><i class="fas fa-check"></i>720p Quality</li>
                    <li><i class="fas fa-check"></i>1 Device</li>
                    <li><i class="fas fa-times" style="color: #ff6b6b;"></i>Ad-Free</li>
                    <li><i class="fas fa-times" style="color: #ff6b6b;"></i>4K Streaming</li>
                </ul>
                <button class="btn btn-secondary">Get Started</button>
            </div>
            <div class="subscription-card" style="border: 2px solid #4ecdc4;">
                <div class="plan-name" style="color: #4ecdc4;">Premium</div>
                <div class="price">$9.99<span style="font-size: 1rem;">/month</span></div>
                <ul class="features">
                    <li><i class="fas fa-check"></i>4K Ultra HD</li>
                    <li><i class="fas fa-check"></i>Unlimited Devices</li>
                    <li><i class="fas fa-check"></i>Ad-Free</li>
                    <li><i class="fas fa-check"></i>Offline Download</li>
                </ul>
                <button class="btn btn-primary" onclick="subscribe('premium')">Subscribe Now</button>
            </div>
            <div class="subscription-card">
                <div class="plan-name">Lifetime</div>
                <div class="price">$99<span style="font-size: 1rem;">once</span></div>
                <ul class="features">
                    <li><i class="fas fa-check"></i>Everything in Premium</li>
                    <li><i class="fas fa-check"></i>Lifetime Access</li>
                    <li><i class="fas fa-check"></i>Priority Support</li>
                    <li><i class="fas fa-check"></i>Early Access</li>
                </ul>
                <button class="btn btn-primary">Buy Lifetime</button>
            </div>
        </div>
    </section>

    <!-- Movies Section -->
    <section class="movies-section" id="movies">
        <h2 class="section-title" style="text-align: center; margin-bottom: 3rem;">Latest 4K Movies</h2>
        <div class="movies-grid" id="moviesGrid">
            <!-- Movies will be populated by JavaScript -->
        </div>
    </section>

    <!-- Upload Section -->
    <section class="upload-section" id="upload">
        <h2 class="section-title" style="text-align: center;">Upload Your Movie</h2>
        <form class="upload-form" id="uploadForm">
            <div class="form-group">
                <label>Movie Title</label>
                <input type="text" placeholder="Enter movie title" required>
            </div>
            <div class="form-group">
                <label>Year</label>
                <input type="number" placeholder="2024" min="1900" max="2025" required>
            </div>
            <div class="form-group">
                <label>Quality</label>
                <select required>
                    <option value="">Select Quality</option>
                    <option value="720p">720p HD</option>
                    <option value="1080p">1080p Full HD</option>
                    <option value="4k">4K Ultra HD</option>
                </select>
            </div>
            <div class="form-group">
                <label>Genre</label>
                <select required>
                    <option value="">Select Genre</option>
                    <option value="action">Action</option>
                    <option value="drama">Drama</option>
                    <option value="comedy">Comedy</option>
                    <option value="horror">Horror</option>
                    <option value="sci-fi">Sci-Fi</option>
                </select>
            </div>
            <div class="form-group">
                <label>Description</label>
                <textarea rows="4" placeholder="Movie description..."></textarea>
            </div>
            <div class="form-group">
                <label>Video File</label>
                <input type="file" accept="video/*" required>
            </div>
            <button type="submit" class="btn btn-primary" style="width: 100%; font-size: 1.2rem;">Upload Movie</button>
        </form>
    </section>

    <!-- Login Modal -->
    <div class="modal" id="loginModal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('loginModal')">&times;</span>
            <h2>Login to Continue</h2>
            <p>Premium content requires subscription</p>
            <button class="btn btn-primary" onclick="subscribe('premium')" style="width: 100%; margin-top: 1rem;">Get Premium</button>
        </div>
    </div>

    <!-- Success Modal -->
    <div class="modal" id="successModal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('successModal')">&times;</span>
            <i class="fas fa-check-circle" style="font-size: 4rem; color: #4ecdc4; margin-bottom: 1rem;"></i>
            <h2>Success!</h2>
            <p id="successMessage"></p>
        </div>
    </div>

    <script>
        // Sample movie data
        const movies = [
            { title: "Avengers: Endgame", year: 2024, quality: "4K", genre: "Action" },
            { title: "Dune Part Two", year: 2024, quality: "4K", genre: "Sci-Fi" },
            { title: "Oppenheimer", year: 2024, quality: "4K", genre: "Drama" },
            { title: "Spider-Man: No Way Home", year: 2024, quality: "1080p", genre: "Action" },
            { title: "The Batman", year: 2024, quality: "4K", genre: "Action" },
            { title: "Black Panther: Wakanda Forever", year: 2024, quality: "4K", genre: "Action" },
            { title: "Top Gun: Maverick", year: 2024, quality: "4K", genre: "Action" },
            { title: "Everything Everywhere All At Once", year: 2024, quality: "4K", genre: "Sci-Fi" },
            { title: "Nope", year: 2024, quality: "1080p", genre: "Horror" },
            { title: "The Menu", year: 2024, quality: "4K", genre: "Horror" },
            { title: "Glass Onion", year: 2024, quality: "4K", genre: "Comedy" },
            { title: "Triangle of Sadness", year: 2024, quality: "1080p", genre: "Comedy" }
        ];

        let isPremium = false;
        let userMovies = [];

        // Initialize app
        document.addEventListener('DOMContentLoaded', function() {
            renderMovies();
            setupScrollEffects();
            setupIntersectionObserver();
        });

        // Render movies grid
        function renderMovies() {
            const moviesGrid = document.getElementById('moviesGrid');
            moviesGrid.innerHTML = '';

            movies.forEach((movie, index) => {
                const movieCard = document.createElement('div');
                movieCard.className = 'movie-card fade-in-up';
                movieCard.style.animationDelay = `${index * 0.1}s`;
                movieCard.innerHTML = `
                    <div class="movie-poster">
                        <i class="fas fa-film" style="font-size: 3rem; color: rgba(255,255,255,0.2);"></i>
                    </div>
                    <div class="movie-info">
                        <div class="movie-title">${movie.title}</div>
                        <div class="movie-year">${movie.year}</div>
                        <div class="movie-quality">
                            <span class="quality-badge">${movie.quality}</span>
                        </div>
                    </div>
                `;
                
                movieCard.addEventListener('click', () => playMovie(movie));
                moviesGrid.appendChild(movieCard);
            });
        }

        // Play movie function
        function playMovie(movie) {
            if (!isPremium && movie.quality === '4K') {
                showLoginModal();
                return;
            }
            
            showSuccessModal(`Playing ${movie.title} in ${movie.quality}`);
        }

        // Subscription
        function subscribe(plan) {
            isPremium = true;
            showSuccessModal('Premium subscription activated! Enjoy 4K streaming.');
            document.querySelectorAll('.quality-badge').forEach(badge => {
                badge.style.background = '#4ecdc4';
            });
        }

        // Upload form handler
        document.getElementById('uploadForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const formData = new FormData(this);
            const movieData = {
                title: this.querySelector('input[type="text"]').value,
                year: this.querySelector('input[type="number"]').value,
                quality: this.querySelector('select:nth-of-type(1)').value,
                genre: this.querySelector('select:nth-of-type(2)').value
            };

            if (!isPremium) {
                showLoginModal();
                return;
            }

            // Simulate upload
            setTimeout(() => {
                movies.unshift(movieData);
                renderMovies();
                this.reset();
                showSuccessModal(`"${movieData.title}" uploaded successfully in ${movieData.quality}!`);
            }, 2000);
        });

        // Modal functions
        function showLoginModal() {
            document.getElementById('loginModal').style.display = 'flex';
        }

        function showRegisterModal() {
            subscribe('premium');
        }

        function showSuccessModal(message) {
            document.getElementById('successMessage').textContent = message;
            document.getElementById('successModal').style.display = 'flex';
        }

        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        // Close modals on outside click
        window.onclick = function(event) {
            const modals = document.querySelectorAll('.modal');
            modals.forEach(modal => {
                if (event.target === modal) {
                    modal.style.display = 'none';
                }
            });
        }

        // Header scroll effect
        function setupScrollEffects() {
            window.addEventListener('scroll', () => {
                const header = document.getElementById('header');
                if (window.scrollY > 100) {
                    header.style.background = 'rgba(0, 0, 0, 0.98)';
                } else {
                    header.style.background = 'rgba(0, 0, 0, 0.95)';
                }
            });
        }

        // Intersection Observer for animations
        function setupIntersectionObserver() {
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            }, { threshold: 0.1 });

            document.querySelectorAll('.movie-card, .subscription-card').forEach(el => {
                el.style.opacity = '0';
                el.style.transform = 'translateY(30px)';
                el.style.transition = 'all 0.6s ease';
                observer.observe(el);
            });
        }

        // Smooth scrolling for nav links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    </script>
</body>
</html>
