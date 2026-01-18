# Deploying Your Portfolio to Netlify with Chatbot

## ✅ Your chatbot is already configured correctly!

The chatbot uses `import.meta.env.VITE_GEMINI_API_KEY` which works perfectly with Netlify.

## 🚀 Deployment Steps

### 1. Push to GitHub (if not already done)

```bash
# Initialize git (if not done)
git init

# Add all files
git add .

# Commit
git commit -m "Portfolio with Jarvis chatbot"

# Add your GitHub repository
git remote add origin YOUR_GITHUB_REPO_URL

# Push to GitHub
git push -u origin main
```

### 2. Deploy to Netlify

#### Option A: Netlify UI (Recommended)

1. Go to [netlify.com](https://www.netlify.com/) and sign up/login
2. Click **"Add new site"** → **"Import an existing project"**
3. Connect your **GitHub account**
4. Select your portfolio repository
5. Configure build settings:
   - **Build command:** `npm run build`
   - **Publish directory:** `dist`
6. Click **"Show advanced"** → **"New variable"**
7. Add your environment variable:
   - **Key:** `VITE_GEMINI_API_KEY`
   - **Value:** `AIzaSyDjJ-Zh9opH14yr6TScLRklMp51XjQ1Mtk`
8. Click **"Deploy site"**

#### Option B: Netlify CLI

```bash
# Install Netlify CLI
npm install -g netlify-cli

# Login to Netlify
netlify login

# Initialize & deploy
netlify init

# Set environment variable
netlify env:set VITE_GEMINI_API_KEY AIzaSyDjJ-Zh9opH14yr6TScLRklMp51XjQ1Mtk

# Deploy
netlify deploy --prod
```

### 3. Verify Chatbot Works

1. Once deployed, open your Netlify site
2. Click the chatbot button (floating button on bottom-right)
3. Type a message to Jarvis
4. Confirm you get AI responses

## 🔒 Security Notes

- ✅ Your `.env` file is now in `.gitignore` (won't be committed)
- ✅ API key is stored securely in Netlify's environment variables
- ⚠️ Client-side API calls expose your key in browser requests
  - For production apps with high traffic, consider creating a serverless function
  - For a portfolio site, this is typically fine

## 🐛 Troubleshooting

### Chatbot not responding after deployment?

1. Check Netlify dashboard → **Site settings** → **Environment variables**
2. Ensure `VITE_GEMINI_API_KEY` is set correctly
3. Redeploy the site (Netlify → **Deploys** → **Trigger deploy**)

### "My systems are experiencing high traffic" error?

- This means the API call failed
- Check if your Gemini API key is valid
- Verify the API key has proper permissions in Google AI Studio

### Build fails on Netlify?

- Ensure `package.json` has all dependencies listed
- Check that `vite` is in `devDependencies`
- Review build logs in Netlify dashboard

## 📝 Future Improvements (Optional)

For better security with high traffic:

1. Create a Netlify serverless function
2. Move API key to server-side
3. Have chatbot call your function instead of Gemini directly

Would you like help setting that up?
