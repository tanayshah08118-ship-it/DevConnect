# Social Media Profile Page — Learning Guide & Skeleton

This guide breaks down the architecture, HTML5 skeleton, key concepts, and Bootstrap 5 techniques used to build this professional, responsive social media profile page.

---

## 1. Project Skeleton (Architecture Overview)

A well-structured web application separates concerns into semantic areas:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Social Media Profile</title>
  <!-- 1. External Stylesheets (Bootstrap 5 + Icons) -->
</head>
<body>

  <!-- 2. Top Navigation Bar (Fixed) -->
  <header>
    <nav class="navbar navbar-expand-lg fixed-top ...">
      <!-- Brand Logo, Search Bar, Navigation Links & Profile Dropdown -->
    </nav>
  </header>

  <!-- 3. Main Content Wrapper -->
  <main class="container my-4">

    <!-- Profile Header / Banner Card -->
    <section class="card profile-header ...">
      <!-- Cover photo banner -->
      <!-- Overlapping round avatar -->
      <!-- User full name, headline, location, action buttons -->
    </section>

    <!-- Main 3-Column Responsive Grid -->
    <div class="row g-4">
      
      <!-- Left Sidebar (Col 12 -> Md 5 -> Lg 3) -->
      <aside class="col-12 col-md-5 col-lg-3">
        <!-- Analytics & Stats Card -->
        <!-- About & Bio Card -->
        <!-- Shortcuts & Saved Items -->
      </aside>

      <!-- Center Activity Feed (Col 12 -> Md 7 -> Lg 6) -->
      <section class="col-12 col-md-7 col-lg-6">
        <!-- Post creation box ("What's on your mind?") -->
        <!-- Feed filter / sorting bar -->
        <!-- Post Cards (<article class="card feed-card">) -->
      </section>

      <!-- Right Sidebar (Col 12 -> Lg 3, hidden on mobile/tablet) -->
      <aside class="col-12 col-lg-3 d-none d-lg-block">
        <!-- Suggested connections -->
        <!-- Trending topics / hashtags -->
        <!-- Skills & badges -->
        <!-- Mini footer links -->
      </aside>

    </div><!-- /row -->

  </main>

  <!-- 4. Interactive Modals (Create Post, Edit Profile, Contact Info) -->
  <div class="modal fade" id="createPostModal">...</div>
  <div class="modal fade" id="editProfileModal">...</div>

  <!-- 5. Bootstrap JavaScript Bundle & Event Handlers -->
  <script src="...bootstrap.bundle.min.js"></script>
</body>
</html>
```

---

## 2. Core Concepts You Need to Learn

### A. Semantic HTML5 Elements
Instead of building everything with generic `<div>` tags, HTML5 provides meaningful tags that improve SEO, accessibility (screen readers), and code readability:
* `<header>`: The introductory header of the document or a specific section.
* `<nav>`: Dedicated navigation landmark for screen readers.
* `<main>`: The dominant, central content area of the `<body>`. Only one `<main>` should exist per page.
* `<section>`: A standalone section of functionality or thematic content (e.g., Profile Header, Center Feed).
* `<aside>`: Content indirectly related to the main content (e.g., sidebars, suggested connections, stats).
* `<article>`: Self-contained, independently distributable content units (ideal for social media posts).
* `<time>`: Machine-readable dates and timestamps (`<time datetime="2026-11-02">3 hrs ago</time>`).
* `<figure>` and `<figcaption>`: Encapsulates media (images, diagrams) with optional captions.

---

### B. Bootstrap 5 Grid System
Bootstrap’s grid is built on a 12-column layout and CSS Flexbox:
1. **Container (`.container` or `.container-fluid`)**: Centers content horizontally and provides responsive padding.
2. **Row (`.row`)**: Wraps columns, ensures proper alignment, and removes negative margins.
3. **Column (`.col-*`)**: Defines how many of the 12 columns an element occupies at different screen widths.
4. **Gutters (`.g-3`, `.g-4`)**: Controls the horizontal and vertical gaps between grid columns.

#### Responsive Breakpoints:
| Breakpoint | Class Infix | Screen Width | Behavior in this Project |
| :--- | :--- | :--- | :--- |
| Extra Small | `<col-12>` | `< 576px` | Full width on mobile phones |
| Small | `<col-sm-*>` | `≥ 576px` | Search bar & icons expand |
| Medium | `<col-md-*>` | `≥ 768px` | Splits into 2-columns (Sidebar: 5, Feed: 7) |
| Large | `<col-lg-*>` | `≥ 992px` | Splits into 3-columns (3 / 6 / 3) |
| Extra Large | `<col-xl-*>` | `≥ 1200px` | Crisp desktop viewing width |

---

### C. Key Bootstrap 5 Components Used
1. **Navbar (`.navbar`, `.navbar-expand-lg`, `.fixed-top`)**:
   * Creates the fixed header that sticks to the top during scrolling.
   * Collapses cleanly into a hamburger menu on small devices via `.navbar-toggler` and `.collapse`.
2. **Cards (`.card`, `.card-header`, `.card-body`, `.card-footer`)**:
   * Used for the profile header, statistical widgets, post creation box, and individual posts.
   * `.card-footer` cleanly separates interactive action buttons (Like, Comment, Repost, Send).
3. **Buttons & Button Groups (`.btn`, `.btn-primary`, `.btn-outline-*`, `.btn-sm`, `.rounded-pill`)**:
   * Provides consistent button shapes, hover states, and color hierarchy.
4. **Badges (`.badge`, `.bg-primary-subtle`, `.rounded-pill`)**:
   * Highlights metrics (e.g., notification counts, verified status, tags).
5. **Modals (`.modal`, `.modal-dialog-centered`)**:
   * Provides non-intrusive interactive popups for "Create Post", "Edit Profile", and "Contact Info".
6. **Dropdowns (`.dropdown`, `.dropdown-toggle`, `.dropdown-menu`)**:
   * Used in post action options (`...`), profile settings, and feed sorting.
7. **Collapse (`.collapse`)**:
   * Toggles the interactive comment thread beneath each post without requiring a page reload.

---

### D. Bootstrap Utility Classes
Bootstrap 5 includes hundreds of utility classes that eliminate the need for verbose custom CSS:
* **Flexbox**:
  * `d-flex`: Activates flex container.
  * `align-items-center`: Vertically centers items.
  * `justify-content-between`: Pushes left and right content to opposite edges.
  * `flex-wrap`: Allows items to wrap on narrow screens.
  * `gap-2`, `gap-3`: Consistent spacing between flex children.
* **Spacing**:
  * `m-*` (margin), `p-*` (padding), `my-4` (vertical margin), `px-3` (horizontal padding).
* **Borders & Shadows**:
  * `border-0`: Removes default borders.
  * `rounded-3`, `rounded-circle`, `rounded-pill`: Smooth corners or circular avatars.
  * `shadow-sm`: Subtle elevation effect.
* **Visibility / Responsive Display**:
  * `d-none d-lg-block`: Completely hides an element on mobile/tablet and displays it as a block element on screens `≥ 992px`.

---

## 3. How the Assignment Requirements Were Met

| Requirement | Implementation Detail |
| :--- | :--- |
| **Fixed Top Navbar** | `<nav class="navbar navbar-expand-lg fixed-top bg-white border-bottom shadow-sm">` with search, badge counters, and profile dropdown menu. |
| **Cover Photo Banner** | `.profile-cover-img` with responsive height, modern gradient, and camera change trigger. |
| **Overlapping Round Avatar** | `.rounded-circle profile-avatar-img shadow` positioned with negative top margin (`-85px`) and online badge. |
| **User Details & Actions** | Name with verified badge, Headline, Location, Followers count, "Open to Work" alert, plus Edit Profile, Connect, and Message buttons. |
| **3-Column Grid Layout** | Left Sidebar (`col-lg-3`), Center Feed (`col-lg-6`), Right Sidebar (`col-lg-3`). |
| **Post Creation Box** | "What's on your mind?" trigger with media, event, article, and poll shortcuts. Opens interactive modal. |
| **Card Components** | Standardized `.card` architecture with author header, post body, responsive image, metrics counter, and footer actions. |
| **Engagement Links** | Like (with live count increment), Comment (collapsible thread with instant submission), Repost, and Send. |
| **Responsive Collapse** | Mobile hamburger navigation, responsive avatar size, and right sidebar hides on tablets (`d-none d-lg-block`). |

---

## 4. How to Run and Test

1. Open File Explorer to:
   ```
   C:\Users\tanay\.gemini\antigravity\scratch\social-media-profile\
   ```
2. Double-click [index.html](file:///C:/Users/tanay/.gemini/antigravity/scratch/social-media-profile/index.html) to open it in Chrome, Edge, or any modern web browser.
3. **Test Responsiveness**:
   * Press `F12` to open Chrome DevTools.
   * Click the Device Toggle icon (`Ctrl + Shift + M` / `Cmd + Shift + M`).
   * Test mobile sizes (e.g. iPhone SE 375px, Pixel 7 412px, iPad 768px, and Laptop 1200px+).
4. **Test Interactivity**:
   * Click **Like** on any post to watch the counter increment and style update.
   * Click **Comment** to expand the comment thread and submit a test comment.
   * Click **"What's on your mind?"** to open the modal and publish a new post to the feed.
   * Click **"Edit Profile"** to update your name or headline live.
