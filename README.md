# robert-blog

This is the source for my blog, now hosted on GitHub Pages: https://allaway.github.io/robert-blog/

Previously hosted at: https://allaway.netlify.app/ (redirects to new location)

## Technology Stack

- **Static Site Generator**: Hugo
- **Theme**: Harbor
- **Hosting**: GitHub Pages
- **CI/CD**: GitHub Actions

## Local Development

### Prerequisites
- Install [Hugo](https://gohugo.io/installation/) (extended version recommended)

### Running Locally
```bash
# Clone the repository with submodules (for the theme)
git clone --recurse-submodules https://github.com/allaway/robert-blog.git

# Navigate to the repository
cd robert-blog

# Start the Hugo development server
hugo server -D

# View the site at http://localhost:1313/robert-blog/
```

## Deployment

The site automatically deploys to GitHub Pages when changes are pushed to the `main` or `master` branch via GitHub Actions.

## Adding New Content

### New Blog Post
```bash
hugo new content/post/YYYY-MM-DD-post-title.en.md
```

### New Page
```bash
hugo new content/page/page-name.md
```

## Migration Notes

This blog was migrated from Netlify to GitHub Pages to remove R dependencies (blogdown) and simplify the hosting setup. The old Netlify site redirects all traffic to the new GitHub Pages URL to maintain link persistence.

For detailed migration information, see [MIGRATION.md](MIGRATION.md).

For deployment instructions, see [DEPLOYMENT.md](DEPLOYMENT.md).
