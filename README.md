# Statistician Portfolio

A Jekyll-based portfolio website showcasing statistical analysis projects and blog posts.

## Setup

1. Install Jekyll: `gem install jekyll bundler`
2. Install dependencies: `bundle install`  
3. Run locally: `bundle exec jekyll serve`
4. Visit: `http://localhost:4000`

## Adding Content

### New Blog Post
Create `_posts/YYYY-MM-DD-title.md`:
```markdown
---
layout: post
title: "Your Title"
tags: [Statistics, R]
---
Content here...
```

### New Project
Create `_projects/project-name.md`:
```markdown
---
layout: project
title: "Project Name"
tech: [R, Python]
github: "https://github.com/user/repo"
---
Project description...
```

## Deployment

Push to GitHub and enable GitHub Pages in repository settings.