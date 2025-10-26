# Discord Verification Website

## Overview
A professional Discord server verification system with OAuth2 integration, privacy-focused hashed IP logging, and automatic role assignment. Built with React, Express, and Discord API.

## Purpose
This application helps Discord server administrators verify members to prevent alts, raids, and maintain community safety. It implements transparent data collection with automatic cleanup and privacy controls.

## Recent Changes (2025-10-26)
- Initial project setup with full-stack TypeScript implementation
- Implemented Discord OAuth2 flow for user verification
- Created privacy-focused IP hashing system with configurable retention
- Built automatic role assignment (add member role, remove restricted role)
- Designed clean, Discord-themed UI with consent page, success page, and error page
- Implemented JSON file-based data persistence with automatic cleanup

## Architecture

### Frontend (React + TypeScript)
- **Consent Page** (`/`) - Landing page explaining data collection with consent information
- **Success Page** (`/success`) - Confirmation after successful verification
- **Error Page** (`/error`) - User-friendly error handling
- Uses Discord brand colors (#5865F2 primary blue) and Inter font
- Fully responsive design with shadcn/ui components

### Backend (Express + TypeScript)
- **OAuth Flow**:
  - `/oauth/start` - Redirects to Discord authorization
  - `/oauth/callback` - Handles Discord response, creates record, assigns roles
- **API Endpoints**:
  - `GET /api/config` - Returns data retention configuration
  - `POST /api/privacy/delete` - Deletes user records by Discord ID
- **Data Storage**: JSON file-based persistence (`db.json`)
- **Automatic Cleanup**: Runs every 6 hours to remove expired records

### Discord Integration
- OAuth2 "identify" scope for user verification
- Bot API for role management
- Configurable member and restricted roles
- SHA-256 hashed IP addresses with custom salt

## Environment Variables (Required)

### Discord Application
- `DISCORD_CLIENT_ID` - Discord application client ID
- `DISCORD_CLIENT_SECRET` - Discord application client secret
- `DISCORD_BOT_TOKEN` - Discord bot token for role management

### Discord Server
- `DISCORD_GUILD_ID` - Server ID where verification occurs
- `DISCORD_MEMBER_ROLE_ID` - Role to assign to verified members
- `DISCORD_RESTRICTED_ROLE_ID` - (Optional) Role to remove after verification

### Security
- `HASH_SALT` - Random string for IP hashing (32+ characters recommended)
- `DATA_RETENTION_DAYS` - (Optional) Days to retain records (default: 30)

## OAuth2 Setup
1. Create Discord application at https://discord.com/developers/applications
2. Add OAuth2 redirect URIs:
   - Development: `http://localhost:5000/oauth/callback`
   - Production: `https://your-repl-url.replit.app/oauth/callback`
3. Enable bot with "Manage Roles" permission
4. Invite bot to your server with appropriate permissions

**Note**: The application automatically detects localhost and uses HTTP for development, HTTPS for production.

## Project Structure
```
├── client/src/
│   ├── pages/
│   │   ├── verify-consent.tsx - Main consent/landing page
│   │   ├── verify-success.tsx - Success confirmation
│   │   └── verify-error.tsx - Error handling
│   ├── App.tsx - Main app with routing
│   └── index.css - Design tokens and styling
├── server/
│   ├── routes.ts - API endpoints and OAuth flow
│   ├── discord.ts - Discord API integration
│   └── storage.ts - Data persistence layer
├── shared/
│   └── schema.ts - Shared TypeScript types
└── design_guidelines.md - UI/UX specifications
```

## Design Principles
- Trust-first design with clean, professional aesthetic
- Discord ecosystem alignment (brand colors, typography)
- Information clarity for consent details
- No animations - stability and professionalism focused
- Fully accessible with proper ARIA labels and test IDs

## Data Privacy
- IP addresses are hashed with SHA-256 + custom salt
- Automatic deletion after configured retention period
- Manual deletion available via API endpoint
- Transparent consent process with clear data collection explanation
- Data never shared outside moderation team

## User Preferences
- Prefers Discord-themed design with brand blue (#5865F2)
- Values privacy and security transparency
- Requires automatic data cleanup and retention controls
- Wants clear, scannable consent information
