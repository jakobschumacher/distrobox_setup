# Distrobox Development Setups

Personal distrobox configurations for development environments. These are opinionated setups for my workflow - feel free to fork and customize for your needs.

> **Note**: This is a personal setup repository. The configurations include my preferred tools and development stack. You may want to review and modify the package lists before using.

## Available Configurations

### Tauri Development (`tauridev_distrobox.ini`)
Complete Tauri development environment with:
- Rust toolchain (stable, clippy, rustfmt)
- Node.js ecosystem (npm, yarn, pnpm, typescript)
- Tauri CLI and create-tauri-app
- Development tools (Claude Code, trunk)
- System libraries for Tauri app compilation
- Debugging tools and utilities

### JavaScript Development (`jsdev_distrobox.ini`)
Modern JavaScript/Node.js development environment with:
- Node.js LTS with npm, yarn, pnpm
- TypeScript and development tools
- Framework tools (React, Next.js, Vue CLI)
- Testing and linting (Jest, ESLint, Prettier)
- Process management (nodemon, pm2)

### R Development (`rdev_distrobox.ini`)
Statistical computing and data science environment with:
- R base and development packages
- Tidyverse, Shiny, R Markdown
- Data science libraries (caret, ggplot2, plotly)
- LaTeX support for document generation
- Python integration via reticulate

## Quick Project Setup

**Bootstrap from anywhere:**
```bash
curl -s https://raw.githubusercontent.com/jakobschumacher/distrobox-setups/main/bootstrap | bash
```

**One-time alias setup** (optional but recommended):
```bash
# Bootstrap script will offer to add these automatically
alias newproject='curl -s https://raw.githubusercontent.com/jakobschumacher/distrobox-setups/main/bootstrap | bash'
alias resume='[ -f .distrobox.ini ] && distrobox-enter $(grep "^\[" .distrobox.ini | tr -d "[]") || echo "No distrobox project found"'
```

**Daily workflow:**
```bash
# Create new project
newproject

# Resume existing project (from project folder)
cd 2025_09_19_myapp
resume
```

## Manual Usage (if needed)

```bash
# Tauri development
distrobox-create --file tauridev_distrobox.ini
distrobox-enter tauri-dev

# JavaScript development  
distrobox-create --file jsdev_distrobox.ini
distrobox-enter js-dev

# R development
distrobox-create --file rdev_distrobox.ini
distrobox-enter r-dev
```

## Notes
- Projects are created with `yyyy_mm_dd_projectname` naming convention
- Each project gets its own isolated container and git repository  
- R setup uses r2u for dramatically faster package installation
- Bootstrap script handles existing projects (enter/rebuild options)
- All configurations include comprehensive development toolsets
- GUI applications supported via X11/Wayland passthrough

