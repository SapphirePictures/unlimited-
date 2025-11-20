# 🚀 Deployment Guide - Unlimited Grace & Mercy Worldwide Mission

This guide will help you deploy your church website with automatic updates using GitHub + Netlify/Vercel.

---

## 📋 Prerequisites

Before you start, make sure you have:
- [ ] A GitHub account (free) - [Sign up here](https://github.com/signup)
- [ ] Your Figma Make project ready
- [ ] A custom domain (optional, but recommended)

---

## 🎯 Deployment Steps

### **Step 1: Download Your Project from Figma Make**

1. In Figma Make, look for the **Export** or **Download** button
2. Download all project files as a ZIP
3. Extract the ZIP file to a folder on your computer
4. Name the folder something like `ugm-church-website`

---

### **Step 2: Set Up GitHub Repository**

#### **Option A: Using GitHub Desktop (Easier)**

1. **Download GitHub Desktop**: https://desktop.github.com/
2. **Install and sign in** with your GitHub account
3. Click **"File"** → **"Add Local Repository"**
4. Select your extracted project folder
5. Click **"Create Repository"**
6. Add a description: "Unlimited Grace & Mercy Church Website"
7. Click **"Publish Repository"**
8. Choose **Public** or **Private** (Private recommended)
9. Click **"Publish Repository"**

#### **Option B: Using Command Line**

```bash
# Navigate to your project folder
cd path/to/ugm-church-website

# Initialize git repository
git init

# Add all files
git add .

# Create first commit
git commit -m "Initial commit: UGM Church Website"

# Create repository on GitHub, then:
git remote add origin https://github.com/YOUR-USERNAME/ugm-church-website.git
git branch -M main
git push -u origin main
```

---

### **Step 3: Deploy to Netlify (Recommended)**

#### **Why Netlify?**
- ✅ Free tier is generous
- ✅ Automatic HTTPS
- ✅ Custom domain support
- ✅ Continuous deployment
- ✅ Form handling
- ✅ Serverless functions

#### **Deployment Steps:**

1. **Go to Netlify**: https://www.netlify.com/
2. **Sign up** with your GitHub account (easiest option)
3. Click **"Add new site"** → **"Import an existing project"**
4. Choose **"Deploy with GitHub"**
5. Authorize Netlify to access your GitHub
6. Select your repository: `ugm-church-website`
7. **Configure build settings**:
   ```
   Build command: npm run build
   Publish directory: dist
   ```
8. Click **"Deploy site"**

#### **🎉 Your site is now live!**
- Netlify will give you a URL like: `random-name-123.netlify.app`
- Every time you push to GitHub, Netlify automatically rebuilds and deploys

---

### **Step 4: Configure Environment Variables**

Your church website needs these environment variables for Supabase:

1. In Netlify, go to **Site settings** → **Environment variables**
2. Add these variables (get values from Supabase dashboard):

```
VITE_SUPABASE_URL=your-project-url.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key
VITE_SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
VITE_SUPABASE_DB_URL=your-db-url
```

#### **Where to find Supabase values:**
1. Go to your Supabase project: https://supabase.com/dashboard
2. Click **Project Settings** → **API**
3. Copy:
   - **Project URL** → `VITE_SUPABASE_URL`
   - **anon/public key** → `VITE_SUPABASE_ANON_KEY`
   - **service_role key** → `VITE_SUPABASE_SERVICE_ROLE_KEY` (⚠️ Keep this secret!)

3. **Trigger a new deploy** after adding environment variables

---

### **Step 5: Set Up Custom Domain (Optional)**

#### **If you have a domain (e.g., ugmworldwide.com):**

1. In Netlify, go to **Domain settings** → **Add custom domain**
2. Enter your domain: `ugmworldwide.com`
3. Netlify will provide DNS settings
4. Go to your domain registrar (Namecheap, GoDaddy, etc.)
5. Update DNS records as instructed by Netlify
6. Wait 24-48 hours for DNS propagation
7. Netlify automatically adds free HTTPS certificate

#### **Common DNS Settings:**
```
Type: A
Name: @
Value: 75.2.60.5 (Netlify's IP)

Type: CNAME
Name: www
Value: your-site-name.netlify.app
```

---

## 🔄 Making Updates (Your New Workflow)

### **Option 1: Using Figma Make → GitHub Desktop**

1. **Make changes in Figma Make** and test thoroughly
2. **Download updated project** from Figma Make
3. **Replace files** in your local project folder
4. **Open GitHub Desktop**
5. Review changes (green = added, red = removed)
6. Write a commit message: "Updated hero section" or "Fixed contact form"
7. Click **"Commit to main"**
8. Click **"Push origin"**
9. **Netlify automatically deploys** in 1-2 minutes! 🚀

### **Option 2: Direct Edit in GitHub**

1. Make small changes directly on GitHub
2. Edit files in the browser
3. Commit changes
4. Netlify auto-deploys

---

## ⚡ Alternative: Deploy to Vercel

Vercel is another excellent option (similar to Netlify):

1. Go to: https://vercel.com/
2. Sign up with GitHub
3. Click **"Import Project"**
4. Select your GitHub repository
5. Configure:
   ```
   Framework Preset: Vite
   Build Command: npm run build
   Output Directory: dist
   ```
6. Add environment variables (same as Netlify)
7. Click **"Deploy"**

---

## 🛠️ Build Configuration Files

Your project should include these files for proper deployment:

### **package.json** (already configured)
```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  }
}
```

### **netlify.toml** (create this in root directory)
```toml
[build]
  command = "npm run build"
  publish = "dist"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200

[functions]
  directory = "supabase/functions"
```

---

## 🔐 Security Checklist

Before going live:

- [ ] Change admin password from default `ugm-admin-2024`
- [ ] Keep `SUPABASE_SERVICE_ROLE_KEY` secret (never commit to GitHub)
- [ ] Set repository to **Private** on GitHub
- [ ] Enable HTTPS on custom domain
- [ ] Test all forms and database connections
- [ ] Test admin dashboard at `/you-are-unlimited`

---

## 📊 Monitoring Your Site

### **Netlify Dashboard:**
- View deployment history
- See build logs if something fails
- Monitor site analytics
- Configure custom domains

### **Supabase Dashboard:**
- Monitor database usage
- View volunteer applications
- Check API usage
- Manage storage

---

## 🆘 Troubleshooting

### **Build Failed:**
- Check build logs in Netlify/Vercel dashboard
- Verify all environment variables are set
- Ensure `package.json` has correct build command

### **Site loads but features don't work:**
- Check browser console for errors
- Verify environment variables in hosting platform
- Ensure Supabase project is active

### **Admin dashboard not accessible:**
- Navigate to: `your-domain.com/you-are-unlimited`
- Clear browser cache
- Check if JavaScript is enabled

---

## 📞 Need Help?

Common issues and solutions:

1. **"Module not found" errors**: Run `npm install` locally first
2. **Database not connecting**: Double-check environment variables
3. **Builds taking too long**: Check if you have large image files (optimize them)
4. **404 errors on page refresh**: Add redirects configuration (see netlify.toml above)

---

## 🎉 Next Steps After Deployment

1. **Test everything**:
   - Navigate through all pages
   - Submit a test volunteer application
   - Access admin dashboard
   - Test on mobile devices

2. **Share your site**:
   - Announce to congregation
   - Add to church social media
   - Print on bulletins/flyers

3. **Set up integrations** (optional):
   - Email notifications for volunteer signups
   - Google Sheets sync
   - Google Analytics

4. **Regular maintenance**:
   - Check volunteer applications weekly
   - Update sermon content
   - Post upcoming events
   - Backup database monthly

---

## ✅ Deployment Checklist

Use this checklist for your first deployment:

- [ ] Project downloaded from Figma Make
- [ ] GitHub account created
- [ ] Repository created and code pushed
- [ ] Netlify/Vercel account created
- [ ] Site deployed successfully
- [ ] Environment variables configured
- [ ] Supabase connection working
- [ ] Custom domain connected (optional)
- [ ] HTTPS enabled
- [ ] Admin password changed
- [ ] All pages tested
- [ ] Mobile responsiveness verified
- [ ] Forms working correctly
- [ ] Admin dashboard accessible

---

## 🌟 Congratulations!

Your church website is now live with automatic deployment! Every time you make changes and push to GitHub, your site automatically updates. 

**Your admin dashboard**: `https://your-domain.com/you-are-unlimited`

**Bookmark it and keep it secure!** 🔐⛪✨
