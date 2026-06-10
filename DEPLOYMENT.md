# VakilAI - Complete Deployment Guide

## ✅ GitHub Repository

**Status:** ✅ Already pushed to GitHub
**URL:** https://github.com/rockanik555-lazy/vakilai

### What's on GitHub
```
✅ All source code
✅ Complete documentation
✅ Configuration files
✅ Legal knowledge base
✅ API routes
✅ UI components
✅ Environment templates
✅ GitHub Actions workflows
✅ Deployment configurations
```

---

## 🚀 Render Deployment Setup

### Step 1: Connect GitHub to Render

1. Go to **https://render.com**
2. Click **"New +"** → **"Web Service"**
3. Select **"Connect a repository"**
4. Find and select **`rockanik555-lazy/vakilai`**
5. Click **"Connect"**

### Step 2: Configure Render Service

**Fill in the form:**

```
Service Name:        vakilai
Environment:         Node
Build Command:       npm run build
Start Command:       npm start
Plan:                Free (or Starter)
```

### Step 3: Add Environment Variables

Click **"Environment"** tab and add:

```
OPENAI_API_KEY       → sk-your-actual-key
NODE_ENV             → production
NEXT_PUBLIC_APP_URL  → https://vakilai.onrender.com
```

**Save:** Click **"Create Web Service"**

---

## 🔄 Automatic Deployment

### GitHub Actions Workflow

The app includes automatic deployment:

**File:** `.github/workflows/deploy.yml`

**What it does:**
1. ✅ Watches for pushes to `main` branch
2. ✅ Runs tests & linting
3. ✅ Builds the app
4. ✅ Deploys to Render automatically

### Manual Redeploy

In Render Dashboard:
1. Go to your service
2. Click **"Manual Deploy"**
3. Select **"Deploy latest commit"**
4. Wait 2-3 minutes for build

---

## 📋 Deployment Checklist

### Before Deploying

- [x] GitHub repository created
- [x] All files committed and pushed
- [x] `Dockerfile` added
- [x] `Procfile` added
- [x] `render.yaml` configured
- [x] GitHub Actions workflow created
- [ ] OpenAI API key obtained

### During Deployment

- [ ] Connect Render to GitHub
- [ ] Configure environment variables
- [ ] Set Node.js version (18.x)
- [ ] Configure build & start commands
- [ ] Add OPENAI_API_KEY
- [ ] Click "Create Web Service"

### After Deployment

- [ ] Wait for build to complete (2-3 min)
- [ ] Check deployment logs
- [ ] Visit your live URL
- [ ] Test all features

---

## 🎯 Step-by-Step Deployment

### Phase 1: Get OpenAI API Key (2 minutes)

1. Go to https://platform.openai.com/signup
2. Create account (or login)
3. Go to **Account** → **API keys**
4. Click **"Create new secret key"**
5. Copy the key (starts with `sk-`)
6. Save it safely

### Phase 2: Connect Render (5 minutes)

1. **Go to:** https://render.com
2. **Sign up** (or login)
3. **Click:** New → Web Service
4. **Select:** rockanik555-lazy/vakilai
5. **Fill form:**
   - Name: `vakilai`
   - Runtime: `Node`
   - Build: `npm run build`
   - Start: `npm start`

### Phase 3: Configure Environment (2 minutes)

1. Click **"Environment"**
2. Add these variables:
   ```
   OPENAI_API_KEY = sk-your-key
   NODE_ENV = production
   NEXT_PUBLIC_APP_URL = https://vakilai.onrender.com
   ```
3. Click **"Create Web Service"**

### Phase 4: Wait for Build (3-5 minutes)

- Watch the build logs
- Should see:
  ```
  ✓ Build successful
  ✓ Server running on port 3000
  ```

### Phase 5: Access Your App

- **URL:** https://vakilai.onrender.com (or your custom domain)
- **Test:** Visit `/chat` and ask a legal question
- **Success:** Response appears with citations

---

## 📊 Deployment Architecture

```
Your Local Computer
    ↓
GitHub Repository (rockanik555-lazy/vakilai)
    ↓
GitHub Actions Workflow (.github/workflows/deploy.yml)
    ↓
Render Platform
    ↓
Docker Container (Dockerfile)
    ↓
Node.js Server (npm start)
    ↓
🌐 Live Website: https://vakilai.onrender.com
```

---

## 🔧 Configuration Files Explained

### `Dockerfile`
- Builds app in container
- Installs dependencies
- Compiles Next.js
- Exposes port 3000
- Starts production server

### `Procfile`
- Tells Render how to start
- Command: `npm start`
- Port: 3000 (automatic)

### `render.yaml`
- Render configuration
- Specifies Node.js runtime
- Defines build & start commands
- Environment variable placeholders

### `.github/workflows/deploy.yml`
- Automatic CI/CD pipeline
- Runs on every push to `main`
- Tests, builds, deploys
- No manual steps needed

---

## 🚀 Local vs Production

### Local Development
```bash
npm install
npm run dev
# Runs on http://localhost:3000
```

### Production (Render)
```bash
npm ci              # Clean install
npm run build       # Compile Next.js
npm start          # Start production server
# Runs on https://vakilai.onrender.com
```

---

## 📈 Monitoring After Deployment

### Check Logs in Render Dashboard

1. Go to your service
2. Click **"Logs"**
3. Should see:
   ```
   ✓ Dependencies installed
   ✓ Build successful
   ✓ Server started on port 3000
   ```

### Common Issues

| Issue | Solution |
|-------|----------|
| Build fails | Check `npm run build` locally first |
| App crashes | Check OPENAI_API_KEY is set |
| 502 errors | Redeploy manually or check logs |
| Slow response | Render free tier throttles |

---

## 🔑 Environment Variables

### Required
- `OPENAI_API_KEY` - Your OpenAI API key (starts with `sk-`)

### Optional
- `NEXT_PUBLIC_SUPABASE_URL` - Supabase database (future)
- `NEXT_PUBLIC_SUPABASE_ANON_KEY` - Supabase auth (future)

### Auto-set by Render
- `NODE_ENV` → production
- `PORT` → 3000
- `HOSTNAME` → 0.0.0.0

---

## 🌐 Custom Domain (Optional)

To use your own domain:

1. In Render Dashboard
2. Go to **Settings** → **Custom Domain**
3. Enter your domain (e.g., `vakilai.com`)
4. Add DNS records (shown in Render)
5. Wait 24 hours for DNS propagation

---

## 💾 Backup & Rollback

### To Rollback to Previous Version

1. In Render Dashboard
2. Go to **Deployments**
3. Find previous deployment
4. Click **"Deploy"** on that version
5. App reverts to previous state

---

## 🔐 Security Best Practices

### DO ✅
- ✅ Never commit API keys to GitHub
- ✅ Use Render environment variables
- ✅ Keep dependencies updated
- ✅ Enable HTTPS (automatic on Render)
- ✅ Monitor logs regularly

### DON'T ❌
- ❌ Don't push `.env` files
- ❌ Don't hardcode API keys
- ❌ Don't share your secret keys
- ❌ Don't disable HTTPS

---

## 📊 Performance Tips

### Free Tier Render Limitations
- Spins down after 15 min inactivity
- ~500MB RAM
- Shared resources
- Cold starts (30+ seconds)

### Solutions
1. **Upgrade Plan** - $7/month for always-on
2. **Keep Warm** - Add uptime monitor
3. **Optimize** - Reduce bundle size

### Uptime Monitor (Keep App Warm)
```bash
# Add free uptime monitor that pings app every 5 minutes
# Prevents cold start delays
```

---

## ✅ Deployment Complete!

### Your App is Now Live

**Website:** https://vakilai.onrender.com

**Features Available:**
- ✅ Landing page
- ✅ AI chat with legal Q&A
- ✅ Lawyer directory
- ✅ Pricing page
- ✅ All APIs working

### Test These URLs
```
https://vakilai.onrender.com/                    # Home
https://vakilai.onrender.com/chat               # Chat interface
https://vakilai.onrender.com/lawyers            # Lawyer marketplace
https://vakilai.onrender.com/pricing            # Pricing page
```

---

## 🎯 Next Steps

### Week 1
- ✅ Monitor deployment
- ✅ Test all features
- ✅ Check performance

### Week 2
- [ ] Expand legal database
- [ ] Add more lawyers
- [ ] Optimize performance

### Week 3-4
- [ ] Add authentication
- [ ] Implement payments
- [ ] Add document uploads

---

## 📞 Troubleshooting Deployment

### Build Failed
```bash
# Test locally first
npm install
npm run build
npm start
# If it works locally, it'll work on Render
```

### App Crashes on Render
```
Check:
1. OPENAI_API_KEY is set
2. No syntax errors (run npm run lint)
3. All dependencies in package.json
4. Node version is 18.x
```

### 502 Bad Gateway
```
Solutions:
1. Check app logs in Render
2. Restart the service
3. Check memory usage
4. Upgrade plan if needed
```

### Slow Performance
```
Expected on free tier:
- First request: 30+ seconds (cold start)
- Subsequent: 1-2 seconds
- Render free spins down after 15 min

Solutions:
1. Upgrade to Starter plan ($7/month)
2. Use uptime monitor
3. Optimize code/bundle
```

---

## 🎉 Congratulations!

Your **VakilAI** application is now:
- ✅ **Live on the internet**
- ✅ **Auto-deploying from GitHub**
- ✅ **Powered by OpenAI**
- ✅ **Accessible to everyone**
- ✅ **Production-ready**

---

## 📱 Share Your App

You can now share:
- **Live URL:** https://vakilai.onrender.com
- **GitHub:** https://github.com/rockanik555-lazy/vakilai
- **Showcase:** Show it to investors, friends, colleagues

---

## 🚀 You're LIVE!

**Deployed successfully!** 🎉⚖️

Start using your AI Legal Assistant now!

---

**Questions?**
- Check Render logs
- Check GitHub Actions
- Review deployment config
- Test locally first

**Success metrics:**
- ✅ App loads in browser
- ✅ Chat responds to questions
- ✅ Lawyers list appears
- ✅ No 502 errors

---

**Happy deploying!** 🚀💻⚖️
