# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is **ErisRWA** - a Real World Asset (RWA) marketplace frontend built with React, TypeScript, and Vite. The application enables two types of users:
- **Investors**: Can browse, invest in, and manage RWA investments
- **RWA Project Originators**: Can list and manage their real-world asset projects

## Commands

### Development
```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run preview      # Preview production build
npm run lint         # Run ESLint
```

## Architecture

### Tech Stack
- **Frontend**: React 18 + TypeScript + Vite
- **Styling**: Tailwind CSS
- **Routing**: React Router v6
- **State Management**: React Context (AuthContext)
- **Icons**: Lucide React

### Key Application Structure

#### Authentication & Authorization
- **AuthContext** (`src/context/AuthContext.tsx`): Manages user authentication state
- **ProtectedRoute** component: Handles route protection based on user type
- Mock authentication system with localStorage persistence
- Two user types: `investor` and `rwa-project` with different access levels

#### User Types & Permissions
- **Investors**: Access marketplace, property details, academy, and investment dashboard
- **RWA Projects**: Access project management dashboard and listing tools
- Route-level protection enforces user type restrictions

#### Core Data Models
- **User**: Includes KYC status, subscription tiers, and profile completion
- **RWA**: Real-world asset properties with investment details
- **InvestedRWA**: User's investment portfolio items
- **AcademyLesson**: Educational content with premium tier restrictions

#### Page Structure
- **Public pages**: Landing, login, register, about, legal pages
- **Protected pages**: Dashboard (user-specific), marketplace, property details, academy
- **Feature landing pages**: Preview pages for marketplace, academy, and dashboard features

#### Component Organization
- **Layout**: Header, footer, and main layout wrapper
- **Modals**: Investment, KYC, profile, and feature preview modals
- **Protected routes**: Role-based access control
- **Reusable components**: Pricing sections, brand kit, scroll management

### Development Notes

#### Mock Data & Demo Accounts
The application uses mock authentication with pre-configured demo accounts:
- Demo investor: `investor@demo.com` (premium tier, KYC approved)
- Demo originator: `originator@demo.com` (premium tier, KYC approved)

#### State Management
- Primary state management through React Context
- User authentication state persisted to localStorage
- No external state management library currently used

#### Routing Strategy
- React Router v6 with declarative route protection
- User type-based route restrictions
- Automatic redirect to login for unauthenticated users
- Fallback redirect to home for unmatched routes