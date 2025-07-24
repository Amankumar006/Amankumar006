# GitHub Actions Profile Setup Guide

This guide explains how to set up and configure the GitHub Actions workflows for your enhanced profile README.

## 🚀 Quick Setup

### 1. Enable GitHub Actions
1. Go to your repository settings
2. Navigate to **Actions** → **General**
3. Under "Actions permissions", select **Allow all actions and reusable workflows**
4. Under "Workflow permissions", select **Read and write permissions**
5. Check **Allow GitHub Actions to create and approve pull requests**

### 2. Enable GitHub Pages
1. Go to **Settings** → **Pages**
2. Under "Source", select **Deploy from a branch**
3. Choose branch: **output** (this will be created automatically by the snake workflow)
4. Choose folder: **/ (root)**
5. Click **Save**

### 3. Repository Permissions
Ensure your repository has the following permissions enabled:
- **Contents**: Read and write (for updating README)
- **Actions**: Read (for running workflows)
- **Pages**: Write (for deploying snake animation)
- **Metadata**: Read (for accessing repository information)

## 📋 Workflow Details

### Snake Animation Workflow (`snake.yml`)
- **Frequency**: Every 12 hours + on push to main
- **Purpose**: Generates snake eating dots animation from your GitHub contributions
- **Output**: Creates SVG and GIF files in the `output` branch
- **Hosting**: Files are automatically deployed to GitHub Pages

### README Update Workflow (`update-readme.yml`)
- **Frequency**: Every 6 hours + on push to main
- **Purpose**: Updates README with latest GitHub activity and blog posts
- **Features**: 
  - Shows recent repository activity
  - Integrates blog posts from dev.to (if available)
  - Auto-commits changes

### Profile Stats Workflow (`profile-stats.yml`)
- **Frequency**: Daily at midnight UTC + on push to main
- **Purpose**: Updates profile statistics and coding metrics
- **Features**:
  - GitHub contribution stats
  - WakaTime integration (optional)
  - Language and project statistics

## 🔧 Optional Configuration

### WakaTime Integration
To enable WakaTime statistics in your profile:
1. Sign up at [WakaTime.com](https://wakatime.com)
2. Get your API key from WakaTime dashboard
3. Add it as a repository secret named `WAKATIME_API_KEY`
4. Install WakaTime extension in your code editor

### Blog Integration
The workflow is configured for dev.to blog integration:
- Default feed: `https://dev.to/feed/amankumar006`
- To change: Edit the `feed_list` in `update-readme.yml`
- Supports RSS/Atom feeds from any blogging platform

## 📝 Adding Content to README

### Snake Animation
Add this to your README.md where you want the snake animation:
```html
<div align="center">
  <img src="https://Amankumar006.github.io/Amankumar006/github-contribution-grid-snake.svg" alt="Snake animation" />
</div>
```

### GitHub Activity
Add this comment block to your README.md where you want recent activity:
```html
<!--START_SECTION:activity-->
<!--END_SECTION:activity-->
```

### Blog Posts
Add this comment block for blog post integration:
```html
<!-- BLOG:START -->
<!-- BLOG:END -->
```

### WakaTime Stats
Add this comment block for WakaTime statistics:
```html
<!--START_SECTION:waka-->
<!--END_SECTION:waka-->
```

### GitHub Stats Cards
Add these for various GitHub statistics:
```html
<!-- GitHub Stats -->
<img src="https://github-readme-stats.vercel.app/api?username=Amankumar006&show_icons=true&theme=radical" alt="GitHub Stats" />

<!-- Top Languages -->
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Amankumar006&layout=compact&theme=radical" alt="Top Languages" />

<!-- GitHub Streak -->
<img src="https://github-readme-streak-stats.herokuapp.com/?user=Amankumar006&theme=radical" alt="GitHub Streak" />
```

## 🔍 Troubleshooting

### Common Issues:

1. **Workflows not running**
   - Check if Actions are enabled in repository settings
   - Verify workflow files are in `.github/workflows/` directory
   - Ensure YAML syntax is correct

2. **Snake animation not showing**
   - Verify GitHub Pages is enabled and set to `output` branch
   - Check if the snake workflow completed successfully
   - Ensure the image URL in README is correct

3. **README not updating**
   - Verify repository has write permissions for Actions
   - Check if the comment blocks are present in README.md
   - Review workflow logs for errors

4. **Permission errors**
   - Go to Settings → Actions → General
   - Set "Workflow permissions" to "Read and write permissions"
   - Enable "Allow GitHub Actions to create and approve pull requests"

### Manual Trigger
You can manually run any workflow:
1. Go to **Actions** tab in your repository
2. Select the workflow you want to run
3. Click **Run workflow** button
4. Choose the branch (usually `main`) and click **Run workflow**

## 📊 Expected Results

After setup completion:
- ✅ Snake animation updates every 12 hours
- ✅ README shows latest GitHub activity (updated every 6 hours)  
- ✅ Profile statistics update daily
- ✅ GitHub Pages hosts the snake animation
- ✅ All workflows can be manually triggered
- ✅ Auto-commits maintain repository activity

## 🔒 Security Notes

- All workflows use `GITHUB_TOKEN` which is automatically provided
- No additional secrets required for basic functionality
- WakaTime integration requires optional `WAKATIME_API_KEY` secret
- Workflows follow GitHub Actions security best practices
- Limited permissions scope for enhanced security

---

For questions or issues, please create an issue in this repository or refer to the [GitHub Actions documentation](https://docs.github.com/en/actions).