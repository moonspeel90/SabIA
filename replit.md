# Overview

Sabia is a Portuguese-language educational chatbot web application designed to help users learn through interactive conversations. The application features a simple chat interface where users can ask questions about various subjects (particularly mathematics) and receive educational responses. The system stores chat history in Firebase Firestore for persistence and potential future analysis.

**Project Status**: Successfully imported from GitHub and configured for Replit environment (September 27, 2025)

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
The application follows a Model-View-ViewModel (MVVM) pattern implemented in vanilla JavaScript:

- **View Layer**: Single HTML page (`index.html`) with a minimalist chat interface using Bulma CSS framework for styling
- **ViewModel Layer**: `app.js` handles user interactions, event handling, and DOM manipulation
- **Model Layer**: `model.js` manages data operations and Firebase interactions using ES6 modules

The architecture choice prioritizes simplicity and maintainability for an educational tool, avoiding complex frameworks that might add unnecessary overhead.

## Backend Architecture
The application uses a serverless approach with Firebase as the backend-as-a-service:

- **Database**: Firebase Firestore for storing chat messages with timestamps
- **Development Server**: HTTP server serving static files on port 5000 with CORS enabled
- **No Server Logic**: All processing happens client-side with simple rule-based response generation

This serverless approach reduces infrastructure complexity and costs while providing real-time data synchronization capabilities.

## Data Storage
- **Primary Database**: Firebase Firestore with a simple `chat` collection structure
- **Schema**: Each document contains `user` message, `bot` response, and `timestamp` fields
- **Access Pattern**: Append-only writes for new messages, ordered reads for chat history

The schema design supports future enhancements like user sessions, conversation threading, and analytics.

## Response Generation
Currently implements a simple keyword-based response system:
- **Pattern Matching**: Basic string matching for educational topics (e.g., "matemática" triggers math-related responses)
- **Fallback Response**: Generic response for unmatched queries
- **Extensibility**: Architecture allows for future integration with AI/ML services

# Replit Environment Configuration

## Recent Changes (September 27, 2025)
- **GitHub Import**: Project successfully imported from GitHub repository
- **Firebase SDK Fix**: Added missing Firebase JavaScript SDK imports to HTML (v9.23.0)
- **Development Server**: Configured http-server to serve static files on port 5000 with CORS
- **Workflow Setup**: Created "Frontend Server" workflow for development
- **Deployment Config**: Configured autoscale deployment for production

## Development Workflow
- **Local Development**: Run `npx http-server public -a 0.0.0.0 -p 5000 --cors`
- **Production Deployment**: Uses autoscale deployment target with static file serving

# External Dependencies

## Firebase Services
- **Firebase Firestore**: Real-time NoSQL database for chat message persistence
- **Firebase Project**: sabia-projeto (configured with API keys in firebase-config.js)
- **Firebase SDK**: Version 9.23.0 compatibility mode loaded via CDN

## Frontend Libraries
- **Bulma CSS**: Version 1.0.4 loaded via CDN for responsive UI components and styling
- **Firebase JavaScript SDK**: Loaded via CDN for client-side Firebase integration

## Development Tools
- **Firebase Tools**: CLI for deployment and project management (installed via npm)
- **HTTP Server**: Local development server for testing (installed via npm)
- **Node.js**: Version 20 runtime environment

## Browser Compatibility
Supports modern browsers including Firefox, Chrome, Safari, and Edge with ES6 module support required for the application architecture.