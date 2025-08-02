# youkoutaku.github.io

[![Waka time](https://wakatime.com/badge/user/09b9ec51-4790-4f52-a7f3-ae35dcbfc6dc/project/2cc51c41-66b5-4804-b2a4-73b94653d498.svg)](https://wakatime.com/badge/user/09b9ec51-4790-4f52-a7f3-ae35dcbfc6dc/project/2cc51c41-66b5-4804-b2a4-73b94653d498)

Personal blog and technical documentation site built with Jekyll and the Chirpy theme. This repository contains articles about AI, Control Theory, Programming, Mathematics, and various technical topics.

## 🚀 Quick Start

### Prerequisites

- Ruby (2.7 or higher)
- Bundler
- Git

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/youkoutaku/youkoutaku.github.io.git
   cd youkoutaku.github.io
   ```

2. Install dependencies:
   ```bash
   bundle install
   ```

### Development

Start the local development server:
```bash
bundle exec jekyll serve
```

The site will be available at `http://localhost:4000`

### Building for Production

Build the static site:
```bash
bundle exec jekyll build
```

## 📚 Resources & Documentation

- **Theme**: [Jekyll Chirpy Theme](https://github.com/cotes2020/jekyll-theme-chirpy)
- **Getting Started**: [Chirpy Documentation](https://chirpy.cotes.page/posts/getting-started/)
- **Writing Guide**: [Creating New Posts](https://chirpy.cotes.page/posts/write-a-new-post/)
- **Typography**: [Text and Typography Guide](https://chirpy.cotes.page/posts/text-and-typography/#fnref:footnote)
- **My Writing Notes**: [Personal Writing Guide](https://youkoutaku.github.io/posts/Writing/)

## 🔄 Maintenance & Updates

### Keeping the Theme Updated
Follow the [Upgrade Guide](https://github.com/cotes2020/jekyll-theme-chirpy/wiki/Upgrade-Guide#upgrading-from-starter) for detailed instructions.

#### Initial Setup (One-time only)

Add the upstream remote:
```bash
git remote add chirpy https://github.com/cotes2020/chirpy-starter.git
```

Verify the remote was added:
```bash
git remote -v
```

Expected output:
```
chirpy  https://github.com/cotes2020/chirpy-starter.git (fetch)
chirpy  https://github.com/cotes2020/chirpy-starter.git (push)
origin  https://github.com/youkoutaku/youkoutaku.github.io.git (fetch)
origin  https://github.com/youkoutaku/youkoutaku.github.io.git (push)
```

## ✍️ Writing Guidelines

### Creating New Posts

Posts are located in the `_posts/` directory and organized by category. Follow this naming convention:
```
YYYY-MM-DD-Title.md
```

### Front Matter Template

```yaml
---
title: "Your Post Title"
date: YYYY-MM-DD HH:MM:SS +/-TTTT
categories: [Category1, Category2]
tags: [tag1, tag2, tag3]
math: true  # Enable if using mathematical expressions
mermaid: true  # Enable if using diagrams
image:
  path: /path/to/image.jpg
  alt: Alternative text for the image
---
```

### Images

Store images in the `src/` directory and reference them as:
```markdown
![Alt text](src/path/to/image.png)
```

For featured images in posts:
```yaml
image:
  path: src/image.jpg
  alt: Description of the image
```

### Mathematical Expressions

This site supports [MathJax](https://www.mathjax.org/) for rendering mathematical notation.

**Important Notes:**
- Use `$x^\ast$` instead of `$x^*$` for optimal notation
- For subscripts with multiple characters, use proper grouping: `$x_{12}$` not `$x_{1_2}$`

Examples:
```markdown
Inline math: $E = mc^2$

Block math:
$$
\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}
$$
```

## 🤝 Contributing

This is a personal blog, but suggestions and corrections are welcome! Please feel free to:

1. Open an issue for content suggestions or corrections
2. Submit a pull request for typos or improvements
3. Share feedback on the content structure

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Note**: This README serves as both documentation and a quick reference for maintaining this Jekyll blog.
