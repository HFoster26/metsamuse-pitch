# JavaScript Code Documentation - MetsäMuse

## Complete Line-by-Line Explanation of main.js

### 1. Page Loader Animation

```javascript
// Loader
window.addEventListener('load', () => {
    setTimeout(() => {
        document.querySelector('.loader').classList.add('hidden');
    }, 1000);
});
```

**What this does:**
- `window.addEventListener('load', ...)` - Waits for the entire page to load (including images, CSS, etc.)
- `setTimeout(..., 1000)` - Delays the code inside by 1000 milliseconds (1 second)
- `document.querySelector('.loader')` - Finds the HTML element with class "loader"
- `.classList.add('hidden')` - Adds the CSS class "hidden" to make the loader disappear
- **Purpose**: Shows a loading screen for 1 second when someone visits the site, then fades it out

---

### 2. Smooth Scrolling for Anchor Links

```javascript
// Smooth scroll
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if (target) {
            target.scrollIntoView({ behavior: 'smooth' });
        }
    });
});
```

**What this does:**
- `document.querySelectorAll('a[href^="#"]')` - Finds ALL links that start with # (like #about, #features)
- `.forEach(anchor => {...})` - Loops through each link found
- `anchor.addEventListener('click', ...)` - Adds a click handler to each link
- `e.preventDefault()` - Stops the default "jump" behavior of anchor links
- `this.getAttribute('href')` - Gets the href value (like "#about")
- `document.querySelector(...)` - Finds the element with that ID
- `target.scrollIntoView({ behavior: 'smooth' })` - Smoothly scrolls to that element
- **Purpose**: Makes internal page links scroll smoothly instead of jumping instantly

---

### 3. Mobile Menu Toggle

```javascript
// Mobile menu
const mobileToggle = document.querySelector('.mobile-toggle');
const navMenu = document.querySelector('.nav-menu');

mobileToggle?.addEventListener('click', () => {
    navMenu.classList.toggle('active');
});
```

**What this does:**
- `const mobileToggle = ...` - Stores the hamburger menu button
- `const navMenu = ...` - Stores the navigation menu
- `mobileToggle?` - The ? checks if mobileToggle exists before continuing
- `.addEventListener('click', ...)` - Runs code when hamburger is clicked
- `navMenu.classList.toggle('active')` - Adds/removes "active" class on the menu
- **Purpose**: Makes the hamburger menu work on mobile - clicking it shows/hides the navigation

---

### 4. Animated Number Counters

```javascript
// Counter animation
const animateCounters = () => {
    const counters = document.querySelectorAll('.stat-number');
    
    counters.forEach(counter => {
        const target = +counter.getAttribute('data-target');
        const increment = target / 200;
        
        const updateCounter = () => {
            const current = +counter.innerText;
            
            if (current < target) {
                counter.innerText = Math.ceil(current + increment);
                setTimeout(updateCounter, 10);
            } else {
                counter.innerText = target;
            }
        };
        
        updateCounter();
    });
};
```

**What this does:**
- `const animateCounters = () => {...}` - Creates a function to animate numbers
- `document.querySelectorAll('.stat-number')` - Finds all elements with stat-number class
- `+counter.getAttribute('data-target')` - Gets the target number from HTML (the + converts string to number)
- `const increment = target / 200` - Calculates how much to increase each time (200 steps total)
- `const updateCounter = () => {...}` - Creates inner function that updates the number
- `const current = +counter.innerText` - Gets current displayed number
- `if (current < target)` - Checks if we've reached the target
- `Math.ceil(current + increment)` - Rounds up and adds increment
- `setTimeout(updateCounter, 10)` - Calls itself again after 10ms
- **Purpose**: Makes numbers count up from 0 to their target value with animation

---

### 5. Trigger Counter Animation on Scroll

```javascript
// Trigger counter animation on scroll
const statsSection = document.querySelector('.stats-section');
let hasAnimated = false;

window.addEventListener('scroll', () => {
    if (statsSection && !hasAnimated) {
        const rect = statsSection.getBoundingClientRect();
        if (rect.top < window.innerHeight && rect.bottom >= 0) {
            animateCounters();
            hasAnimated = true;
        }
    }
});
```

**What this does:**
- `const statsSection = ...` - Finds the statistics section
- `let hasAnimated = false` - Tracks if we've already animated (prevents repeating)
- `window.addEventListener('scroll', ...)` - Runs code when user scrolls
- `if (statsSection && !hasAnimated)` - Only runs if section exists AND hasn't animated yet
- `getBoundingClientRect()` - Gets the position of the stats section relative to viewport
- `rect.top < window.innerHeight` - Checks if top of section is visible
- `rect.bottom >= 0` - Checks if bottom of section hasn't scrolled past
- `animateCounters()` - Starts the number animation
- `hasAnimated = true` - Marks as complete so it doesn't repeat
- **Purpose**: Starts number animation only when user scrolls to the stats section

---

### 6. Navbar Scroll Effects

```javascript
// Navbar scroll effect
let lastScroll = 0;
const navbar = document.querySelector('.navbar');

window.addEventListener('scroll', () => {
    const currentScroll = window.pageYOffset;
    
    if (currentScroll > 100) {
        navbar.style.background = 'rgba(255, 255, 255, 0.98)';
        navbar.style.boxShadow = '0 5px 20px rgba(0,0,0,0.1)';
    } else {
        navbar.style.background = 'rgba(255, 255, 255, 0.95)';
        navbar.style.boxShadow = 'var(--shadow)';
    }
    
    lastScroll = currentScroll;
});
```

**What this does:**
- `let lastScroll = 0` - Stores the last scroll position (for future features)
- `window.pageYOffset` - Gets how far down the page user has scrolled
- `if (currentScroll > 100)` - If scrolled more than 100 pixels
- `navbar.style.background = ...` - Makes navbar more opaque (0.98 vs 0.95)
- `navbar.style.boxShadow = ...` - Changes the shadow to be lighter
- `lastScroll = currentScroll` - Updates the stored position
- **Purpose**: Makes the navbar slightly more solid and changes shadow when scrolling

---

## Summary of Features

1. **Loading Screen**: Professional entrance animation
2. **Smooth Scrolling**: Better UX for navigation
3. **Mobile Menu**: Responsive design for phones/tablets
4. **Number Animation**: Eye-catching statistics display
5. **Scroll-Triggered Animation**: Engages users as they explore
6. **Dynamic Navbar**: Subtle visual feedback while scrolling

## Common JavaScript Concepts Used

- **Event Listeners**: Code that runs when something happens (click, scroll, load)
- **Query Selectors**: Finding HTML elements to manipulate
- **Class Manipulation**: Adding/removing CSS classes for styling
- **Conditional Statements**: if/else logic to control behavior
- **Functions**: Reusable blocks of code
- **setTimeout**: Delays code execution
- **Template Literals**: Not used here, but would look like `${variable}`

## How It All Works Together

1. Page loads → Loading screen shows
2. After 1 second → Loading screen fades out
3. User scrolls → Navbar becomes more solid
4. Stats section appears → Numbers animate up
5. User clicks menu → Navigation appears/disappears
6. User clicks anchor link → Smooth scroll to section

This creates a modern, interactive experience without being overwhelming or gimmicky.
