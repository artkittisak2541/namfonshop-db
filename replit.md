# Thai Fashion E-commerce Platform

## Overview

This is a full-stack e-commerce application built for a Thai fashion retailer ("น้ำฝนแฟชั่น" - Rain Fashion). The application provides a modern online shopping experience with product browsing, cart management, and filtering capabilities, all designed with Thai language support and cultural preferences in mind.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

The application follows a **monorepo architecture** with clear separation between frontend and backend concerns:

- **Frontend**: React SPA with TypeScript, served by Vite during development
- **Backend**: Express.js REST API with TypeScript
- **Database**: PostgreSQL with Drizzle ORM for type-safe database operations
- **Styling**: Tailwind CSS with shadcn/ui component library
- **State Management**: TanStack Query for server state management

## Key Components

### Frontend Architecture
- **Framework**: React 18 with TypeScript and Vite bundler
- **UI Library**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom Thai fashion brand colors and Thai/English font support
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack Query for server state, React hooks for local state

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Database ORM**: Drizzle with PostgreSQL dialect
- **Session Management**: Session-based cart management using localStorage session IDs
- **API Design**: RESTful endpoints with proper error handling and logging

### Database Schema
- **Products Table**: Stores product information including Thai names, descriptions, pricing, categories, images, sizes, colors, and feature lists
- **Cart Items Table**: Manages shopping cart with session-based persistence, linking to products with quantity and variant selections

### Authentication & Authorization
- **Session Management**: Client-generated session IDs stored in localStorage for cart persistence
- **No User Authentication**: Current implementation uses anonymous sessions for shopping cart functionality

## Data Flow

1. **Product Display**: Client fetches products from `/api/products` with filtering parameters
2. **Search & Filtering**: Real-time filtering by category, price range, search query, and sorting options
3. **Cart Management**: Session-based cart operations via `/api/cart` endpoints
4. **State Synchronization**: TanStack Query manages cache invalidation and optimistic updates

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Neon PostgreSQL serverless driver
- **drizzle-orm**: Type-safe ORM with PostgreSQL support
- **@tanstack/react-query**: Server state management
- **@radix-ui/***: Headless UI components for accessibility
- **tailwindcss**: Utility-first CSS framework

### Development Tools
- **Vite**: Fast development server and build tool
- **TypeScript**: Type safety across frontend and backend
- **ESBuild**: Fast JavaScript bundler for production builds

### UI Components
- Complete shadcn/ui component library including forms, dialogs, navigation, and data display components
- Tailwind CSS for styling with custom Thai brand color scheme

## Deployment Strategy

**Development Environment**:
- Vite dev server for frontend with HMR
- tsx for running TypeScript server with auto-reload
- Replit-specific plugins for development experience

**Production Build**:
- Frontend: Vite builds React app to static files in `dist/public`
- Backend: ESBuild bundles server code to `dist/index.js`
- Single executable deployment with static file serving

**Database**:
- Uses Drizzle migrations in `./migrations` directory
- PostgreSQL connection via `DATABASE_URL` environment variable
- Production-ready with Neon serverless PostgreSQL

**Key Build Considerations**:
- Shared TypeScript configuration across client, server, and shared modules
- Path aliases for clean imports (`@/` for client, `@shared/` for shared types)
- ES modules throughout the stack for modern JavaScript features
- Environment-specific Vite plugin loading for Replit development features