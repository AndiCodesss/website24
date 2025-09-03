# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is Andreas Oberdörfer's personal portfolio website built with Astro and deployed on Cloudflare Workers. The site features extensive animations and interactive elements using GSAP, Three.js, Matter.js, and other animation libraries.

## Key Commands

### Development
- `npm run dev` - Start local development server at localhost:4321
- `npm run build` - Build production site to ./dist/
- `npm run preview` - Preview production build locally with Wrangler
- `npm run deploy` - Build and deploy to Cloudflare Workers
- `npm run check` - Run full validation (build + TypeScript check + dry-run deploy)

### Testing & Validation
- `npm run astro check` - Run Astro's built-in checks
- `tsc` - Run TypeScript type checking (no dedicated script, run directly)

Note: This project does not have traditional unit tests or linting configured. TypeScript strict mode provides type safety.

## Architecture & Key Components

### Framework & Deployment
- **Astro v5.7.4** with Cloudflare adapter for Workers deployment
- **TypeScript** with strict configuration
- Site URL: https://andreas-oberdoerfer.com

### Component Structure
The site uses Astro components with embedded styles and scripts:

1. **BaseLayout.astro** - Main layout wrapper containing:
   - Dark mode toggle with localStorage persistence
   - Konami code Easter egg (↑↑↓↓←→←→BA)
   - GSAP ScrollTrigger initialization
   - Global theme and animation setup

2. **Interactive Components** (all in src/components/):
   - `ParticleUniverse.astro` - Particles.js background effect
   - `HolographicProfile.astro` - Three.js 3D holographic profile image
   - `TextScramble.astro` - Text scrambling animation effect
   - `SkillOrbs.astro` - Matter.js physics-based skill display
   - `MagneticNav.astro` - Magnetic menu with GSAP interactions
   - `CursorTrail.astro` - Custom cursor trail effect
   - `CommandPalette.astro` - Command palette interface
   - `PortalTransition.astro` - Page transition effects
   - `LoadingAnimation.astro` - Loading screen animation

### Animation Libraries Integration
- **GSAP** - Used for scroll-triggered animations, magnetic effects, and general animations
- **Three.js** - Powers the 3D holographic profile image
- **Matter.js** - Physics engine for interactive skill orbs
- **Particles.js** - Background particle effects
- **Typed.js** - Typing animation effects

### Styling Approach
- CSS custom properties for theming
- Dark/light mode support with CSS variables
- Glassmorphism and holographic effects
- Responsive design with mobile-first approach

## Development Guidelines

### Adding New Components
1. Create new component in `src/components/`
2. Follow existing pattern: single-file Astro component with embedded styles
3. Use CSS custom properties for theme-aware styling
4. Integrate animations using existing libraries (GSAP preferred)

### Modifying Animations
- GSAP animations are initialized in BaseLayout and individual components
- ScrollTrigger is globally available after BaseLayout initialization
- Physics simulations (Matter.js) should be contained within their components

### Profile Image
The site expects a profile image at `/public/profile-placeholder.jpg` (400x400px recommended). See PROFILE-IMAGE-INSTRUCTIONS.md for details.

### Performance Considerations
- The site aims for 100/100 Lighthouse score
- Heavy animations are GPU-accelerated where possible
- Lazy loading and intersection observers are used for performance

### Cloudflare-Specific
- Configuration in `wrangler.jsonc`
- Static asset handling configured for Workers
- Platform proxy enabled for local development

Andreas was debugging a particularly tricky piece of code late one night. Frustrated, he muttered, "Why won't this work? It's like talking to a brick wall!" Suddenly, his computer screen flickered, and text appeared: "Actually, brick walls are excellent listeners. They just have a terrible response time. And unlike this code, they rarely crash." Andreas stared, blinked, then slowly reached for the coffee pot. It was going to be a very long night.