# Melmua Blog Management

This directory contains the blog posts and related assets for the Melmua website. Follow these instructions to add a new blog post.

## Directory Structure

```
website/pages/mlogs/
├── mlogs.json         # Main blog configuration file
├── blogs/             # Blog content directory
│   ├── 1/            # Blog post directories (numbered)
│   │   ├── images/   # Blog-specific images
│   │   │   └── 1_thumbnail.png
│   │   └── 1_blog.md # Blog content file
│   └── ...
└── authors/          # Author profile pictures
    └── author-name.png
```

## How to Add a New Blog Post

### 1. Create Blog ID

- Find the highest existing blog ID in `mlogs.json`
- Use the next number as your new blog ID
- Example: If the last blog is `12`, use `13` for the new blog

### 2. Create Directory Structure

```bash
cd website/pages/mlogs/blogs
mkdir -p <blog-id>/images
```

Example for blog ID 13:
```bash
mkdir -p 13/images
```

### 3. Add Blog Content

1. Create the markdown file:
   - Name format: `<blog-id>_blog.md`
   - Location: `blogs/<blog-id>/`
   - Example: `blogs/13/13_blog.md`

2. Blog content structure:
   - Content can be any valid Markdown format
   - You can include headers, lists, tables, code blocks, etc.
   - Example structure:
```markdown
# Your Blog Title

Your content here in any valid Markdown format...

## Some Section

- List items
- Tables
- Code blocks
- Quotes
- etc.

### Images in Blog

![Image Description](https://raw.githubusercontent.com/melmua/static-assets/main/website/pages/mlogs/blogs/<blog-id>/images/your-image.png)

```

### 4. Add Images

1. Add thumbnail image:
   - Name format: `<blog-id>_thumbnail.png`
   - Location: `blogs/<blog-id>/images/`
   - Example: `blogs/13/images/13_thumbnail.png`
   - URL format in JSON: `https://raw.githubusercontent.com/melmua/static-assets/main/website/pages/mlogs/blogs/<blog-id>/images/<blog-id>_thumbnail.png`

2. Blog content images:
   - Store all blog-related images in the `blogs/<blog-id>/images/` directory
   - Use meaningful names for images (e.g., `product-comparison.png`, `tutorial-step1.png`)
   - Always use GitHub raw URLs in markdown:
     ```
     https://raw.githubusercontent.com/melmua/static-assets/main/website/pages/mlogs/blogs/<blog-id>/images/your-image.png
     ```

3. Author profile picture (if new author):
   - Name format: `author-name.png`
   - Location: `authors/`
   - URL format in JSON: `https://raw.githubusercontent.com/melmua/static-assets/main/website/pages/mlogs/authors/author-name.png`

### 5. Update mlogs.json

Add a new entry to the `blogItems` array in `mlogs.json`:

```json
{
  "id": "<blog-id>",
  "title": "Your Blog Title",
  "thumbnailUrl": "https://raw.githubusercontent.com/melmua/static-assets/main/website/pages/mlogs/blogs/<blog-id>/images/<blog-id>_thumbnail.png",
  "searchKeywords": [
    "keyword1",
    "keyword2",
    "keyword3",
    "keyword4"
  ],
  "author": "Author Name",
  "authorProfilePic": "https://raw.githubusercontent.com/melmua/static-assets/main/website/pages/mlogs/authors/author-name.png",
  "lastUpdatedAt": "YYYY-MM-DDThh:mm:ssZ",
  "blogContent": "https://raw.githubusercontent.com/melmua/static-assets/main/website/pages/mlogs/blogs/<blog-id>/<blog-id>_blog.md",
  "readingTime": <estimated-minutes>,
  "category": {
    "main": "<main-category>",
    "sub": "<sub-category>"
  },
  "excerpt": "A brief description of your blog post (150-200 characters)",
  "relatedPosts": ["<related-post-id-1>", "<related-post-id-2>"]
}
```

### 6. Validation Checklist

- [ ] Blog ID is incremental and unique
- [ ] Directory structure is correct
- [ ] Markdown file follows naming convention
- [ ] Thumbnail image is added
- [ ] Author profile picture exists
- [ ] JSON entry is properly formatted
- [ ] All URLs are correct
- [ ] Related posts exist and are valid
- [ ] Category matches existing categories

## Categories Management

### Main Categories (Fixed)
The following main categories are fixed and should NOT be modified:
- beauty-trends
- beauty-tutorials
- product-reviews

### Sub Categories (Flexible)
Current sub-categories:
- Seasonal Trends
- Skincare Routines
- Makeup Reviews
- Celebrity Looks
- Advanced Techniques
- Tools & Accessories
- Makeup Basics
- Social Media Trends
- Hair Styling
- Runway Beauty

You can:
- Add new sub-categories as needed
- Use existing sub-categories
- Create variations of existing sub-categories

When adding a new sub-category:
1. Use clear, descriptive names
2. Follow the existing capitalization format
3. Ensure it logically fits under one of the main categories
4. Update this README to include the new sub-category

Example of adding a new sub-category:
```json
"category": {
  "main": "beauty-tutorials",
  "sub": "Your New Sub-Category"
}
```
