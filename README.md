# Hanlin (Harry) Shi — personal website

A single-page site with three tabs (Home, Research, CV). No build step, no
framework, no dependencies. Everything is plain HTML, CSS and JavaScript.

## Contents

    index.html            the whole site
    media/                images, videos and video poster frames
    CV_Hanlin_Shi.pdf     linked from the CV page
    shi2024robosoft.pdf   linked from the CV page (RoboSoft accepted manuscript)

`index.html` refers to `media/` by relative path, so keep the folder structure
as it is.

## Preview it locally first

Opening `index.html` straight from disk mostly works, but some browsers block
video from `file://` URLs. To see it properly, run this in the folder:

    python3 -m http.server 8000

then open http://localhost:8000

## Publish on GitHub Pages

1. Sign in to GitHub and create a new repository named exactly

       <your-username>.github.io

   Public. Do not add a README, .gitignore or licence — the repo should start empty.

2. Upload the files. Either drag them into the web interface
   (Add file > Upload files), or from the command line:

       cd <this folder>
       git init
       git add .
       git commit -m "Personal website"
       git branch -M main
       git remote add origin https://github.com/<your-username>/<your-username>.github.io.git
       git push -u origin main

   Note: `index.html` and the two PDFs go at the repository root, with `media/`
   as a folder beside them. Not inside another folder.

3. In the repository, go to Settings > Pages. Under "Build and deployment",
   set Source to "Deploy from a branch", branch `main`, folder `/ (root)`. Save.

4. Wait a few minutes, then visit

       https://<your-username>.github.io

   The Actions tab shows the deployment progress if it seems slow.

## Updating it later

Replace the file and push again — GitHub redeploys automatically:

    git add .
    git commit -m "Update research page"
    git push

Browsers cache aggressively. After an update, check with a hard refresh
(Ctrl+Shift+R, or Cmd+Shift+R on a Mac).

## Using your own domain

1. Buy the domain (Namecheap, Cloudflare and Porkbun are all fine, roughly $12/year).

2. In the repository root, create a file named `CNAME` containing only your
   domain, with no protocol and no trailing slash:

       hanlinshi.com

3. At your registrar's DNS settings, add these records:

   - Four `A` records for the apex domain (`@`), pointing at GitHub's Pages
     addresses. GitHub publishes the current list at
     https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site
     — use that page rather than copying addresses from elsewhere, as they change.
   - One `CNAME` record for `www`, pointing at `<your-username>.github.io`

4. Back in Settings > Pages, enter the domain under "Custom domain" and tick
   "Enforce HTTPS" once the certificate has been issued. DNS changes can take
   anywhere from a few minutes to a day to take effect.

## Notes on the media

Videos are H.264 MP4 with no audio track. They play when scrolled into view and
pause when they leave, so nothing downloads until a visitor reaches it.

Figures marked "Click to enlarge" open in a full-window overlay. The DSBC
controller diagram has a separate 4200px file for that; the others enlarge to
their own resolution.

## Before you send the link to anyone

- Add the IEEE copyright notice to `shi2024robosoft.pdf`. IEEE permits posting
  the accepted version on a personal site, and asks for a notice naming the
  publication and DOI. Check their current author-posting policy for the exact
  wording.
- Click through every link, including the DOI and both PDFs.
- Open the site on a phone.
