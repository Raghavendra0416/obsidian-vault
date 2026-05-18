## 📄 index.html Structure (No Code - Just Blueprint)

Here's what your **index.html** should contain:

---

## 🏗️ Basic HTML Document Structure

```
1. DOCTYPE declaration
2. <html> with lang attribute
3. <head> section
4. <body> section
```

---

## 📦 HEAD Section Should Include:

### Meta Tags

- Character encoding (UTF-8)
- Viewport for responsive design
- Description meta tag
- Keywords meta tag

### Title

- Page title: "LearnHub - Interactive Learning Platform"

### CSS Links

- Link to `./css/styles.css`
- Link to `./css/visualizer.css`
- Link to `./css/responsive.css`

### External Resources (Optional)

- Font Awesome CDN for icons
- Google Fonts (Poppins or similar)

---

## 🎯 BODY Section Structure

### 1. **NAVIGATION BAR** (`<nav>`)

Should contain:

- **Logo Section**
    
    - Icon (graduation cap or similar)
    - Text: "LearnHub"
    - Link to home
- **Navigation Menu** (unordered list)
    
    - Home link (id: should have data-page="home")
    - Courses link (data-page="courses")
    - Quiz link (data-page="quiz")
    - Playground link (data-page="playground")
    - Visualizer link (data-page="visualizer")
    - Dashboard link (data-page="dashboard")
    - Profile link (data-page="profile")
    - Each link needs an icon + text
- **Search Bar**
    
    - Input field (id: "globalSearch")
    - Search icon
- **Theme Toggle Button** (id: "themeToggle")
    
    - Moon/sun icon
- **Mobile Menu Toggle** (id: "hamburger")
    
    - 3 span elements (hamburger bars)
- **Search Dropdown** (id: "searchDropdown")
    
    - Empty div for search results

---

### 2. **MAIN CONTENT AREA** (`<main>`)

#### **HOME PAGE Section** (id: "homePage")

**a) Hero Section**

- Hero content area:
    - Main heading: "Learn **Anything**, Anytime"
    - Subtitle paragraph
    - Search bar with input + button
    - Stats display (3 stat items):
        - 50+ Courses
        - 10K+ Students
        - 4.8 Rating
- Hero image area (placeholder image)

**b) Featured Courses Section**

- Section header with title + "View All" link
- Course grid container (id: "featuredCoursesGrid")
    - Empty (will be filled by JavaScript)

**c) How It Works Section**

- Section title
- 3 step cards:
    - Step 1: Browse Courses (icon + text)
    - Step 2: Start Learning (icon + text)
    - Step 3: Get Certified (icon + text)

**d) Categories Section**

- Section title
- 4 category cards:
    - Programming (with data-category attribute)
    - Design
    - Business
    - Data Science
    - Each with icon, title, course count

**e) Testimonials Section**

- Section title
- Testimonials grid (id: "testimonialsGrid")
    - Empty (will be filled by JavaScript)

---

#### **COURSES PAGE Section** (id: "coursesPage", class: "hidden")

**a) Page Header**

- Title: "Explore Courses"
- Subtitle

**b) Courses Container**

**Filters Sidebar** (`<aside>`)

- Filter header:
    
    - "Filters" title
    - "Clear All" button (id: "clearFilters")
- **Category Filter Group**
    
    - Multiple checkboxes:
        - All Categories (checked)
        - Programming
        - Design
        - Business
        - Data Science
- **Difficulty Filter Group**
    
    - Radio buttons:
        - All Levels (checked)
        - Beginner
        - Intermediate
        - Advanced
- **Price Range Filter Group**
    
    - Range slider (id: "priceRange", min=0, max=100)
    - Price labels (min/max display)
- **Rating Filter Group**
    
    - Radio buttons:
        - All Ratings
        - 4.5+ Stars
        - 4.0+ Stars

**Courses Main Area**

- Toolbar:
    
    - Results count (id: "resultsCount")
    - Sort dropdown (id: "sortSelect")
        - Options: Popularity, Price Low-High, Price High-Low, Rating, Newest
- Courses grid (id: "coursesGrid")
    
    - Empty (JavaScript will populate)
- No results message (id: "noResults", class: "hidden")
    
    - Icon + message

---

#### **COURSE DETAIL PAGE Section** (id: "courseDetailPage", class: "hidden")

- Course detail container (id or class for styling)
    - Empty (JavaScript will populate based on selected course)

---

#### **QUIZ PAGE Section** (id: "quizPage", class: "hidden")

**a) Quiz Selection View** (id: "quizSelection")

- Title: "Choose a Quiz"
- Quiz cards container (id: "quizCards")
    - Empty (JavaScript fills)

**b) Quiz Taking View** (id: "quizContainer", class: "hidden")

- Quiz header:
    
    - Quiz title (id: "quizTitle")
    - Question counter (ids: "currentQuestion", "totalQuestions")
    - Timer (id: "timer")
- Progress bar (id: "quizProgressBar")
    
- Question area:
    
    - Question text (id: "questionText")
    - Options container (id: "optionsContainer")
- Navigation buttons:
    
    - Previous button (id: "prevQuestion")
    - Next button (id: "nextQuestion")
    - Submit button (id: "submitQuiz", class: "hidden")

**c) Quiz Results View** (id: "quizResults", class: "hidden")

- Empty (JavaScript will populate)

---

#### **CODE PLAYGROUND Section** (id: "playgroundPage", class: "hidden")

**a) Problem Panel**

- Panel header:
    
    - "Problem" title
    - Problem select dropdown (id: "problemSelect")
        - Options: Two Sum, Reverse String, Palindrome Check
- Problem content (id: "problemContent")
    
    - Empty (JavaScript fills)
- Test cases section (id: "testCasesDisplay")
    

**b) Editor Panel**

- Panel header:
    
    - "Code Editor" title
    - Reset button (id: "resetCode")
- Textarea (id: "codeEditor")
    
    - Placeholder: "// Write your code here..."
- Action buttons:
    
    - Run Code button (id: "runCode")
    - Submit button (id: "submitCode")
- Output section:
    
    - Title
    - Output content area (id: "outputContent")

---

#### **VISUALIZER PAGE Section** (id: "visualizerPage", class: "hidden")

**a) Controls Panel**

- Title: "Algorithm Visualizer"
    
- Algorithm select dropdown (id: "algorithmSelect")
    
    - Options: Bubble Sort, Selection Sort, Insertion Sort, Merge Sort, Quick Sort, Binary Search
- Array size slider (id: "arraySize", min=5, max=50)
    
    - Display value (id: "arraySizeValue")
- Speed slider (id: "speedControl", min=1, max=5)
    
    - Display value (id: "speedValue")
- Control buttons:
    
    - Generate Array (id: "generateArray")
    - Start (id: "startVisualization")
    - Pause (id: "pauseVisualization", class: "hidden")
    - Reset (id: "resetVisualization")
- Binary search input (id: "binarySearchInput", class: "hidden")
    
    - Input for target number (id: "targetNumber")
- Algorithm info section:
    
    - Description (id: "algorithmDescription")
    - Time complexity (id: "timeComplexity")
    - Space complexity (id: "spaceComplexity")

**b) Visualization Area**

- Array container (id: "arrayContainer")
    
    - Empty (bars created by JavaScript)
- Stats display:
    
    - Comparisons count (id: "comparisons")
    - Swaps count (id: "swaps")
    - Elapsed time (id: "elapsedTime")

---

#### **DASHBOARD PAGE Section** (id: "dashboardPage", class: "hidden")

**a) Dashboard Header**

- Title + subtitle

**b) Stats Overview**

- 4 stat cards:
    - Courses Enrolled (id: "enrolledCount")
    - Courses Completed (id: "completedCount")
    - Hours Learned (id: "hoursLearned")
    - Certificates (id: "certificatesEarned")
    - Each with icon + number + label

**c) Continue Learning Section**

- Section title
- Enrolled courses container (id: "enrolledCourses")
    - Empty (JavaScript fills)

**d) Learning Analytics**

- Section title
- 2 chart cards:
    - Category chart (id: "categoryChart")
    - Activity chart (id: "activityChart")

**e) Learning Streak**

- Section title
- Calendar container (id: "streakCalendar")

---

#### **PROFILE PAGE Section** (id: "profilePage", class: "hidden")

**a) Profile Header**

- Avatar section:
    
    - User avatar image (id: "userAvatar")
    - Edit avatar button
- Profile info:
    
    - User name (id: "userName")
    - Bio (id: "userBio")
    - Stats (joined date, location)
- Edit profile button (id: "editProfileBtn")
    

**b) Profile Tabs**

- 3 tab buttons:
    - About (data-tab="about", class: "active")
    - Achievements (data-tab="achievements")
    - Settings (data-tab="settings")

**c) Tab Contents**

**About Tab** (id: "aboutTab", class: "active")

- About section:
    - User description (id: "userAbout")
- Skills section:
    - Skills tags (id: "userSkills")

**Achievements Tab** (id: "achievementsTab")

- Title
- Achievements grid (id: "achievementsGrid")

**Settings Tab** (id: "settingsTab")

- Email notifications toggle (id: "emailNotifications")
- Dark mode toggle (id: "darkModeToggle")
- Language select (id: "languageSelect")

---

### 3. **FOOTER Section** (`<footer>`)

**a) Footer Content (4 columns)**

- Column 1: LearnHub
    
    - Logo/name
    - Tagline
    - Social media links (Facebook, Twitter, LinkedIn, GitHub icons)
- Column 2: Quick Links
    
    - Links to: Courses, Quizzes, Playground, Visualizer
- Column 3: Support
    
    - Links to: Help Center, Contact, FAQ, Privacy Policy
- Column 4: Newsletter
    
    - Newsletter signup form:
        - Email input
        - Subscribe button

**b) Footer Bottom**

- Copyright text

---

### 4. **Global Components** (outside main sections)

**a) Loading Spinner** (id: "loadingSpinner", class: "hidden")

- Spinner element

**b) Toast Container** (id: "toastContainer")

- Empty (for notifications)

---

### 5. **JavaScript File Links** (at end of body)

Link to JavaScript files in this order:

1. Data files:
    
    - `./js/data/courses.js`
    - `./js/data/users.js`
    - `./js/data/quizzes.js`
    - `./js/data/problems.js`
2. Utility files:
    
    - `./js/utils/helpers.js`
    - `./js/utils/dataGenerator.js`
    - `./js/storage/localStorage.js`
3. Main file:
    
    - `./js/main.js`

---

## 🎯 Important Notes:

### **CSS Classes to Use:**

- `.page` - for all main page sections
- `.hidden` - to hide pages initially (all except homePage)
- `.btn` - for all buttons
- `.btn-primary`, `.btn-secondary`, `.btn-success`, `.btn-warning` - button variants

### **ID Naming Convention:**

- Use camelCase: `globalSearch`, `coursesGrid`, `quizTitle`
- Be descriptive: `enrolledCourses` not just `courses`

### **Data Attributes:**

- Use `data-page` for navigation links
- Use `data-category` for category cards
- Use `data-tab` for tab buttons

### **Form Elements:**

- Use `name` attribute for radio button groups
- Use `value` attribute for all inputs
- Add `placeholder` text where helpful

---

## ✅ Structure Checklist:

Before moving to CSS, make sure you have:

- [ ] All 7 page sections created
- [ ] Every element has an ID or class for JavaScript
- [ ] Navigation links have data-page attributes
- [ ] All forms have proper input elements
- [ ] Footer with all links
- [ ] Script tags at the end
- [ ] Valid HTML5 structure

---
