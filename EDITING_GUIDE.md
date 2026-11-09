# Editing Guide — maintain the website yourself

The site is plain HTML and CSS. There is nothing to install and no build step:
**edit a file → commit → the live site updates in 1–2 minutes.**

---

## 1. How to edit (two ways)

**A. Directly on GitHub (easiest, works from any computer)**
1. Open your repository `hamid-khabiri.github.io` on github.com.
2. Click the file (e.g. `index.html`), then the **pencil icon** (Edit).
3. Use **Ctrl+F** (Cmd+F on Mac) to find the text you want to change.
4. Make the change, click **Commit changes**.

**B. On your computer (better for bigger changes)**
1. Install **Visual Studio Code** (free).
2. Open the unzipped site folder in VS Code and edit files.
3. Preview: double-click `index.html` to open it in your browser (refresh after each save).
4. Upload changed files to GitHub: repo page → **Add file → Upload files** → drag them in → **Commit changes**.
   Files with the same name are replaced.

**Uploading images / PDFs / videos:** open the folder on GitHub (e.g. `assets/figures`), then **Add file → Upload files**.

---

## 2. Golden rules (avoid breaking the page)

- Every `<tag>` you open must be closed: `<p> ... </p>`, `<div> ... </div>`, `<li> ... </li>`.
- When adding a new item, **copy a whole existing block** (from its opening tag to its closing tag), paste it right after, then change only the text.
- File names: lowercase, no spaces, e.g. `robot_demo.jpg` (not `Robot Demo.JPG`). Names are case-sensitive on GitHub.
- Special characters in text: write `&amp;` for **&**. Normal letters, numbers, commas, quotes are fine.
- If something looks wrong after a commit, open the file's **History** on GitHub and compare with the previous version, or simply revert by re-uploading the old file.

---

## 3. Where things are

| Section | File | Search for |
|---|---|---|
| Headline / intro / hero cards | `index.html` | `HERO` |
| News | `index.html` | `NEWS` |
| About text | `index.html` | `ABOUT` |
| Education | `index.html` | `EDUCATION` |
| Experience | `index.html` | `EXPERIENCE` |
| Project cards (home page) | `index.html` | `PROJECTS` |
| Publications, patents, theses | `index.html` | `PUBLICATIONS` |
| Awards | `index.html` | `AWARDS` |
| Teaching | `index.html` | `TEACHING` |
| Skills | `index.html` | `SKILLS` |
| Contact / LinkedIn | `index.html` | `CONTACT` |
| Project detail pages | `projects/<name>.html` | — |
| Colours | `styles.css` | `:root` (first lines) |

---

## 4. Copy-paste templates

### News item (paste inside `<div class="news-grid">`, newest first)
```html
<article class="content-card news-card">
  <p class="news-date">March 2027</p>
  <h3>Short headline</h3>
  <p>One or two sentences describing the update.</p>
</article>
```

### Journal paper (paste inside the "Peer-reviewed Journal Papers" list, then update the count number in `<span class="accordion-count">8</span>`)
```html
<div class="content-card publication">
  <h3>Paper Title</h3>
  <p class="publication-meta">Journal Name, Volume(Issue), pages, Year</p>
  <p class="authors">A. Author, <strong>H. Khabiri</strong>, B. Author</p>
  <div class="publication-links"><a href="https://doi.org/XXXX" target="_blank" rel="noreferrer">DOI</a></div>
</div>
```

### Award (paste inside the Awards `<div class="item-list">`)
```html
<div>
  <h3>Award name</h3>
  <p>Year · Short description.</p>
</div>
```

### Experience entry (paste inside `<div class="experience-list">`, newest first)
```html
<div class="content-card experience-card">
  <div class="logo-tile">ABC</div>
  <div>
    <h3>Company Name, City, Country</h3>
    <p class="role">Job Title</p>
    <p class="dates">Month Year – Present</p>
    <ul>
      <li>What you did and the result.</li>
      <li>Another responsibility.</li>
    </ul>
  </div>
</div>
```

### Logo instead of initials
Upload the logo to `assets/logos/` (create the folder by typing `assets/logos/` in the upload path), then replace
`<div class="logo-tile">UofA</div>` with:
```html
<img src="assets/logos/ualberta.png" alt="University of Alberta logo">
```

### LinkedIn button
In the CONTACT section, find the line starting with `<!-- Add LinkedIn here` and replace the whole line with:
```html
<a href="https://www.linkedin.com/in/YOUR-PROFILE" target="_blank" rel="noreferrer">LinkedIn</a>
```

---

## 5. Videos

### YouTube (recommended)
1. Upload the video to YouTube (Public or **Unlisted**).
2. From the video link `https://www.youtube.com/watch?v=AbC123xYz`, the **VIDEO_ID** is the part after `v=` → `AbC123xYz`.
   (For a `https://youtu.be/AbC123xYz` link it is the part after the last `/`.)
3. On a project page (`projects/....html`), paste this block **after the figure** (after `</figure>`):
```html
<div class="content-card">
  <h2>Video demonstration</h2>
  <div class="video-wrap">
    <iframe src="https://www.youtube.com/embed/VIDEO_ID" title="Project demo video"
      allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen loading="lazy"></iframe>
  </div>
  <p class="caption">Short description of what the video shows.</p>
</div>
```

### MP4 file stored in the website
Keep clips short and compressed (aim < 20 MB; GitHub web upload limit is 25 MB per file).
Upload to `assets/videos/`, then on a project page paste:
```html
<div class="content-card">
  <h2>Video demonstration</h2>
  <div class="video-wrap">
    <video src="../assets/videos/my_demo.mp4" controls muted playsinline preload="metadata"></video>
  </div>
  <p class="caption">Short description of what the video shows.</p>
</div>
```
(On `index.html` use `assets/videos/...` without the `../`.)

### A "Videos" section on the home page
1. Paste this section in `index.html` just **before** `<!-- ================= DOCUMENTS ================= -->`:
```html
<section class="section" id="videos">
  <div class="section-heading">
    <div><p class="eyebrow">Media</p><h2>Videos</h2></div>
    <p>Short demonstrations of robotic systems I designed and built.</p>
  </div>
  <div class="video-grid">
    <div class="content-card video-card">
      <div class="video-wrap">
        <iframe src="https://www.youtube.com/embed/VIDEO_ID" title="Demo video" allowfullscreen loading="lazy"></iframe>
      </div>
      <h3>Video title</h3>
      <p>One-sentence description.</p>
    </div>
    <!-- copy the video-card block above to add more videos -->
  </div>
</section>
```
2. Add it to the menu: in the `<nav class="nav">` list, add `<a href="#videos">Videos</a>` after the Projects link.

---

## 6. Adding a new project

**Step 1 — the detail page:** in the `projects` folder, copy an existing page (e.g. `wearable-hand-orthosis.html`),
save it with a new name like `my-new-robot.html`, and change the title, texts, list items and image file name.
Image paths inside project pages start with `../assets/figures/`.

**Step 2 — the card on the home page:** paste inside the right `<div class="project-grid">`:
```html
<article class="project-card">
  <div class="tag-row"><span>Tag 1</span><span>Tag 2</span><span>Tag 3</span></div>
  <img class="project-thumb" loading="lazy" src="assets/figures/my_new_robot.jpg" alt="My new robot">
  <h3>Project Title</h3>
  <p class="project-affiliation"><strong>Affiliation:</strong> Organization, Country</p>
  <p>Two-sentence summary of the project and your role.</p>
  <a class="text-link" href="projects/my-new-robot.html">Read project →</a>
</article>
```

To remove a project, delete its `<article class="project-card"> ... </article>` block (and the page in `projects/` if you want).

---

## 7. Replace the Resume / CV
Upload new PDFs to `assets/resumes/` with exactly these names (they will overwrite the old ones):
- `Hamid_Khabiri_Resume.pdf`
- `Hamid_Khabiri_CV.pdf`

Tip: after updating a PDF, your browser may still show the old one — press **Ctrl+F5** (Cmd+Shift+R on Mac) to refresh.

---

## 8. Change colours
At the top of `styles.css`, change `--accent: #2354d6;` (blue) to another colour code, e.g. `#0f766e` (teal).
Use a colour picker website to find codes.

---

## 9. Optional: custom domain later
If you buy a domain (e.g. `hamidkhabiri.com`): repo **Settings → Pages → Custom domain**, enter it, and follow GitHub's DNS instructions.
