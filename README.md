# Platecraft — Meal Planner

AI-powered weekly meal planning. High protein, veggie-forward, moderate carbs.

## Project Structure

```
platecraft/
├── index.html                  # The app
├── netlify.toml                # Netlify config
├── netlify/
│   └── functions/
│       └── claude-proxy.js     # Serverless proxy (keeps API key secret)
└── README.md
```

---

## Deploy to Netlify (step-by-step)

### 1. Create a free Netlify account
Go to [netlify.com](https://netlify.com) and sign up with your GitHub account.

### 2. Push this project to GitHub
```bash
cd platecraft
git init
git add .
git commit -m "Initial commit"
gh repo create platecraft --public --push --source=.
```
(Requires GitHub CLI. Or create the repo manually at github.com and push.)

### 3. Connect to Netlify
- In the Netlify dashboard, click **"Add new site" → "Import an existing project"**
- Choose **GitHub** and select your `platecraft` repo
- Build settings will auto-detect from `netlify.toml` — leave them as-is
- Click **Deploy site**

### 4. Add your Anthropic API key (the important part)
- In Netlify dashboard → your site → **Site configuration → Environment variables**
- Click **"Add a variable"**
- Key: `ANTHROPIC_API_KEY`
- Value: your Anthropic API key (get it at [console.anthropic.com](https://console.anthropic.com))
- Click **Save**, then go to **Deploys → Trigger deploy → Deploy site**

### 5. Customize your URL (optional)
- Go to **Site configuration → Domain management**
- Click **"Change site name"**
- Set it to something like `platecraft` → your URL becomes `platecraft.netlify.app`

### 6. Share it
Send the URL to your wife, mom, and dad. Works on any phone or browser.
To add it to the iPhone home screen: open in Safari → Share → "Add to Home Screen"

---

## Security
Your API key is stored as a Netlify environment variable — it never touches the browser.
All AI requests go: Browser → Netlify Function → Anthropic API → back to browser.
