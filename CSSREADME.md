# CSS Code Documentation - MetsäMuse

## Complete Line-by-Line Explanation of style.css

### 1. CSS Reset and Box Model

```css
/* Modern CSS Reset and Variables */
*, *::before, *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

**What this does:**
- `*` - Selects EVERY element on the page
- `*::before, *::after` - Also selects pseudo-elements (decorative elements)
- `margin: 0; padding: 0` - Removes all default spacing browsers add
- `box-sizing: border-box` - Makes width/height calculations include padding and borders
- **Purpose**: Creates consistent styling across all browsers by removing defaults

---

### 2. CSS Custom Properties (Variables)

```css
:root {
    --primary: #2d5a3d;          /* Deep forest green */
    --primary-dark: #1e3a29;     /* Darker forest green */
    --secondary: #7a9a7e;        /* Sage green */
    --accent: #a3b88c;          /* Moss green accent */
    --light: #f5f3f0;           /* Off-white background */
    --dark: #1a1a1a;            /* Almost black */
    --gray: #6b6b6b;            /* Medium gray */
    --white: #ffffff;           /* Pure white */
    
    --shadow: 0 10px 30px rgba(0,0,0,0.1);        /* Standard shadow */
    --shadow-hover: 0 20px 40px rgba(0,0,0,0.15); /* Deeper shadow on hover */
    
    --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1); /* Smooth animation */
}
```

**What this does:**
- `:root` - Defines variables available everywhere in the CSS
- `--variable-name` - Creates reusable values (like constants in programming)
- Color values - Hex codes for consistent color scheme
- Shadow values - Reusable drop shadow effects
- Transition - Standard animation timing for smooth effects
- **Purpose**: Change colors/styles in ONE place instead of hundreds

---

### 3. Base Typography and Body Styles

```css
body {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    line-height: 1.6;
    color: var(--dark);
    background-color: var(--light);
    overflow-x: hidden;
}
```

**What this does:**
- `font-family` - Uses system fonts (matches user's OS for familiar look)
- `line-height: 1.6` - Makes text 1.6x taller than font size (easier to read)
- `color: var(--dark)` - Uses our dark variable for text color
- `background-color: var(--light)` - Off-white background
- `overflow-x: hidden` - Prevents horizontal scrollbar
- **Purpose**: Sets default styles for the entire page

---

### 4. Loading Screen Styles

```css
.loader {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: var(--light);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 9999;
    transition: opacity 0.5s, visibility 0.5s;
}

.loader.hidden {
    opacity: 0;
    visibility: hidden;
}
```

**What this does:**
- `position: fixed` - Stays in place even when scrolling
- `top: 0; left: 0; width: 100%; height: 100%` - Covers entire screen
- `display: flex; align-items: center; justify-content: center` - Centers content
- `z-index: 9999` - Ensures it appears on top of everything
- `transition` - Animates the fade out over 0.5 seconds
- `.loader.hidden` - Makes it invisible when JavaScript adds "hidden" class
- **Purpose**: Full-screen loading overlay that fades out smoothly

---

### 5. Loading Animation

```css
.tree-loader {
    width: 50px;
    height: 50px;
    border: 3px solid var(--secondary);
    border-top-color: var(--primary);
    border-radius: 50%;
    animation: spin 1s linear infinite;
}

@keyframes spin {
    to { transform: rotate(360deg); }
}
```

**What this does:**
- Creates a 50x50 pixel circle
- `border: 3px solid` - Makes a ring with secondary color
- `border-top-color` - Makes top part primary color
- `border-radius: 50%` - Makes it circular
- `animation: spin 1s linear infinite` - Rotates continuously
- `@keyframes spin` - Defines the rotation animation
- **Purpose**: Creates a spinning circle loader animation

---

### 6. Navigation Bar Base Styles

```css
.navbar {
    position: fixed;
    top: 0;
    width: 100%;
    background: rgba(255, 255, 255, 0.95);
    backdrop-filter: blur(10px);
    box-shadow: var(--shadow);
    z-index: 1000;
    transition: var(--transition);
}
```

**What this does:**
- `position: fixed; top: 0` - Sticks to top of screen
- `background: rgba(255, 255, 255, 0.95)` - Semi-transparent white
- `backdrop-filter: blur(10px)` - Blurs content behind navbar
- `box-shadow` - Adds subtle shadow below
- `z-index: 1000` - Keeps navbar above content but below loader
- **Purpose**: Creates a modern "frosted glass" navigation bar

---

### 7. Navigation Container and Logo

```css
.nav-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 1rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.nav-logo {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 1.5rem;
    font-weight: 600;
    color: var(--primary);
}
```

**What this does:**
- `max-width: 1200px` - Limits width on large screens
- `margin: 0 auto` - Centers the container
- `display: flex` - Makes children align horizontally
- `justify-content: space-between` - Pushes logo and menu to opposite sides
- `gap: 0.5rem` - Space between tree emoji and text
- **Purpose**: Creates responsive navbar layout with centered content

---

### 8. Navigation Links and Hover Effects

```css
.nav-link {
    text-decoration: none;
    color: var(--gray);
    font-weight: 500;
    position: relative;
    transition: var(--transition);
}

.nav-link::after {
    content: '';
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 0;
    height: 2px;
    background: var(--primary);
    transition: width 0.3s;
}

.nav-link:hover::after, .nav-link.active::after {
    width: 100%;
}
```

**What this does:**
- `text-decoration: none` - Removes underline from links
- `position: relative` - Allows positioning of ::after element
- `::after` - Creates invisible element below each link
- `content: ''` - Required for ::after to appear
- `width: 0` - Starts with no width (invisible)
- On hover/active - Width becomes 100% creating underline animation
- **Purpose**: Creates animated underline effect on hover

---

### 9. Mobile Menu Button

```css
.mobile-toggle {
    display: none;
    flex-direction: column;
    gap: 4px;
    cursor: pointer;
}

.mobile-toggle span {
    width: 25px;
    height: 3px;
    background: var(--primary);
    transition: var(--transition);
}
```

**What this does:**
- `display: none` - Hidden by default (desktop)
- `flex-direction: column` - Stacks the three lines vertically
- Three `span` elements create hamburger menu lines
- `cursor: pointer` - Shows hand cursor on hover
- **Purpose**: Creates the three-line hamburger menu icon

---

### 10. Hero Section Layout

```css
.hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    margin-top: 70px;
}
```

**What this does:**
- `min-height: 100vh` - At least full screen height (vh = viewport height)
- `display: flex` - Enables flexbox centering
- `align-items: center` - Centers vertically
- `justify-content: center` - Centers horizontally
- `margin-top: 70px` - Accounts for fixed navbar height
- **Purpose**: Creates full-screen hero section with centered content

---

### 11. Hero Background and Image Effects

```css
.hero-image {
    max-width: 500px;
    width: 100%;
    height: auto;
    border-radius: 20px;
    box-shadow: var(--shadow);
    transition: var(--transition);
}

.hero-image:hover {
    transform: translateY(-10px);
    box-shadow: var(--shadow-hover);
}
```

**What this does:**
- `max-width: 500px` - Limits size on large screens
- `width: 100%` - Responsive sizing
- `border-radius: 20px` - Rounded corners
- On hover - Moves up 10px and deepens shadow
- **Purpose**: Makes hero image responsive with hover effect

---

### 12. Floating Leaf Animation

```css
.floating-leaf {
    position: absolute;
    font-size: 2rem;
    animation: float 6s ease-in-out infinite;
}

@keyframes float {
    0%, 100% { transform: translateY(0) rotate(0); }
    50% { transform: translateY(-20px) rotate(180deg); }
}
```

**What this does:**
- `position: absolute` - Positions leaves over the image
- `animation: float` - Applies floating animation
- `6s` - Takes 6 seconds for one complete animation
- `ease-in-out` - Smooth acceleration/deceleration
- `infinite` - Loops forever
- Keyframes - Moves up 20px and rotates at midpoint
- **Purpose**: Creates gentle floating effect for decorative leaves

---

### 13. Button Styles

```css
.btn-primary, .btn-secondary {
    padding: 1rem 2.5rem;
    border: none;
    border-radius: 50px;
    font-size: 1rem;
    font-weight: 500;
    cursor: pointer;
    transition: var(--transition);
}

.btn-primary {
    background: var(--primary);
    color: var(--white);
}

.btn-primary:hover {
    background: var(--primary-dark);
    transform: translateY(-2px);
    box-shadow: var(--shadow);
}
```

**What this does:**
- `padding: 1rem 2.5rem` - Creates pill-shaped button
- `border-radius: 50px` - Fully rounded ends
- Primary button - Solid color background
- Secondary button - Transparent with border
- Hover effects - Slight lift and shadow
- **Purpose**: Creates consistent, interactive button styles

---

### 14. Scroll Indicator Animation

```css
.mouse {
    width: 30px;
    height: 50px;
    border: 2px solid var(--gray);
    border-radius: 25px;
    margin: 1rem auto;
    position: relative;
}

.mouse::after {
    content: '';
    width: 4px;
    height: 10px;
    background: var(--gray);
    position: absolute;
    top: 10px;
    left: 50%;
    transform: translateX(-50%);
    animation: scroll 2s infinite;
}

@keyframes scroll {
    0% { opacity: 1; top: 10px; }
    100% { opacity: 0; top: 20px; }
}
```

**What this does:**
- Creates mouse-shaped outline
- `::after` creates the scrolling dot inside
- Animation moves dot down while fading out
- Loops every 2 seconds
- **Purpose**: Visual hint to encourage scrolling

---

### 15. Feature Cards and Hover Effects

```css
.feature-card {
    background: var(--light);
    padding: 2rem;
    border-radius: 15px;
    text-align: center;
    transition: var(--transition);
}

.feature-card:hover {
    transform: translateY(-10px);
    box-shadow: var(--shadow);
}
```

**What this does:**
- Creates card with light background
- Rounded corners for modern look
- On hover - Lifts up with shadow
- **Purpose**: Interactive cards that respond to user interaction

---

### 16. Responsive Grid Layouts

```css
.features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}
```

**What this does:**
- `display: grid` - Uses CSS Grid layout
- `repeat(auto-fit, minmax(300px, 1fr))` - Creates responsive columns
- Columns are minimum 300px wide
- Automatically adjusts number of columns based on space
- `gap: 2rem` - Space between cards
- **Purpose**: Creates responsive layout that works on all screen sizes

---

### 17. Mobile Responsive Styles

```css
@media (max-width: 768px) {
    .nav-menu {
        display: none;
    }
    
    .mobile-toggle {
        display: flex;
    }
    
    .hero-title {
        font-size: 2.5rem;
    }
}
```

**What this does:**
- `@media (max-width: 768px)` - Only applies on screens smaller than 768px
- Hides desktop menu
- Shows mobile hamburger menu
- Reduces font sizes for mobile
- **Purpose**: Adapts layout for phones and tablets

---

## CSS Concepts Summary

1. **Flexbox**: Used for navigation, hero section, centering
2. **CSS Grid**: Used for responsive card layouts
3. **Custom Properties**: Variables for consistent theming
4. **Transitions**: Smooth animations on hover/interaction
5. **Keyframe Animations**: Complex animations like spinning, floating
6. **Media Queries**: Responsive design for different screens
7. **Pseudo-elements**: ::before and ::after for decorative elements
8. **Transform**: Moving, rotating, scaling elements
9. **Position**: Fixed, absolute, relative positioning
10. **Modern Effects**: Backdrop blur, RGBA transparency

## How The CSS Architecture Works

1. **Reset & Variables**: Foundation for consistency
2. **Layout Components**: Navigation, sections, grids
3. **Interactive Elements**: Buttons, links, cards
4. **Animations**: Loading, floating, scrolling effects
5. **Responsive Design**: Mobile-first approach
6. **Utility Classes**: Reusable styles across pages
