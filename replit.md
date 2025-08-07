# QutbiDownloader - Universal Media Downloader

## Overview

QutbiDownloader is a complete full-stack web application that allows users to download videos and audio content from popular social media platforms including YouTube, Instagram, TikTok, Facebook, Twitter/X, and Vimeo. The application provides a clean, responsive interface where users can paste video URLs and choose from multiple quality and format options for downloading.

**Status: ✅ FULLY FUNCTIONAL** - Application is deployed and working with successful video/audio downloads, multiple format options, and proper error handling.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
The frontend is built using **React 18** with **TypeScript** and follows modern React patterns:

- **UI Framework**: Built with **shadcn/ui** components providing a comprehensive design system with Radix UI primitives
- **Styling**: **Tailwind CSS** with CSS variables for theming and dark mode support
- **State Management**: **TanStack Query (React Query)** for server state management and caching
- **Routing**: **Wouter** for lightweight client-side routing
- **Form Handling**: **React Hook Form** with **Zod** validation
- **Theme System**: Custom theme provider supporting light/dark modes with system preference detection

The application structure includes:
- Home page with download interface and platform grid
- Static pages (FAQ, Terms, Privacy, Contact)
- Responsive layout with mobile-first design
- Component-based architecture with reusable UI components

### Backend Architecture
The backend is built with **Express.js** and **TypeScript**:

- **Runtime**: **Node.js** with ESM modules
- **Web Framework**: **Express.js** with custom middleware for logging and error handling
- **Media Processing**: **yt-dlp** integration for fetching video metadata and download URLs
- **Security**: Rate limiting (10 requests per 15 minutes), URL sanitization, and **Helmet** for security headers
- **Caching**: In-memory caching with TTL for media information to improve performance
- **Development**: **Vite** integration for HMR and development server

### Data Storage Solutions
- **Database**: **PostgreSQL** with **Drizzle ORM** for type-safe database operations
- **Database Provider**: **Neon Database** (serverless PostgreSQL)
- **Schema Management**: **Drizzle Kit** for migrations and schema management
- **Session Storage**: **connect-pg-simple** for PostgreSQL session storage
- **Caching**: Memory-based caching for media info with configurable TTL

The storage layer uses a clean interface pattern allowing for easy switching between storage implementations.

### Authentication and Authorization
Currently implemented as a stateless application with:
- IP-based rate limiting for abuse prevention
- No user authentication required
- Request logging for monitoring and analytics
- Session management infrastructure ready for future user features

### API Design
RESTful API with typed request/response schemas:
- **POST /api/fetch**: Main endpoint for fetching media information and available formats
- **GET /api/download/:formatId**: Download endpoint that generates direct download URLs using yt-dlp
- **GET /api/health**: Health check endpoint
- **GET /api/platforms**: Supported platforms information

Request validation using **Zod** schemas ensures type safety and data integrity. The download system uses yt-dlp to generate authentic direct download URLs, avoiding proxy streaming issues and 403 errors.

## External Dependencies

### Core Media Processing
- **yt-dlp**: Python-based tool for extracting media metadata and download URLs from various platforms
- **child_process**: Node.js spawn for executing yt-dlp commands safely

### Database and Storage
- **@neondatabase/serverless**: Serverless PostgreSQL database connection
- **drizzle-orm**: Type-safe ORM for database operations
- **drizzle-kit**: Schema management and migrations
- **connect-pg-simple**: PostgreSQL session store

### Security and Rate Limiting
- **express-rate-limit**: IP-based rate limiting middleware
- **helmet**: Security headers middleware

### UI and Styling
- **@radix-ui/\***: Comprehensive set of accessible UI primitives
- **shadcn/ui**: Pre-built component library built on Radix UI
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Utility for creating variant-based component APIs
- **lucide-react**: Icon library

### Development and Build Tools
- **Vite**: Build tool and development server with HMR
- **TypeScript**: Type checking and compilation
- **ESBuild**: Fast JavaScript bundler for production builds
- **tsx**: TypeScript execution for development

### Third-Party Integrations
The application integrates with multiple social media platforms through yt-dlp:
- YouTube
- Instagram  
- TikTok
- Facebook
- Twitter/X
- Vimeo

All platform integrations are handled server-side through yt-dlp, ensuring no direct API dependencies on social media platforms.

## Recent Changes (August 6, 2025)

### Core Implementation Completed
- ✅ Full-stack application deployed and functional
- ✅ React frontend with modern UI components and dark/light theme
- ✅ Express backend with yt-dlp integration
- ✅ Multiple video quality options (144p to 4K when available)
- ✅ Audio format support with various bitrates
- ✅ Direct download system using yt-dlp URL generation
- ✅ Rate limiting and security features implemented
- ✅ Complete page structure (Home, FAQ, Terms, Privacy, Contact)

### Technical Fixes Applied
- ✅ Installed required packages (express-rate-limit, helmet, yt-dlp)
- ✅ Fixed Content Security Policy for Vite development
- ✅ Added proxy trust settings for rate limiting
- ✅ Enhanced format processing for better quality detection
- ✅ Implemented reliable download system avoiding 403 errors
- ✅ Added comprehensive error handling and user feedback

### Current Status
The application is fully operational with successful video downloads from YouTube and other supported platforms. Users can select from multiple video qualities and audio formats, and downloads complete successfully through the yt-dlp integration.