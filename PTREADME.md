# Page Template Guide - MetsäMuse

## Quick Start Guide for Creating New Pages

This guide shows you how to create consistent pages for the MetsäMuse website using our template system.

---

## Step 1: Copy the Template

Copy this template code to create your new page:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PAGE_TITLE - MetsäMuse</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <!-- Loading Screen -->
    <div class="loader">
        <div class="loader-content">
            <div class="tree-loader"></div>
            <p>Entering the forest...</p>
        </div>
    </div>

    <!-- Navigation Bar - DO NOT EDIT -->
    <nav class="navbar">
        <div class="nav-container">
            <div class="nav-logo">
                <span class="logo-icon">🌲</span>
                <span class="logo-text">MetsäMuse</span>
            </div>
            <div class="nav-menu">
                <a href="index.html" class="nav-link">Home</a>
                <a href="about.html" class="nav-link">About</a>
                <a href="features.html" class="nav-link">Features</a>
                <a href="audience.html" class="nav-link">Audience</a>
                <a href="team.html" class="nav-link">Team</a>
            </div>
            <div class="mobile-toggle">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>

    <!-- Page Header -->
    <section class="page-header">
        <div class="container">
            <h1>PAGE_HEADING</h1>
            <p class="page-subtitle">PAGE_SUBTITLE</p>
        </div>
    </section>

    <!-- Main Content -->
    <section class="content-section">
        <div class="container">
            <!-- ============ TEAM: ADD YOUR CONTENT HERE ============ -->
            
            <!-- CONTENT GOES HERE -->
            
            <!-- ============ END CONTENT AREA ============ -->
        </div>
    </section>

    <!-- Footer - DO NOT EDIT WITHOUT PERMISSION -->
    <footer class="footer">
        <div class="footer-content">
            <div class="footer-section">
                <h4>MetsäMuse</h4>
                <p>Connecting people with Finland's forest heritage through digital innovation.</p>
            </div>
            <div class="footer-section">
                <h4>Quick Links</h4>
                <a href="#">Privacy Policy</a>
                <a href="#">Terms of Service</a>
                <a href="#">Contact</a>
            </div>
            <div class="footer-section">
                <h4>Connect</h4>
                <div class="social-links">
                    <a href="#">GitHub</a>
                    <a href="#">Twitter</a>
                    <a href="#">Instagram</a>
                </div>
            </div>
        </div>
        <div class="footer-bottom">
            <p>&copy; 2025 MetsäMuse - CHI Fellowship Project</p>
        </div>
    </footer>

    <!-- JavaScript - DO NOT EDIT -->
    <script src="js/main.js"></script>
</body>
</html>
```

---

## Step 2: Replace Placeholders

Replace these placeholders with your page-specific content:

| Placeholder | What to Replace With | Example |
|-------------|---------------------|---------|
| `PAGE_TITLE` | Browser tab title | "About" |
| `PAGE_HEADING` | Main page heading | "About MetsäMuse" |
| `PAGE_SUBTITLE` | Descriptive subtitle | "Bridging Technology and Forest Heritage" |

---

## Step 3: Add Active Class

Add the `active` class to YOUR page's navigation link:

```html
<!-- For About page -->
<a href="about.html" class="nav-link active">About</a>

<!-- For Features page -->
<a href="features.html" class="nav-link active">Features</a>

<!-- For Audience page -->
<a href="audience.html" class="nav-link active">Audience</a>

<!-- For Team page -->
<a href="team.html" class="nav-link active">Team</a>
```

---

## Step 4: Add Your Content

Place your content between the marked sections:

```html
<!-- ============ TEAM: ADD YOUR CONTENT HERE ============ -->

<h2>Your Section Title</h2>
<p>Your paragraph text goes here...</p>

<h3>Subsection Title</h3>
<ul>
    <li>Bullet point 1</li>
    <li>Bullet point 2</li>
    <li>Bullet point 3</li>
</ul>

<!-- ============ END CONTENT AREA ============ -->
```

---

## Page-Specific Instructions

### About Page (about.html)
- **Title**: "About - MetsäMuse"
- **Heading**: "About MetsäMuse"
- **Subtitle**: "Bridging Technology and Forest Heritage"
- **Content**: Use Project Description section from vision document

### Features Page (features.html)
- **Title**: "Features - MetsäMuse"
- **Heading**: "Features & Technology"
- **Subtitle**: "Innovation Meets Nature"
- **Content**: Use Functionality & Technology section from vision document

### Audience Page (audience.html)
- **Title**: "Audience - MetsäMuse"
- **Heading**: "Who We Serve"
- **Subtitle**: "Connecting Communities with Their Heritage"
- **Content**: Use Audience section from vision document

### Team Page (team.html)
- **Title**: "Team - MetsäMuse"
- **Heading**: "Meet the Team"
- **Subtitle**: "The People Behind MetsäMuse"
- **Content**: Create team member cards using this structure:

```html
<div class="team-grid">
    <div class="team-member">
        <img src="images/team-member-1.jpg" alt="Team Member Name">
        <h3>Member Name</h3>
        <p class="role">Project Role</p>
        <p>Brief bio about the team member...</p>
    </div>
    <!-- Repeat for each team member -->
</div>
```

---

## Available HTML Elements

Use these pre-styled elements in your content:

### Headings
```html
<h2>Main Section Heading</h2>
<h3>Subsection Heading</h3>
<h4>Minor Heading</h4>
```

### Text Elements
```html
<p>Regular paragraph text</p>
<p class="lead">Emphasized intro paragraph</p>
<strong>Bold text</strong>
<em>Italic text</em>
```

### Lists
```html
<!-- Unordered list -->
<ul>
    <li>Item one</li>
    <li>Item two</li>
</ul>

<!-- Ordered list -->
<ol>
    <li>First step</li>
    <li>Second step</li>
</ol>
```

### Buttons
```html
<button class="btn-primary">Primary Action</button>
<button class="btn-secondary">Secondary Action</button>
```

### Cards
```html
<div class="feature-card">
    <div class="feature-icon">🌲</div>
    <h3>Card Title</h3>
    <p>Card description text</p>
</div>
```

---

## DO NOT EDIT Sections

These sections should remain unchanged across all pages:
- Navigation bar structure
- Footer content (without permission)
- JavaScript file link
- Loading screen

---

## Tips for Success

1. **Test locally** before pushing to GitHub
2. **Keep content concise** - users don't read long paragraphs
3. **Use headings** to break up content
4. **Include visuals** where appropriate
5. **Check mobile view** - resize browser to test

---

## Need Help?

- Check existing pages for examples
- Review CSS documentation for available styles
- Ask the Harry for clarification in Mattermost
- Test changes locally first
- Don't committ changes to the main branch until the whole team approves

Remember: The goal is consistency across all pages while allowing flexibility in content!
