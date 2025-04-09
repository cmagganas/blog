# Development Guide

## Common Gotchas and Solutions

### 1. MkDocs Material Configuration
- **Issue**: Social cards and imaging features require Cairo library
- **Solution**: Either install Cairo dependencies or disable social cards in `mkdocs.yml`:
  ```yaml
  theme:
    social:
      cards: false
  ```

### 2. Blog Plugin Configuration
- **Issue**: Author references not working
- **Solution**: 
  - Create `.authors.yml` in the correct location (`docs/blog/.authors.yml`)
  - Use correct author ID format:
    ```yaml
    me:  # Author ID
      name: Your Name
      description: Your Description
      avatar: https://github.com/username.png
      url: https://github.com/username
    ```
  - Reference author ID in blog posts:
    ```yaml
    authors:
      - me  # Must match the ID in .authors.yml
    ```

### 3. Navigation Structure
- **Issue**: Files not included in navigation
- **Solution**: Add all relevant files to the `nav` section in `mkdocs.yml`:
  ```yaml
  nav:
    - Home: 'index.md'
    - Blog:
      - "blog/posts/your-post.md"
  ```

### 4. Asset Management
- **Issue**: Missing images or assets
- **Solution**: 
  - Place assets in the `docs` directory
  - Use relative paths in markdown: `![alt text](./path/to/image.png)`
  - Ensure all referenced assets exist

### 5. GitHub Pages Deployment
- **Issue**: Deployment failures
- **Solution**:
  - Ensure `gh-pages` branch exists
  - Run `mkdocs gh-deploy` from the correct directory
  - Check GitHub repository settings for Pages configuration

### 6. YAML Frontmatter
- **Issue**: Invalid frontmatter format
- **Solution**: Use correct YAML format for blog posts:
  ```yaml
  ---
  title: Your Title
  description: Your Description
  date: YYYY-MM-DD
  authors:
    - your_author_id
  categories:
    - Category1
    - Category2
  ---
  ```

## Best Practices
1. Always test locally with `mkdocs serve` before deploying
2. Keep the `docs` directory structure clean and organized
3. Use consistent naming conventions for files and directories
4. Document any custom configurations or plugins
5. Regularly update dependencies in `requirements.txt` 