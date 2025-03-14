# Implementation Guide for Website Update

This guide outlines the steps to update your existing GitHub Pages website with the new minimal theme.

## Step 1: Create a New Branch

```bash
git checkout -b theme-update
```

## Step 2: Replace/Update Core Files

Replace or create the following files with the provided versions:

1. `_config.yml`: Site configuration
2. `assets/css/style.scss`: CSS styles
3. `_layouts/default.html`: Main layout template
4. `_layouts/course.html`: Course layout template
5. `_includes/image.html`: Image component
6. `_includes/gallery.html`: Gallery component

## Step 3: Create Required Directories

Make sure these directories exist:

```bash
mkdir -p _courses _data _includes _layouts teaching/es2 teaching/hri teaching/design-lab
```

## Step 4: Add Content Files

Add these content files:

1. `index.md`: Homepage
2. `about.md`: About page
3. `publications.md`: Publications list
4. `teaching/index.md`: Teaching overview
5. `activities.md`: Activities page

## Step 5: Add Data Files

Add these data files:

1. `_data/publications.yml`: Publication entries
2. `_data/years.yml`: Publication years
3. `_data/glass_gallery.yml`: Glass gallery images

## Step 6: Add Course Collections

Add these course files:

1. `_courses/es2-computing.md`: ES2 course
2. `_courses/human-robot-interaction.md`: HRI course
3. `_courses/engineering-design-lab.md`: Design lab course

## Step 7: Test Locally

Run the site locally to test:

```bash
bundle exec jekyll serve
```

Visit http://localhost:4000 to preview the site.

## Step 8: Commit and Push

```bash
git add .
git commit -m "Update site with new minimal theme"
git push origin theme-update
```

## Step 9: Create Pull Request

On GitHub, create a pull request from your `theme-update` branch to `main` branch.

## Step 10: Merge Changes

After reviewing the changes, merge the pull request to deploy the new theme.

## Next Steps

After implementing the theme:

1. Add additional course pages as needed
2. Update course materials and resources
3. Add more project photos and documentation
4. Expand the timeline data for courses with more detail
5. Connect any missing image resources

## Troubleshooting

- If images aren't displaying, check path references and file permissions
- If Jekyll build fails, check for YAML syntax errors in frontmatter
- If styles aren't applying correctly, ensure CSS paths are correct
- If collections aren't showing, verify _config.yml collections settings