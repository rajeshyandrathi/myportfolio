# Deploy to GitHub Pages — Step by Step

You'll go from local files → live site at `https://<your-github-username>.github.io/` in about 5 minutes.

There are two flavors. Pick **Option A** if you want the site to be your main personal page (recommended). Pick **Option B** if you want it as a project page under an existing account.

---

## Option A — Personal site at `https://<username>.github.io/` (recommended)

This is the cleanest URL and the one most people use for portfolios.

### 1. Create a GitHub account (skip if you already have one)

Go to https://github.com/signup and sign up. Pick a username — you'll see it in the URL of your live site (e.g. `rajeshyandrathi.github.io`).

### 2. Create the repository

1. Click the **+** in the top-right of GitHub → **New repository**.
2. Repository name: `<your-username>.github.io` — **this exact name matters**. Example: if your username is `rajeshyandrathi`, name the repo `rajeshyandrathi.github.io`.
3. Visibility: **Public**.
4. **Do NOT** check "Add a README".
5. Click **Create repository**.

### 3. Upload the site (the no-terminal way)

On the empty repo page, click **uploading an existing file**.

Drag-and-drop these files from the `rajesh-portfolio` folder I built for you:
- `index.html`
- `README.md`
- `DEPLOY.md` (optional)

Scroll down → commit message: `initial site` → **Commit changes**.

That's it. In about 30–60 seconds, visit `https://<your-username>.github.io/` and your site is live.

> If the page doesn't load, open the repo → **Settings** → **Pages** in the left sidebar. Under "Build and deployment", make sure Source is **Deploy from a branch**, Branch is **main**, folder is **/ (root)**, and click **Save**. Wait a minute, then refresh.

### 3 (alternative) — The git command-line way

If you'd rather use the terminal:

```bash
# Inside the rajesh-portfolio folder
cd "/path/to/rajesh-portfolio"

# Initialize git
git init -b main

# Tell git who you are (only needed once globally)
git config --global user.name  "Rajesh Yandrathi"
git config --global user.email "rajeshyandrathi@gmail.com"

# Stage + commit
git add .
git commit -m "initial site"

# Connect to GitHub (replace USERNAME)
git remote add origin https://github.com/USERNAME/USERNAME.github.io.git

# Push it up
git push -u origin main
```

You'll be prompted to log in. On modern GitHub, the password is a **personal access token**, not your login password:
1. Go to https://github.com/settings/tokens → **Generate new token (classic)**.
2. Tick the **repo** scope. Generate. Copy the token.
3. Paste the token when git asks for a password.

Tip: install the GitHub CLI (`brew install gh` on macOS, `winget install --id GitHub.cli` on Windows), run `gh auth login`, and you'll never need to deal with tokens again.

---

## Option B — Project page at `https://<username>.github.io/portfolio/`

Use this if you already have a `<username>.github.io` repo for something else.

1. Create a new repo, e.g. `portfolio`. Public.
2. Upload the files (or push via git as above).
3. Repo → **Settings** → **Pages**. Source: **Deploy from a branch**. Branch: **main**, folder: **/ (root)**. **Save**.
4. After ~1 minute the site is live at `https://<username>.github.io/portfolio/`.

---

## Custom domain (optional)

Want `rajeshyandrathi.com` to point at the site?

1. Buy the domain (Namecheap, Cloudflare Registrar, Porkbun — any registrar works).
2. In your DNS settings, add four A records pointing the apex (`@`) to GitHub's IPs:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`.
3. Add a CNAME record for `www` → `<your-username>.github.io`.
4. In GitHub: **Settings** → **Pages** → **Custom domain** → enter `rajeshyandrathi.com` → **Save**. Tick **Enforce HTTPS** once it becomes available (a few minutes).

---

## Updating the site later

Edit `index.html` locally → commit → push.

```bash
git add .
git commit -m "update certifications"
git push
```

GitHub Pages rebuilds automatically. Hard-refresh your browser (Cmd-Shift-R / Ctrl-Shift-R) to see changes.

---

## Things to personalise after launch

- Add your **LinkedIn** and **Trailblazer** profile links into the contact section of `index.html`.
- Replace the placeholder cert tiles with your actual certification credential URLs.
- Drop a profile photo (`me.jpg`) into the folder and add an `<img>` to the hero if you'd like a face on the page.
- Update the `<meta name="description">` if you want a different SEO blurb.
