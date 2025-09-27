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
- Essential R packages for data analysis
- LaTeX support for document generation
- Development tools and utilities

### Vala Development (`valadev_distrobox.ini`)
Modern Vala development environment with Ubuntu 25.04:
- Vala compiler and documentation tools
- GTK 3/4 and Libadwaita for modern UI development
- Complete GLib ecosystem (GObject, GIO, GStreamer)
- Folks libraries for contact management and social integration
- Evolution Data Server integration (contacts, calendar, accounts)
- Additional Vala libraries (Secret, Notify, Peas plugins)
- Build tools (Meson, Ninja, CMake)

## Quick Project Setup

**Bootstrap from anywhere:**
```bash
curl -s https://raw.githubusercontent.com/jakobschumacher/distrobox_setup/main/bootstrap -o /tmp/bootstrap && bash /tmp/bootstrap
```

**One-time alias setup** (recommended):
```bash
# Add to ~/.bashrc
echo "" >> ~/.bashrc
echo "# Distrobox project aliases" >> ~/.bashrc
echo "alias newproject='curl -s https://raw.githubusercontent.com/jakobschumacher/distrobox_setup/main/bootstrap -o /tmp/bootstrap && bash /tmp/bootstrap'" >> ~/.bashrc
echo "alias resume='[ -f .distrobox.ini ] && distrobox-enter \$(grep \"^\\[\" .distrobox.ini | tr -d \"[]\") || echo \"No distrobox project found\"'" >> ~/.bashrc

# Reload shell
source ~/.bashrc
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
distrobox-assemble create --file tauridev_distrobox.ini
distrobox-enter tauri-dev

# JavaScript development  
distrobox-assemble create --file jsdev_distrobox.ini
distrobox-enter js-dev

# R development
distrobox-assemble create --file rdev_distrobox.ini
distrobox-enter r-dev

# Vala development
distrobox-assemble create --file valadev_distrobox.ini
distrobox-enter vala-dev
```

## Notes
- Projects are created with `yyyy_mm_dd_projectname` naming convention
- Each project gets its own isolated container and git repository  
- R setup uses r2u for dramatically faster package installation
- Bootstrap script handles existing projects (enter/rebuild options)
- All configurations include comprehensive development toolsets
- GUI applications supported via X11/Wayland passthrough

