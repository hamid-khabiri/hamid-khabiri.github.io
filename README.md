# Hamid Khabiri — Portfolio Website

Static portfolio site (HTML + CSS only, no build step) for **https://hamid-khabiri.github.io**.

**To add or change content yourself (news, papers, projects, videos, logos), see [EDITING_GUIDE.md](EDITING_GUIDE.md).**

## Folder structure

```
index.html                 Main page (all sections)
styles.css                 All styling — colours are at the top (:root)
favicon.svg                Browser-tab icon
projects/*.html            One detail page per project
assets/figures/            Project images + profile photo
assets/resumes/            Hamid_Khabiri_Resume.pdf, Hamid_Khabiri_CV.pdf
.nojekyll                  Tells GitHub Pages to serve files as-is
```

## Publish on GitHub Pages (one time)

1. Sign in at github.com as **hamid-khabiri**.
2. Click **New repository**. Name it exactly `hamid-khabiri.github.io`, set it to **Public**, and create it (no README needed).
3. On the empty repo page click **uploading an existing file**.
4. Drag in **everything inside** this folder (index.html, styles.css, favicon.svg, .nojekyll, README.md, and the `assets` and `projects` folders). Click **Commit changes**.
   - If `.nojekyll` is hidden on your computer, skip it — the site still works.
5. Go to **Settings → Pages**. Under *Build and deployment* choose **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
6. After 1–2 minutes the site is live at **https://hamid-khabiri.github.io**.

## Updating content

| What | How |
|---|---|
| Profile photo | Upload a portrait photo named `profile.jpg` to `assets/figures/` (about 4:5 ratio). No code change needed. |
| 3-DOF upper-limb robot photo | Upload `upper_limb_rehab_robot.jpg` to `assets/figures/`. |
| Cell-culture incubator photo | Upload `cell_culture_incubator.jpg` to `assets/figures/`. |
| Resume / CV | Replace the PDFs in `assets/resumes/` (keep the same file names). |
| University / company logos | Add the image to `assets/logos/` and replace `<div class="logo-tile">TUMS</div>` with `<img src="assets/logos/tums.png" alt="TUMS logo">` in `index.html`. |
| LinkedIn | In `index.html`, Contact section, un-comment the LinkedIn line and paste your profile URL. |
| News | Edit the `news-card` blocks near the top of `index.html`; copy one block to add a new item. |
| Text on a project page | Edit the matching file in `projects/`. |

Until a photo is uploaded, a neutral placeholder is shown automatically.

To edit a file directly on GitHub: open it in the repo, click the pencil icon, change it, then **Commit changes**. The live site updates within a minute or two.
