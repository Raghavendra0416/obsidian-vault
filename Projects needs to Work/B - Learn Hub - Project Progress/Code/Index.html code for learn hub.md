Index.html code: 
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="LearnHub - Interactive Learning Platform for coding and algorithms">
    <meta name="keywords" content="learning, courses, coding, algorithms, javascript">
    <title>LearnHub - Interactive Learning Platform</title>
    
    <!-- CSS Files -->
    <link rel="stylesheet" href="./css/styles.css">
    <link rel="stylesheet" href="./css/visualizer.css">
    <link rel="stylesheet" href="./css/responsive.css">
    
    <!-- Font Awesome for icons (optional) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Google Fonts (optional) -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
</head>
<body>
    
    <!-- ========== NAVIGATION BAR ========== -->
    <nav class="navbar" id="navbar">
        <div class="nav-container">
            <!-- Logo -->
            <div class="nav-logo">
                <a href="#home">
                    <i class="fas fa-graduation-cap"></i>
                    <span>LearnHub</span>
                </a>
            </div>

            <!-- Navigation Links -->
            <ul class="nav-menu" id="navMenu">
                <li class="nav-item">
                    <a href="#home" class="nav-link active" data-page="home">
                        <i class="fas fa-home"></i>
                        Home
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#courses" class="nav-link" data-page="courses">
                        <i class="fas fa-book"></i>
                        Courses
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#quiz" class="nav-link" data-page="quiz">
                        <i class="fas fa-question-circle"></i>
                        Quiz
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#playground" class="nav-link" data-page="playground">
                        <i class="fas fa-code"></i>
                        Playground
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#visualizer" class="nav-link" data-page="visualizer">
                        <i class="fas fa-chart-bar"></i>
                        Visualizer
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#dashboard" class="nav-link" data-page="dashboard">
                        <i class="fas fa-tachometer-alt"></i>
                        Dashboard
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#profile" class="nav-link" data-page="profile">
                        <i class="fas fa-user"></i>
                        Profile
                    </a>
                </li>
            </ul>

            <!-- Search Bar -->
            <div class="nav-search">
                <input type="text" id="globalSearch" placeholder="Search courses...">
                <i class="fas fa-search"></i>
            </div>

            <!-- Theme Toggle -->
            <button class="theme-toggle" id="themeToggle" aria-label="Toggle theme">
                <i class="fas fa-moon"></i>
            </button>

            <!-- Mobile Menu Toggle -->
            <div class="hamburger" id="hamburger">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>

        <!-- Search Results Dropdown -->
        <div class="search-dropdown" id="searchDropdown"></div>
    </nav>

    <!-- ========== MAIN CONTENT AREA ========== -->
    <main class="main-content" id="mainContent">
        
        <!-- ========== HOME PAGE ========== -->
        <section class="page" id="homePage">
            
            <!-- Hero Section -->
            <div class="hero-section">
                <div class="hero-content">
                    <h1 class="hero-title">Learn <span class="highlight">Anything</span>, Anytime</h1>
                    <p class="hero-subtitle">Master coding, algorithms, and more with interactive lessons</p>
                    <div class="hero-search">
                        <input type="text" placeholder="What do you want to learn?">
                        <button class="btn btn-primary">
                            <i class="fas fa-search"></i>
                            Search
                        </button>
                    </div>
                    <div class="hero-stats">
                        <div class="stat-item">
                            <h3>50+</h3>
                            <p>Courses</p>
                        </div>
                        <div class="stat-item">
                            <h3>10K+</h3>
                            <p>Students</p>
                        </div>
                        <div class="stat-item">
                            <h3>4.8</h3>
                            <p>Rating</p>
                        </div>
                    </div>
                </div>
                <div class="hero-image">
                    <img src="./assets/hero-image.svg" alt="Learning illustration">
                </div>
            </div>

            <!-- Featured Courses Section -->
            <section class="featured-courses">
                <div class="section-header">
                    <h2>Featured Courses</h2>
                    <a href="#courses" class="view-all">View All <i class="fas fa-arrow-right"></i></a>
                </div>
                <div class="course-grid" id="featuredCoursesGrid">
                    <!-- Courses will be dynamically inserted here -->
                </div>
            </section>

            <!-- How It Works Section -->
            <section class="how-it-works">
                <h2>How It Works</h2>
                <div class="steps-container">
                    <div class="step">
                        <div class="step-icon">
                            <i class="fas fa-search"></i>
                        </div>
                        <h3>1. Browse Courses</h3>
                        <p>Explore our wide range of courses in programming, design, and more</p>
                    </div>
                    <div class="step">
                        <div class="step-icon">
                            <i class="fas fa-play"></i>
                        </div>
                        <h3>2. Start Learning</h3>
                        <p>Watch video lessons, practice coding, and take quizzes</p>
                    </div>
                    <div class="step">
                        <div class="step-icon">
                            <i class="fas fa-certificate"></i>
                        </div>
                        <h3>3. Get Certified</h3>
                        <p>Complete courses and earn certificates to showcase your skills</p>
                    </div>
                </div>
            </section>

            <!-- Categories Section -->
            <section class="categories-section">
                <h2>Popular Categories</h2>
                <div class="categories-grid">
                    <div class="category-card" data-category="Programming">
                        <i class="fas fa-code"></i>
                        <h3>Programming</h3>
                        <p>15 Courses</p>
                    </div>
                    <div class="category-card" data-category="Design">
                        <i class="fas fa-palette"></i>
                        <h3>Design</h3>
                        <p>8 Courses</p>
                    </div>
                    <div class="category-card" data-category="Business">
                        <i class="fas fa-briefcase"></i>
                        <h3>Business</h3>
                        <p>12 Courses</p>
                    </div>
                    <div class="category-card" data-category="Data Science">
                        <i class="fas fa-chart-line"></i>
                        <h3>Data Science</h3>
                        <p>10 Courses</p>
                    </div>
                </div>
            </section>

            <!-- Testimonials Section -->
            <section class="testimonials">
                <h2>What Our Students Say</h2>
                <div class="testimonials-grid" id="testimonialsGrid">
                    <!-- Testimonials will be dynamically inserted -->
                </div>
            </section>

        </section>

        <!-- ========== COURSES PAGE ========== -->
        <section class="page hidden" id="coursesPage">
            
            <div class="page-header">
                <h1>Explore Courses</h1>
                <p>Find the perfect course to boost your skills</p>
            </div>

            <div class="courses-container">
                
                <!-- Filters Sidebar -->
                <aside class="filters-sidebar">
                    <div class="filter-header">
                        <h3>Filters</h3>
                        <button class="clear-filters" id="clearFilters">Clear All</button>
                    </div>

                    <!-- Category Filter -->
                    <div class="filter-group">
                        <h4>Category</h4>
                        <label class="filter-option">
                            <input type="checkbox" name="category" value="all" checked>
                            <span>All Categories</span>
                        </label>
                        <label class="filter-option">
                            <input type="checkbox" name="category" value="Programming">
                            <span>Programming</span>
                        </label>
                        <label class="filter-option">
                            <input type="checkbox" name="category" value="Design">
                            <span>Design</span>
                        </label>
                        <label class="filter-option">
                            <input type="checkbox" name="category" value="Business">
                            <span>Business</span>
                        </label>
                        <label class="filter-option">
                            <input type="checkbox" name="category" value="Data Science">
                            <span>Data Science</span>
                        </label>
                    </div>

                    <!-- Difficulty Filter -->
                    <div class="filter-group">
                        <h4>Difficulty</h4>
                        <label class="filter-option">
                            <input type="radio" name="difficulty" value="all" checked>
                            <span>All Levels</span>
                        </label>
                        <label class="filter-option">
                            <input type="radio" name="difficulty" value="Beginner">
                            <span>Beginner</span>
                        </label>
                        <label class="filter-option">
                            <input type="radio" name="difficulty" value="Intermediate">
                            <span>Intermediate</span>
                        </label>
                        <label class="filter-option">
                            <input type="radio" name="difficulty" value="Advanced">
                            <span>Advanced</span>
                        </label>
                    </div>

                    <!-- Price Filter -->
                    <div class="filter-group">
                        <h4>Price Range</h4>
                        <div class="price-range">
                            <input type="range" id="priceRange" min="0" max="100" value="100">
                            <div class="price-labels">
                                <span>$0</span>
                                <span id="maxPrice">$100</span>
                            </div>
                        </div>
                    </div>

                    <!-- Rating Filter -->
                    <div class="filter-group">
                        <h4>Rating</h4>
                        <label class="filter-option">
                            <input type="radio" name="rating" value="all" checked>
                            <span>All Ratings</span>
                        </label>
                        <label class="filter-option">
                            <input type="radio" name="rating" value="4.5">
                            <span>4.5+ ⭐</span>
                        </label>
                        <label class="filter-option">
                            <input type="radio" name="rating" value="4.0">
                            <span>4.0+ ⭐</span>
                        </label>
                    </div>

                </aside>

                <!-- Courses Main Area -->
                <div class="courses-main">
                    
                    <!-- Sort & Results Count -->
                    <div class="courses-toolbar">
                        <div class="results-count">
                            Showing <span id="resultsCount">0</span> courses
                        </div>
                        <div class="sort-options">
                            <label>Sort by:</label>
                            <select id="sortSelect">
                                <option value="popularity">Popularity</option>
                                <option value="price-low">Price: Low to High</option>
                                <option value="price-high">Price: High to Low</option>
                                <option value="rating">Highest Rated</option>
                                <option value="newest">Newest</option>
                            </select>
                        </div>
                    </div>

                    <!-- Courses Grid -->
                    <div class="courses-grid" id="coursesGrid">
                        <!-- Courses will be dynamically inserted -->
                    </div>

                    <!-- No Results Message -->
                    <div class="no-results hidden" id="noResults">
                        <i class="fas fa-search"></i>
                        <h3>No courses found</h3>
                        <p>Try adjusting your filters</p>
                    </div>

                </div>

            </div>

        </section>

        <!-- ========== COURSE DETAIL PAGE ========== -->
        <section class="page hidden" id="courseDetailPage">
            <div class="course-detail-container">
                <!-- Content will be dynamically inserted -->
            </div>
        </section>

        <!-- ========== QUIZ PAGE ========== -->
        <section class="page hidden" id="quizPage">
            
            <!-- Quiz Selection View -->
            <div class="quiz-selection" id="quizSelection">
                <h1>Choose a Quiz</h1>
                <div class="quiz-cards" id="quizCards">
                    <!-- Quiz cards will be dynamically inserted -->
                </div>
            </div>

            <!-- Quiz Taking View -->
            <div class="quiz-container hidden" id="quizContainer">
                
                <!-- Quiz Header -->
                <div class="quiz-header">
                    <div class="quiz-info">
                        <h2 id="quizTitle">Quiz Title</h2>
                        <span class="question-counter">
                            Question <span id="currentQuestion">1</span> of <span id="totalQuestions">10</span>
                        </span>
                    </div>
                    <div class="quiz-timer">
                        <i class="fas fa-clock"></i>
                        <span id="timer">10:00</span>
                    </div>
                </div>

                <!-- Progress Bar -->
                <div class="quiz-progress">
                    <div class="progress-bar" id="quizProgressBar"></div>
                </div>

                <!-- Question Area -->
                <div class="question-area">
                    <h3 class="question-text" id="questionText"></h3>
                    <div class="options-container" id="optionsContainer">
                        <!-- Options will be dynamically inserted -->
                    </div>
                </div>

                <!-- Navigation Buttons -->
                <div class="quiz-navigation">
                    <button class="btn btn-secondary" id="prevQuestion">
                        <i class="fas fa-arrow-left"></i> Previous
                    </button>
                    <button class="btn btn-primary" id="nextQuestion">
                        Next <i class="fas fa-arrow-right"></i>
                    </button>
                    <button class="btn btn-success hidden" id="submitQuiz">
                        Submit Quiz
                    </button>
                </div>

            </div>

            <!-- Quiz Results View -->
            <div class="quiz-results hidden" id="quizResults">
                <!-- Results will be dynamically inserted -->
            </div>

        </section>

        <!-- ========== CODE PLAYGROUND PAGE ========== -->
        <section class="page hidden" id="playgroundPage">
            
            <div class="playground-container">
                
                <!-- Problem Description -->
                <div class="problem-panel">
                    <div class="panel-header">
                        <h3>Problem</h3>
                        <select id="problemSelect">
                            <option value="0">Two Sum</option>
                            <option value="1">Reverse String</option>
                            <option value="2">Palindrome Check</option>
                        </select>
                    </div>
                    <div class="problem-content" id="problemContent">
                        <!-- Problem description will be loaded here -->
                    </div>
                    <div class="test-cases">
                        <h4>Test Cases</h4>
                        <div id="testCasesDisplay"></div>
                    </div>
                </div>

                <!-- Code Editor -->
                <div class="editor-panel">
                    <div class="panel-header">
                        <h3>Code Editor</h3>
                        <button class="btn btn-secondary" id="resetCode">
                            <i class="fas fa-undo"></i> Reset
                        </button>
                    </div>
                    <textarea 
                        id="codeEditor" 
                        class="code-editor" 
                        spellcheck="false"
                        placeholder="// Write your code here..."></textarea>
                    
                    <div class="editor-actions">
                        <button class="btn btn-primary" id="runCode">
                            <i class="fas fa-play"></i> Run Code
                        </button>
                        <button class="btn btn-success" id="submitCode">
                            <i class="fas fa-check"></i> Submit
                        </button>
                    </div>

                    <!-- Output Section -->
                    <div class="output-section">
                        <h4>Output</h4>
                        <div class="output-content" id="outputContent">
                            <p class="output-placeholder">Run your code to see the output...</p>
                        </div>
                    </div>
                </div>

            </div>

        </section>

        <!-- ========== ALGORITHM VISUALIZER PAGE ========== -->
        <section class="page hidden" id="visualizerPage">
            
            <div class="visualizer-container">
                
                <!-- Controls Panel -->
                <div class="visualizer-controls">
                    <h2>Algorithm Visualizer</h2>
                    
                    <div class="control-group">
                        <label>Algorithm:</label>
                        <select id="algorithmSelect">
                            <option value="bubble">Bubble Sort</option>
                            <option value="selection">Selection Sort</option>
                            <option value="insertion">Insertion Sort</option>
                            <option value="merge">Merge Sort</option>
                            <option value="quick">Quick Sort</option>
                            <option value="binary">Binary Search</option>
                        </select>
                    </div>

                    <div class="control-group">
                        <label>Array Size: <span id="arraySizeValue">20</span></label>
                        <input type="range" id="arraySize" min="5" max="50" value="20">
                    </div>

                    <div class="control-group">
                        <label>Speed: <span id="speedValue">Medium</span></label>
                        <input type="range" id="speedControl" min="1" max="5" value="3">
                    </div>

                    <div class="control-buttons">
                        <button class="btn btn-primary" id="generateArray">
                            <i class="fas fa-random"></i> Generate Array
                        </button>
                        <button class="btn btn-success" id="startVisualization">
                            <i class="fas fa-play"></i> Start
                        </button>
                        <button class="btn btn-warning hidden" id="pauseVisualization">
                            <i class="fas fa-pause"></i> Pause
                        </button>
                        <button class="btn btn-secondary" id="resetVisualization">
                            <i class="fas fa-undo"></i> Reset
                        </button>
                    </div>

                    <!-- Binary Search Input -->
                    <div class="binary-search-input hidden" id="binarySearchInput">
                        <label>Target Number:</label>
                        <input type="number" id="targetNumber" placeholder="Enter target">
                    </div>

                    <!-- Algorithm Info -->
                    <div class="algorithm-info">
                        <h3>Algorithm Info</h3>
                        <p id="algorithmDescription"></p>
                        <div class="complexity-info">
                            <span>Time: <strong id="timeComplexity">O(n²)</strong></span>
                            <span>Space: <strong id="spaceComplexity">O(1)</strong></span>
                        </div>
                    </div>
                </div>

                <!-- Visualization Area -->
                <div class="visualization-area">
                    <div class="array-container" id="arrayContainer">
                        <!-- Array bars will be dynamically created -->
                    </div>
                    <div class="visualization-stats">
                        <div class="stat">
                            <span>Comparisons:</span>
                            <strong id="comparisons">0</strong>
                        </div>
                        <div class="stat">
                            <span>Swaps:</span>
                            <strong id="swaps">0</strong>
                        </div>
                        <div class="stat">
                            <span>Time:</span>
                            <strong id="elapsedTime">0s</strong>
                        </div>
                    </div>
                </div>

            </div>

        </section>

        <!-- ========== DASHBOARD PAGE ========== -->
        <section class="page hidden" id="dashboardPage">
            
            <div class="dashboard-header">
                <h1>My Dashboard</h1>
                <p>Track your learning progress</p>
            </div>

            <div class="dashboard-container">
                
                <!-- Stats Overview -->
                <div class="dashboard-stats">
                    <div class="stat-card">
                        <div class="stat-icon">
                            <i class="fas fa-book"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="enrolledCount">0</h3>
                            <p>Courses Enrolled</p>
                        </div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-icon">
                            <i class="fas fa-check-circle"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="completedCount">0</h3>
                            <p>Courses Completed</p>
                        </div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-icon">
                            <i class="fas fa-clock"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="hoursLearned">0</h3>
                            <p>Hours Learned</p>
                        </div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-icon">
                            <i class="fas fa-certificate"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="certificatesEarned">0</h3>
                            <p>Certificates</p>
                        </div>
                    </div>
                </div>

                <!-- Continue Learning Section -->
                <section class="dashboard-section">
                    <h2>Continue Learning</h2>
                    <div class="enrolled-courses" id="enrolledCourses">
                        <!-- Enrolled courses will be dynamically inserted -->
                    </div>
                </section>

                <!-- Progress Charts -->
                <section class="dashboard-section">
                    <h2>Learning Analytics</h2>
                    <div class="charts-container">
                        <div class="chart-card">
                            <h3>Courses by Category</h3>
                            <div class="chart" id="categoryChart"></div>
                        </div>
                        <div class="chart-card">
                            <h3>Weekly Activity</h3>
                            <div class="chart" id="activityChart"></div>
                        </div>
                    </div>
                </section>

                <!-- Learning Streak -->
                <section class="dashboard-section">
                    <h2>Learning Streak 🔥</h2>
                    <div class="streak-calendar" id="streakCalendar">
                        <!-- Calendar will be dynamically generated -->
                    </div>
                </section>

            </div>

        </section>

        <!-- ========== PROFILE PAGE ========== -->
        <section class="page hidden" id="profilePage">
            
            <div class="profile-container">
                
                <!-- Profile Header -->
                <div class="profile-header">
                    <div class="profile-avatar">
                        <img src="./assets/default-avatar.png" alt="User Avatar" id="userAvatar">
                        <button class="edit-avatar">
                            <i class="fas fa-camera"></i>
                        </button>
                    </div>
                    <div class="profile-info">
                        <h1 id="userName">John Doe</h1>
                        <p id="userBio">Passionate learner | JavaScript Developer</p>
                        <div class="profile-stats">
                            <span><i class="fas fa-calendar"></i> Joined Jan 2024</span>
                            <span><i class="fas fa-map-marker-alt"></i> San Francisco, CA</span>
                        </div>
                    </div>
                    <button class="btn btn-primary" id="editProfileBtn">
                        <i class="fas fa-edit"></i> Edit Profile
                    </button>
                </div>

                <!-- Profile Tabs -->
                <div class="profile-tabs">
                    <button class="tab-btn active" data-tab="about">About</button>
                    <button class="tab-btn" data-tab="achievements">Achievements</button>
                    <button class="tab-btn" data-tab="settings">Settings</button>
                </div>

                <!-- About Tab -->
                <div class="tab-content active" id="aboutTab">
                    <div class="about-section">
                        <h3>About Me</h3>
                        <p id="userAbout">
                            I'm a passionate learner interested in web development and algorithms.
                            Currently improving my JavaScript skills and exploring data structures.
                        </p>
                    </div>
                    <div class="skills-section">
                        <h3>Skills</h3>
                        <div class="skills-tags" id="userSkills">
                            <span class="skill-tag">JavaScript</span>
                            <span class="skill-tag">HTML/CSS</span>
                            <span class="skill-tag">React</span>
                        </div>
                    </div>
                </div>

                <!-- Achievements Tab -->
                <div class="tab-content" id="achievementsTab">
                    <h3>Badges & Achievements</h3>
                    <div class="achievements-grid" id="achievementsGrid">
                        <!-- Achievements will be dynamically inserted -->
                    </div>
                </div>

                <!-- Settings Tab -->
                <div class="tab-content" id="settingsTab">
                    <h3>Settings</h3>
                    <div class="settings-form">
                        <div class="setting-item">
                            <label>Email Notifications</label>
                            <label class="toggle-switch">
                                <input type="checkbox" id="emailNotifications" checked>
                                <span class="slider"></span>
                            </label>
                        </div>
                        <div class="setting-item">
                            <label>Dark Mode</label>
                            <label class="toggle-switch">
                                <input type="checkbox" id="darkModeToggle">
                                <span class="slider"></span>
                            </label>
                        </div>
                        <div class="setting-item">
                            <label>Language</label>
                            <select id="languageSelect">
                                <option value="en">English</option>
                                <option value="es">Spanish</option>
                                <option value="fr">French</option>
                            </select>
                        </div>
                    </div>
                </div>

            </div>

        </section>

    </main>

    <!-- ========== FOOTER ========== -->
    <footer class="footer">
        <div class="footer-container">
            <div class="footer-section">
                <h3>LearnHub</h3>
                <p>Your journey to mastering new skills starts here.</p>
                <div class="social-links">
                    <a href="#"><i class="fab fa-facebook"></i></a>
                    <a href="#"><i class="fab fa-twitter"></i></a>
                    <a href="#"><i class="fab fa-linkedin"></i></a>
                    <a href="#"><i class="fab fa-github"></i></a>
                </div>
            </div>
            <div class="footer-section">
                <h4>Quick Links</h4>
                <ul>
                    <li><a href="#courses">Courses</a></li>
                    <li><a href="#quiz">Quizzes</a></li>
                    <li><a href="#playground">Playground</a></li>
                    <li><a href="#visualizer">Visualizer</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h4>Support</h4>
                <ul>
                    <li><a href="#">Help Center</a></li>
                    <li><a href="#">Contact Us</a></li>
                    <li><a href="#">FAQ</a></li>
                    <li><a href="#">Privacy Policy</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h4>Newsletter</h4>
                <p>Subscribe to get updates on new courses</p>
                <div class="newsletter-form">
                    <input type="email" placeholder="Your email">
                    <button class="btn btn-primary">Subscribe</button>
                </div>
            </div>
        </div>
        <div class="footer-bottom">
            <p>&copy; 2024 LearnHub. All rights reserved. Built with ❤️ by You</p>
        </div>
    </footer>

    <!-- Loading Spinner (Global) -->
    <div class="loading-spinner hidden" id="loadingSpinner">
        <div class="spinner"></div>
    </div>

    <!-- Toast Notifications -->
    <div class="toast-container" id="toastContainer"></div>

    <!-- ========== JAVASCRIPT FILES ========== -->
    <!-- Data Files -->
    <script src="./js/data/courses.js"></script>
    <script src="./js/data/users.js"></script>
    <script src="./js/data/quizzes.js"></script>
    <script src="./js/data/problems.js"></script>
    
    <!-- Utility Files -->
    <script src="./js/utils/helpers.js"></script>
    <script src="./js/utils/dataGenerator.js"></script>
    <script src="./js/storage/localStorage.js"></script>
    
    <!-- Main Application -->
    <script src="./js/main.js"></script>
    
</body>
</html>
```