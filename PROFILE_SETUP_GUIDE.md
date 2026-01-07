# 🎨 GitHub Profile README - Setup Guide

This guide explains how I created my dynamic GitHub profile README with all the bells and whistles! Feel free to learn from it and create your own awesome profile.

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Setup Instructions](#setup-instructions)
- [Components Breakdown](#components-breakdown)
- [Snake Animation Setup](#snake-animation-setup)
- [Customization Tips](#customization-tips)
- [Troubleshooting](#troubleshooting)

---

## 🌟 Overview

This is a fully dynamic GitHub profile README featuring:
- Real-time typing animation
- Categorized skills with bordered icons
- Live GitHub statistics
- Streak tracking
- Contribution graphs
- Animated snake eating contributions
- Social media badges
- Custom GIFs

## ✨ Features

### 1. **Profile Badges**
```markdown
![Profile Views](https://komarev.com/ghpvc/?username=YOUR_USERNAME&color=blueviolet&style=flat-square&label=Profile+Views)
[![GitHub followers](https://img.shields.io/github/followers/YOUR_USERNAME?style=social)](https://github.com/YOUR_USERNAME)
[![GitHub stars](https://img.shields.io/github/stars/YOUR_USERNAME?style=social)](https://github.com/YOUR_USERNAME)
```

### 2. **Typing Animation**
Uses `readme-typing-svg` service to create a dynamic typewriter effect:
```markdown
<img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=20&pause=1000&center=true&vCenter=true&width=700&lines=Hey+there!+I'm+Your+Name;I+build+amazing+things;Always+learning%2C+always+building" alt="Typing SVG" />
```

**Customization parameters:**
- `font` - Font family
- `size` - Text size
- `pause` - Delay between lines (ms)
- `center` - Center alignment
- `width` - Width of the text box
- `lines` - Your custom messages (separated by semicolons)

### 3. **Skills Section with HTML Tables**
Organized skills in categories with bordered cells:
```markdown
### 💻 Programming Languages
<table>
  <tr>
    <td align="center" width="90" style="border: 2px solid #444;">
      <img src="ICON_URL" width="50" height="50" alt="Tech Name" />
      <br>Tech Name
    </td>
    <!-- More cells -->
  </tr>
</table>
```

**Pro Tip:** Use cascading alignment (`<div align="right">`) to create a zigzag effect!

### 4. **GitHub Statistics**

#### Stats Cards:
```markdown
<img src="https://github-readme-stats-sigma-five.vercel.app/api?username=YOUR_USERNAME&show_icons=true&theme=radical&hide_border=true&count_private=true" alt="GitHub Stats" />
```

#### Top Languages:
```markdown
<img src="https://github-readme-stats-sigma-five.vercel.app/api/top-langs/?username=YOUR_USERNAME&layout=compact&theme=radical&hide_border=true&langs_count=10" alt="Top Languages" />
```

#### Streak Stats:
```markdown
<a href="https://git.io/streak-stats">
  <img src="https://streak-stats.demolab.com?user=YOUR_USERNAME" alt="GitHub Streak" />
</a>
```

### 5. **Contribution Graph**
```markdown
[![Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=YOUR_USERNAME&theme=github-compact&hide_border=true)](https://github.com/YOUR_USERNAME)
```

### 6. **Social Media Badges**
```markdown
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](YOUR_LINKEDIN_URL)
[![Twitter](https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](YOUR_TWITTER_URL)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:YOUR_EMAIL)
```

---

## 🐍 Snake Animation Setup

This is the coolest feature! A snake that eats your GitHub contributions.

### Step 1: Create GitHub Action Workflow

Create file: `.github/workflows/snake.yml`

```yaml
name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"  # Runs daily at midnight
  workflow_dispatch:      # Allows manual trigger
  push:
    branches:
      - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: Generate snake.svg
        uses: Platane/snk@v3
        with:
          github_user_name: YOUR_USERNAME
          outputs: |
            dist/snake.svg
            dist/snake-dark.svg?palette=github-dark

      - name: Push snake.svg to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

**Important:** Replace `YOUR_USERNAME` with your GitHub username!

### Step 2: Add Snake to README

```markdown
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/snake.svg">
</picture>
```

### Step 3: Run the Workflow

1. **Commit and push** your changes:
   ```bash
   git add .
   git commit -m "Add snake animation"
   git push origin main
   ```

2. **Manually trigger the workflow:**
   - Go to your GitHub repository
   - Click on **"Actions"** tab
   - Click on **"Generate Snake"** workflow (left sidebar)
   - Click **"Run workflow"** button (right side)
   - Select **"main"** branch
   - Click **"Run workflow"**

3. **Wait for completion:**
   - The workflow will take 1-2 minutes
   - Look for a green checkmark ✅
   - The snake will automatically update daily!

4. **View your snake:**
   - Refresh your profile page
   - The snake animation should now be visible!

### Step 4: Troubleshooting Snake Animation

**If snake doesn't appear:**

1. **Check workflow status:**
   - Go to Actions tab → Check if workflow completed successfully
   - If red X appears, click on it to see error logs

2. **Check output branch:**
   - Go to your repo → Branches
   - Look for "output" branch
   - Should contain `snake.svg` and `snake-dark.svg`

3. **Verify permissions:**
   - Go to repo Settings → Actions → General
   - Scroll to "Workflow permissions"
   - Select "Read and write permissions"
   - Save changes

4. **Check image URL:**
   - Make sure URL format is correct:
     ```
     https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/snake.svg
     ```

5. **Force refresh:**
   - Clear browser cache
   - Try incognito/private mode
   - Add `?v=1` to the end of image URL to bypass cache

---

## 🛠️ Setup Instructions

### 1. Create Profile Repository
- Create a repository with the **same name as your GitHub username**
- Example: If your username is `johndoe`, create repo `johndoe`
- Make it **public**
- Add a `README.md` file

### 2. Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/YOUR_USERNAME.git
cd YOUR_USERNAME
```

### 3. Copy the Template
- Copy the structure from my `README.md`
- Replace all instances of `barada02` with your username
- Update personal information, skills, and links

### 4. Add Custom Assets
- Add your own GIF files to the repository
- Update image paths in README

### 5. Setup Snake Animation
- Follow the [Snake Animation Setup](#snake-animation-setup) section above
- Create the workflow file
- Push and trigger the action

### 6. Commit and Push
```bash
git add .
git commit -m "Create awesome profile README"
git push origin main
```

---

## 🎨 Customization Tips

### Colors and Themes
- **Change theme:** Replace `theme=radical` with:
  - `dark`, `tokyonight`, `dracula`, `gruvbox`, `onedark`, `cobalt`
  - [More themes](https://github.com/anuraghazra/github-readme-stats/blob/master/themes/README.md)

### Icon Sources
- **DevIcon:** https://devicon.dev/
- **Simple Icons:** https://simpleicons.org/
- **Shields.io:** https://shields.io/

### Badge Styles
Replace `style=for-the-badge` with:
- `flat` - Flat design
- `flat-square` - Square edges
- `plastic` - Glossy look
- `social` - GitHub-style

### Layout Options

**Centered Layout:**
```markdown
<div align="center">
  <!-- Content -->
</div>
```

**Right-Aligned:**
```markdown
<div align="right">
  <!-- Content -->
</div>
```

**Table Layout:**
```markdown
<table>
  <tr>
    <td>Left Content</td>
    <td>Right Content</td>
  </tr>
</table>
```

---

## 📚 Resources

### Tools & Services
- [GitHub Readme Stats](https://github.com/anuraghazra/github-readme-stats)
- [Readme Typing SVG](https://github.com/DenverCoder1/readme-typing-svg)
- [GitHub Readme Streak Stats](https://github.com/DenverCoder1/github-readme-streak-stats)
- [GitHub Activity Graph](https://github.com/Ashutosh00710/github-readme-activity-graph)
- [Snake Animation](https://github.com/Platane/snk)
- [Shields.io Badges](https://shields.io/)
- [DevIcon](https://devicon.dev/)
- [Profile Views Counter](https://github.com/antonkomarev/github-profile-views-counter)

### Inspiration
- [Awesome GitHub Profile README](https://github.com/abhisheknaiidu/awesome-github-profile-readme)
- [GitHub Profile README Examples](https://github.com/coderjojo/creative-profile-readme)

---

## ⚠️ Troubleshooting

### Stats Not Showing
- **Solution:** Try alternative deployment: `github-readme-stats-sigma-five.vercel.app`
- **Reason:** Main vercel.app might be rate-limited

### Snake Not Generating
- Check Actions tab for errors
- Ensure repository is public
- Verify workflow permissions (Settings → Actions → General)
- Make sure `GITHUB_TOKEN` has write permissions

### Typing Animation Not Working
- Service might be down temporarily
- Try refreshing or wait a few minutes
- Check if URL is correctly formatted

### Images Not Loading
- Use absolute URLs, not relative paths
- For local images, commit them to the repo first
- Clear browser cache

---

## 🤝 Contributing

Feel free to:
- Fork this guide
- Add your own tips
- Share improvements
- Create issues for questions

---

## 📄 License

This guide is free to use and share. Give credit if you found it helpful!

---

## 💬 Questions?

If you have questions or need help:
1. Check the troubleshooting section
2. Review the GitHub Actions logs
3. Search for similar issues on GitHub
4. Reach out to the community

---

**Happy Coding!** 🚀

Made with ❤️ by [barada02](https://github.com/barada02)
