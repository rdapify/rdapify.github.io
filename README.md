# RDAPify Website

This repository hosts the built website for [RDAPify](https://github.com/rdapify/RDAPify) on GitHub Pages.

## 🌐 Live Site

- **Production**: https://rdapify.com
- **GitHub Pages**: https://rdapify.github.io

## 📦 About This Repository

This repository contains **only the built static files** from the main RDAPify repository. It is automatically updated by GitHub Actions.

### ⚠️ Important

**Do NOT edit files in this repository directly!**

All website source files are in the main repository:
- Source: https://github.com/rdapify/RDAPify/tree/main/website
- Documentation: https://github.com/rdapify/RDAPify/tree/main/docs

## 🔄 How It Works

```
RDAPify/website/ → Build → Deploy → rdapify.github.io → GitHub Pages → rdapify.com
```

1. Edit files in `RDAPify/website/` or `RDAPify/docs/`
2. Push to main branch
3. GitHub Actions builds the website
4. Built files are deployed to this repository
5. GitHub Pages serves the site at rdapify.com

## 🛠️ Development

To work on the website:

```bash
# Clone the main repository
git clone https://github.com/rdapify/RDAPify.git
cd RDAPify/website

# Install dependencies
npm install

# Start development server
npm start

# Build for production
npm run build
```

## 📚 Documentation

- [Main Repository](https://github.com/rdapify/RDAPify)
- [Website Setup Guide](https://github.com/rdapify/RDAPify/blob/main/GITHUB_SETUP.md)
- [Contributing Guide](https://github.com/rdapify/RDAPify/blob/main/CONTRIBUTING.md)

## 📄 License

MIT License - see [LICENSE](https://github.com/rdapify/RDAPify/blob/main/LICENSE)

---

© 2025 RDAPify Contributors
