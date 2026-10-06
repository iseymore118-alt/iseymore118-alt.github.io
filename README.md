# Isaiah Seymore — personal website

A complete, editable static portfolio. No packages, framework, paid services, or build step. The site contains Home, Projects, About, Engineering Time Machine, Notes, and a résumé overview. Project/post lists start empty; no work experience or opinions have been invented. Confirm the background copy before publishing.

## Preview

Open index.html directly, or run `python3 -m http.server 8000` in this folder and visit http://localhost:8000. All links are relative, so the site also works beneath a GitHub project path. Templates are .txt files so unfinished content is not presented as a website page.

## Publish on GitHub Pages

1. Create a public repository (for example personal-website).
2. Upload the CONTENTS of this folder to the repository root, not the enclosing folder. Include assets, CNAME, and .nojekyll. Keep templates and README if you want them available in your repository.
3. Under Settings → Pages, choose Deploy from a branch → main → / (root) → Save.
4. Set Custom domain to isaiahseymore.com before changing DNS. Verify domain ownership using GitHub’s documented TXT-record process.
5. At your domain’s DNS provider, replace conflicting apex website records with the following A records. Keep unrelated email/MX/TXT records.

| Type | Host | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | YOUR-GITHUB-USERNAME.github.io |

Replace YOUR-GITHUB-USERNAME. The www CNAME points to your GitHub username hostname, without the repository name or https://. DNS can take up to 24 hours. Enable Enforce HTTPS when available. This download does not change your DNS or deploy the website.

Official setup instructions:
https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages

## Add a book, podcast, or essay post

1. Copy templates/post.html.txt to notes/your-post-title.html.
2. Replace its title, description, category/date, heading, and paragraphs. Category can be Books, Podcasts, or Essays. The template already has the correct ../ paths for the notes folder.
3. In notes.html, remove the empty-state block inside .post-list and insert:

```html
<a class="post-link" href="notes/your-post-title.html">
  <span class="eyebrow">Books · October 6, 2026</span>
  <h3>Your post title</h3>
  <p>A short description of your reflection.</p>
</a>
```

4. Repeat the link for each post, newest first. Commit/upload changes to GitHub to publish. There is no browser-based editor or login; you own and edit the files.

Use <p> for paragraphs, <h2> for sections, <em> for book titles, and <a href="https://..."> for source links. Escape & as &amp; and < as &lt; in prose. For spoilers, clearly label the post or use <details><summary>Spoilers</summary><p>...</p></details>. Only publish your own writing or material you have permission to share.

## Add a project

Copy templates/project.html.txt to projects/project-name.html. Fill in the problem, approach, results, and reflection. Add a link to it in projects.html using the .post-link pattern above. Remove the project empty-state when you publish your first project. Save figures in assets; in a project page, use <img src="../assets/figure.png" alt="A meaningful description" style="max-width:100%;height:auto">. Publish coursework only when course rules permit.

## Add your full résumé and experience

Replace the résumé overview with your verified experience. To add a PDF, put it at assets/Isaiah-Seymore-Resume.pdf and replace the “full résumé” message in resume.html with:

```html
<a class="text-link" href="assets/Isaiah-Seymore-Resume.pdf">Download résumé (PDF)</a>
```

Add roles to about.html as needed. Add a public email/social link only when you choose to share it; none is assumed here.

## Customize

- Copy/text: edit the relevant HTML page.
- Colors: change variables at the top of assets/style.css.
- Menu: edit the navigation in each HTML page and both templates.
- Footer: edit each HTML page and both templates; JS updates the year.
- Domain: update CNAME if you change it.

Everything uses system fonts and local files. No analytics, external fonts, tracking scripts, or cookies. The résumé page supports browser printing. Main content does not depend on JavaScript.

## Engineering Time Machine

The series is featured on the homepage and has a dedicated landing page, engineering-time-machine.html. Episode pages live in episodes/. These files provide a publishing home for the series; there are no existing media files or published episodes in this package.

1. Copy templates/episode.html.txt to episodes/your-episode.html.
2. Fill in the title, description, date, story, explanation, transcript, sources, and research notes. Templates support historical storytelling with room for technical detail.
3. Add an audio or video player only after the file exists. For small audio files, place your recording in assets and use:

```html
<audio controls preload="metadata" aria-label="Listen to this episode">
  <source src="../assets/your-episode.mp3" type="audio/mpeg">
  Your browser does not support audio playback.
</audio>
<p><a href="../assets/your-episode.mp3">Download episode audio</a></p>
```

For a video you host, use <video controls preload="metadata"><source src="YOUR-VERIFIED-VIDEO-URL" type="video/mp4"><track kind="captions" src="../assets/your-episode.vtt" srclang="en" label="English" default></video>. Provide captions and a transcript. You can also use your video provider’s official embed code instead, keeping the episode page, sources, and transcript on your website. Do not put placeholders for missing media in public players. Large recordings should be served by a suitable media host rather than uploaded to your code repository.

4. In engineering-time-machine.html, replace the episode empty-state with a link:

```html
<a class="post-link" href="episodes/your-episode.html">
  <span class="eyebrow">Episode 01 · Publication date</span>
  <h3>Your episode title</h3>
  <p>A short description of the story.</p>
</a>
```

For research transparency, link primary sources where available, identify your interpretation, cite figures, and document corrections on the episode page. Choose topics and published media yourself; none is invented here. The website does not yet include a podcast RSS feed or podcast-directory distribution.
