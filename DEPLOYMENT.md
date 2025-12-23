# Deployment Guide: Enabling GitHub Pages

This guide will help you enable GitHub Pages for your blog and complete the migration from Netlify.

## Step 1: Enable GitHub Pages

1. Go to your repository on GitHub: https://github.com/allaway/robert-blog
2. Click on **Settings** (top navigation)
3. In the left sidebar, click **Pages** (under "Code and automation")
4. Under "Build and deployment":
   - **Source**: Select "GitHub Actions"
   - This will use the workflow we've created (`.github/workflows/hugo.yml`)
5. Click **Save**

## Step 2: Trigger the First Deployment

Once you merge this PR to the `main` or `master` branch, the GitHub Actions workflow will automatically:
1. Build your Hugo site
2. Deploy it to GitHub Pages

Your site will be available at: **https://allaway.github.io/robert-blog/**

## Step 3: Monitor the Deployment

1. Go to the **Actions** tab in your repository
2. You should see a workflow run called "Deploy Hugo site to Pages"
3. Click on it to see the build and deployment progress
4. Once both "build" and "deploy" jobs complete successfully, your site is live!

## Step 4: Verify Your Site

1. Visit https://allaway.github.io/robert-blog/
2. Check that:
   - The homepage loads correctly
   - Blog posts are accessible:
     - https://allaway.github.io/robert-blog/2020/08/08/gaggia-steam-mod/
     - https://allaway.github.io/robert-blog/2020/12/18/2020-sophia-cider/
   - Navigation works (About, Categories, Tags, Search)
   - Images display properly

## Step 5: Update Netlify to Redirect Traffic

Your old Netlify site (https://allaway.netlify.app/) will automatically redirect to the new GitHub Pages URL thanks to the updated `netlify.toml` configuration. This ensures that:
- Old bookmarks continue to work
- Search engine links are preserved
- Social media shares redirect properly

The redirect is configured as a permanent redirect (301) which tells search engines to update their indexes.

## Step 6: (Optional) Set Up a Custom Domain

If you want to use a custom domain instead of `allaway.github.io`:

1. In GitHub Pages settings, add your custom domain
2. Configure your DNS provider to point to GitHub Pages:
   - Create a CNAME record pointing to `allaway.github.io`
   - Or create A records pointing to GitHub's IP addresses
3. Update the `baseURL` in `config.toml` to your custom domain
4. Update the redirect in `netlify.toml` to point to your custom domain

See GitHub's documentation: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

## Troubleshooting

### Build fails
- Check the Actions tab for error messages
- Ensure the Hugo version in the workflow matches your local setup
- Verify that the theme submodule is properly checked out

### Site doesn't load
- Wait a few minutes after the first deployment
- Clear your browser cache
- Check that GitHub Pages is enabled in repository settings

### Redirects don't work
- Verify that the Netlify site is still active
- Check the `netlify.toml` configuration is correct
- Contact Netlify support if needed

## What Changed?

### Added
- `.github/workflows/hugo.yml` - GitHub Actions workflow for automated deployment
- `DEPLOYMENT.md` - This deployment guide

### Modified
- `config.toml` - Updated `baseURL` to GitHub Pages URL
- `README.md` - Updated with new hosting information and development instructions
- `.gitignore` - Added Hugo build artifacts and improved organization
- `netlify.toml` - Configured to redirect all traffic to GitHub Pages
- `themes/harbor/layouts/_default/rss.xml` - Fixed Hugo compatibility issue (`.URL` → `.Permalink`)

### Removed
- `index.Rmd` - R/blogdown-specific file (no longer needed)
- `robert-blog.Rproj` - RStudio project file (no longer needed)

## Support

If you encounter any issues, please:
1. Check the Actions tab for build logs
2. Review this deployment guide
3. Consult GitHub Pages documentation: https://docs.github.com/en/pages
