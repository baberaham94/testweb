<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instagram Clone</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }
        
        body {
            background-color: #fafafa;
            color: #262626;
            line-height: 1.5;
        }
        
        .container {
            max-width: 935px;
            margin: 0 auto;
            padding: 30px 20px;
        }
        
        /* Header Styles */
        header {
            border-bottom: 1px solid #dbdbdb;
            background-color: white;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .header-content {
            max-width: 935px;
            margin: 0 auto;
            padding: 10px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-family: 'Grand Hotel', cursive;
            font-size: 24px;
        }
        
        .search-bar {
            background: #fafafa;
            border: 1px solid #dbdbdb;
            border-radius: 3px;
            padding: 5px 10px;
            width: 215px;
        }
        
        .nav-icons a {
            margin-left: 15px;
            color: #262626;
            font-size: 20px;
        }
        
        /* Profile Section */
        .profile {
            display: flex;
            margin-bottom: 44px;
            padding: 30px 0;
        }
        
        .profile-pic {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            margin-right: 30px;
            object-fit: cover;
            border: 1px solid #dbdbdb;
        }
        
        .profile-info h1 {
            font-size: 28px;
            font-weight: 300;
            margin-bottom: 12px;
        }
        
        .profile-stats {
            display: flex;
            margin-bottom: 20px;
        }
        
        .profile-stats div {
            margin-right: 40px;
        }
        
        .profile-bio h2 {
            font-size: 16px;
            font-weight: 600;
        }
        
        /* Posts Section */
        .posts-header {
            border-top: 1px solid #dbdbdb;
            display: flex;
            justify-content: center;
        }
        
        .posts-header a {
            padding: 15px 0;
            margin: 0 30px;
            text-transform: uppercase;
            font-size: 12px;
            font-weight: 600;
            letter-spacing: 1px;
            color: #8e8e8e;
            text-decoration: none;
            display: flex;
            align-items: center;
        }
        
        .posts-header a.active {
            color: #262626;
            border-top: 1px solid #262626;
        }
        
        .posts-header i {
            margin-right: 6px;
        }
        
        .posts-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 28px;
            margin-top: 30px;
        }
        
        .post {
            position: relative;
            aspect-ratio: 1;
            background-color: #efefef;
            border-radius: 3px;
            overflow: hidden;
            cursor: pointer;
        }
        
        .post img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.3s;
        }
        
        .post:hover img {
            transform: scale(1.05);
        }
        
        .carousel-post {
            position: relative;
            background-color: #000;
            border-radius: 3px;
            overflow: hidden;
            margin-bottom: 28px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        
        .carousel-container {
            position: relative;
            height: 500px;
            overflow: hidden;
        }
        
        .carousel-slides {
            display: flex;
            transition: transform 0.5s ease;
            height: 100%;
        }
        
        .carousel-slide {
            min-width: 100%;
            height: 100%;
        }
        
        .carousel-slide img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .carousel-nav {
            position: absolute;
            top: 50%;
            width: 100%;
            display: flex;
            justify-content: space-between;
            transform: translateY(-50%);
            padding: 0 10px;
        }
        
        .carousel-nav button {
            background: rgba(255, 255, 255, 0.7);
            border: none;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .carousel-dots {
            display: flex;
            justify-content: center;
            position: absolute;
            bottom: 15px;
            width: 100%;
        }
        
        .carousel-dot {
            width: 6px;
            height: 6px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.5);
            margin: 0 3px;
            cursor: pointer;
        }
        
        .carousel-dot.active {
            background: rgba(255, 255, 255, 0.9);
        }
        
        .post-header {
            display: flex;
            align-items: center;
            padding: 14px 16px;
        }
        
        .post-avatar {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            margin-right: 10px;
            object-fit: cover;
        }
        
        .post-username {
            font-weight: 600;
        }
        
        .post-actions {
            padding: 10px 16px;
            display: flex;
            justify-content: space-between;
            font-size: 24px;
        }
        
        .post-actions-left i {
            margin-right: 15px;
            cursor: pointer;
        }
        
        .post-likes {
            padding: 0 16px;
            font-weight: 600;
            margin-bottom: 8px;
        }
        
        .post-caption {
            padding: 0 16px 10px;
            display: flex;
        }
        
        .post-caption-username {
            font-weight: 600;
            margin-right: 5px;
        }
        
        .post-comments {
            padding: 0 16px 10px;
            color: #8e8e8e;
        }
        
        .post-time {
            padding: 0 16px 12px;
            color: #8e8e8e;
            font-size: 10px;
            text-transform: uppercase;
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .posts-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 3px;
            }
            
            .profile {
                flex-direction: column;
                align-items: center;
                text-align: center;
            }
            
            .profile-pic {
                margin-right: 0;
                margin-bottom: 20px;
            }
            
            .profile-stats {
                justify-content: center;
            }
            
            .search-bar {
                display: none;
            }
        }
        
        @media (max-width: 480px) {
            .posts-grid {
                grid-template-columns: 1fr;
            }
            
            .carousel-container {
                height: 400px;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="header-content">
            <div class="logo">Instagram</div>
            <div class="search-bar">
                <input type="text" placeholder="Search" style="border: none; background: transparent; width: 100%; outline: none;">
            </div>
            <div class="nav-icons">
                <a href="#"><i class="fas fa-home"></i></a>
                <a href="#"><i class="fas fa-paper-plane"></i></a>
                <a href="#"><i class="fas fa-compass"></i></a>
                <a href="#"><i class="fas fa-heart"></i></a>
                <a href="#"><i class="fas fa-user"></i></a>
            </div>
        </div>
    </header>
    
    <div class="container">
        <!-- Profile Section -->
        <section class="profile">
            <img src="https://images.unsplash.com/photo-1494790108755-2616b612b786?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=150&q=80" alt="Profile Picture" class="profile-pic">
            <div class="profile-info">
                <h1>jane_doe</h1>
                <div class="profile-stats">
                    <div><strong>125</strong> posts</div>
                    <div><strong>1,254</strong> followers</div>
                    <div><strong>872</strong> following</div>
                </div>
                <div class="profile-bio">
                    <h2>Jane Doe</h2>
                    <p>Travel enthusiast 🌍 | Photography lover 📸</p>
                    <p>📍 New York, NY</p>
                    <a href="#">www.janedoe.com</a>
                </div>
            </div>
        </section>
        
        <!-- Posts Navigation -->
        <section class="posts-header">
            <a href="#" class="active"><i class="fas fa-th"></i> Posts</a>
            <a href="#"><i class="fas fa-tv"></i> Reels</a>
            <a href="#"><i class="fas fa-bookmark"></i> Saved</a>
            <a href="#"><i class="fas fa-user-tag"></i> Tagged</a>
        </section>
        
        <!-- Posts Grid -->
        <section class="posts-grid">
            <!-- Post 1 - Single Image -->
            <div class="post">
                <img src="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" alt="Mountain landscape">
            </div>
            
            <!-- Post 2 - Single Image -->
            <div class="post">
                <img src="https://images.unsplash.com/photo-1519681393784-d120267933ba?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" alt="Snowy mountain">
            </div>
            
            <!-- Post 3 - Single Image -->
            <div class="post">
                <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" alt="Lake view">
            </div>
        </section>
        
        <!-- Carousel Post Example -->
        <section class="carousel-post">
            <div class="post-header">
                <img src="https://images.unsplash.com/photo-1494790108755-2616b612b786?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=150&q=80" alt="Profile Picture" class="post-avatar">
                <div class="post-username">jane_doe</div>
            </div>
            
            <div class="carousel-container">
                <div class="carousel-slides">
                    <div class="carousel-slide">
                        <img src="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=80" alt="Mountain landscape">
                    </div>
                    <div class="carousel-slide">
                        <img src="https://images.unsplash.com/photo-1519681393784-d120267933ba?ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=80" alt="Snowy mountain">
                    </div>
                    <div class="carousel-slide">
                        <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=80" alt="Lake view">
                    </div>
                </div>
                
                <div class="carousel-nav">
                    <button class="carousel-prev"><i class="fas fa-chevron-left"></i></button>
                    <button class="carousel-next"><i class="fas fa-chevron-right"></i></button>
                </div>
                
                <div class="carousel-dots">
                    <span class="carousel-dot active"></span>
                    <span class="carousel-dot"></span>
                    <span class="carousel-dot"></span>
                </div>
            </div>
            
            <div class="post-actions">
                <div class="post-actions-left">
                    <i class="far fa-heart"></i>
                    <i class="far fa-comment"></i>
                    <i class="far fa-paper-plane"></i>
                </div>
                <div class="post-actions-right">
                    <i class="far fa-bookmark"></i>
                </div>
            </div>
            
            <div class="post-likes">1,254 likes</div>
            
            <div class="post-caption">
                <span class="post-caption-username">jane_doe</span>
                <span>Beautiful views from my hiking trip last weekend! 🏔️ #nature #mountains #hiking</span>
            </div>
            
            <div class="post-comments">View all 42 comments</div>
            
            <div class="post-time">2 DAYS AGO</div>
        </section>
    </div>

    <script>
        // Carousel functionality
        document.addEventListener('DOMContentLoaded', function() {
            const carouselSlides = document.querySelector('.carousel-slides');
            const slides = document.querySelectorAll('.carousel-slide');
            const prevButton = document.querySelector('.carousel-prev');
            const nextButton = document.querySelector('.carousel-next');
            const dots = document.querySelectorAll('.carousel-dot');
            
            let currentSlide = 0;
            const slideCount = slides.length;
            
            // Function to update carousel position
            function updateCarousel() {
                carouselSlides.style.transform = `translateX(-${currentSlide * 100}%)`;
                
                // Update dots
                dots.forEach((dot, index) => {
                    dot.classList.toggle('active', index === currentSlide);
                });
            }
            
            // Next slide
            nextButton.addEventListener('click', function() {
                currentSlide = (currentSlide + 1) % slideCount;
                updateCarousel();
            });
            
            // Previous slide
            prevButton.addEventListener('click', function() {
                currentSlide = (currentSlide - 1 + slideCount) % slideCount;
                updateCarousel();
            });
            
            // Dot navigation
            dots.forEach((dot, index) => {
                dot.addEventListener('click', function() {
                    currentSlide = index;
                    updateCarousel();
                });
            });
            
            // Auto-advance carousel (optional)
            setInterval(function() {
                currentSlide = (currentSlide + 1) % slideCount;
                updateCarousel();
            }, 5000);
        });
    </script>
</body>
</html>
