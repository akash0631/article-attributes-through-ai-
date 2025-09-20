# Quick Start Checklist ✅

## Before You Start
- [ ] Download and extract the `article-intake-vercel.tar.gz` file
- [ ] Have your OpenAI API key ready (starts with `sk-`)

## Step-by-Step Deployment

### 1. Create Accounts (5 minutes)
- [ ] Sign up for GitHub at [github.com](https://github.com)
- [ ] Sign up for Vercel at [vercel.com](https://vercel.com) using your GitHub account

### 2. Upload to GitHub (3 minutes)
- [ ] Create new repository called `article-intake`
- [ ] Upload ALL files from the extracted folder
- [ ] Commit the files

### 3. Deploy on Vercel (2 minutes)
- [ ] Import your GitHub repository
- [ ] Add environment variable: `OPENAI_API_KEY` = your API key
- [ ] Click Deploy

### 4. Test Your App
- [ ] Visit your live app URL
- [ ] Upload a test image
- [ ] Click Extract
- [ ] Verify it works

## Your App URLs
- **GitHub Repository**: `https://github.com/YOUR_USERNAME/article-intake`
- **Live App**: `https://article-intake-XXXXX.vercel.app` (Vercel will give you this)

## Important Files Included
- ✅ `vercel.json` - Vercel configuration
- ✅ `api/extract.js` - OpenAI Vision API endpoint
- ✅ `api/map.js` - Field mapping endpoint
- ✅ `dist/` folder - Built application files
- ✅ All React components and styling

## If Something Goes Wrong
1. Check Vercel deployment logs
2. Verify your OpenAI API key is correct
3. Make sure all files were uploaded to GitHub
4. Try deploying again

## Need Help?
- Read the full `EASY_DEPLOY.md` guide
- Check Vercel's documentation
- Verify your OpenAI account has credits

**Total Time: About 10 minutes from start to finish!** 🚀
