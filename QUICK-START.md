# ⚡ Quick Start Deployment Guide

**Get your church website live in 10 minutes!**

---

## 🎯 Fastest Path to Deployment

### **Step 1: Download (1 minute)**
1. Download this project from Figma Make
2. Extract the ZIP file to a folder

### **Step 2: GitHub (2 minutes)**
1. Go to https://github.com/new
2. Sign in or create account
3. Repository name: `ugm-church-website`
4. Click "Create repository"
5. Follow the commands shown (or use GitHub Desktop)

### **Step 3: Netlify (5 minutes)**
1. Go to https://www.netlify.com/
2. Click "Sign up" → Choose "GitHub"
3. Click "Add new site" → "Import an existing project"
4. Choose GitHub → Select your repository
5. Build settings:
   - Build command: `npm run build`
   - Publish directory: `dist`
6. Click "Deploy site"

### **Step 4: Environment Variables (2 minutes)**
1. In Netlify: Site settings → Environment variables
2. Add these (get from Supabase dashboard):
   ```
   VITE_SUPABASE_URL = your-url
   VITE_SUPABASE_ANON_KEY = your-key
   VITE_SUPABASE_SERVICE_ROLE_KEY = your-key
   ```
3. Trigger redeploy

---

## 🎉 Done!

Your site is live at: `your-site-name.netlify.app`

**Admin access**: `your-site-name.netlify.app/you-are-unlimited`

---

## 🔄 How to Update Later

1. Make changes in Figma Make
2. Download updated project
3. Replace files in your GitHub repository
4. Push to GitHub
5. Netlify auto-deploys! ✨

---

## 📖 Need More Details?

See the full `DEPLOYMENT-GUIDE.md` for:
- Custom domain setup
- Troubleshooting
- Security best practices
- Advanced configuration

---

## 🆘 Quick Help

**Build failed?**
- Check environment variables are set
- View build logs in Netlify dashboard

**Site not working?**
- Open browser console (F12)
- Check for error messages
- Verify Supabase is connected

**Can't access admin?**
- Go to: `/you-are-unlimited`
- Password: `ugm-admin-2024` (change this!)

---

✅ **You're all set! Your church is now online!** 🙏⛪✨
