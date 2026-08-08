# Al-Fawaz Warehouse - Architecture Overview

This document outlines the system architecture for the Al-Fawaz Medicines Warehouse application.

## System Architecture

```mermaid
graph TB
    subgraph Client["Client Layer"]
        Android["📱 Android App"]
        Web["🌐 Web Application"]
    end

    subgraph Firebase["Firebase Services"]
        Auth["🔐 Firebase Authentication"]
        Firestore["💾 Firestore Database"]
        Storage["📦 Cloud Storage"]
        Functions["⚡ Cloud Functions"]
        Messaging["📨 Cloud Messaging"]
    end

    subgraph Backend["Backend Services"]
        API["REST API"]
        Admin["Admin SDK"]
        Logic["Business Logic"]
    end

    subgraph Data["Data Layer"]
        Collections["Medicines Collection"]
        Orders["Orders Collection"]
        Inventory["Inventory Management"]
        Users["Users Database"]
    end

    subgraph External["External Services"]
        GoogleAPI["Google APIs"]
        Analytics["Analytics Service"]
        Notifications["Push Notifications"]
    end

    Android -->|Firebase SDK| Auth
    Web -->|Firebase SDK| Auth
    
    Auth --> Firestore
    Auth --> Storage
    
    Android -->|API Calls| API
    Web -->|API Calls| API
    
    API --> Admin
    Admin --> Functions
    
    Functions --> Logic
    Logic --> Firestore
    Logic --> Storage
    
    Firestore --> Collections
    Firestore --> Orders
    Firestore --> Inventory
    Firestore --> Users
    
    Functions --> Messaging
    Messaging --> Notifications
    
    Functions --> GoogleAPI
    Functions --> Analytics

    style Client fill:#e1f5ff
    style Firebase fill:#fff3e0
    style Backend fill:#f3e5f5
    style Data fill:#e8f5e9
    style External fill:#fce4ec
```

## Component Description

### Client Layer
- **Android App**: Native Android application for warehouse management and medicine distribution
- **Web Application**: Browser-based interface for administration and monitoring

### Firebase Services
- **Authentication**: Secure user login and session management
- **Firestore**: Real-time NoSQL database for medicines, orders, and inventory
- **Cloud Storage**: Image and document storage for medicine information
- **Cloud Functions**: Serverless backend logic and API endpoints
- **Cloud Messaging**: Push notifications for order updates and alerts

### Backend Services
- **REST API**: RESTful endpoints for client applications
- **Admin SDK**: Firebase Admin SDK for server-side operations
- **Business Logic**: Core application logic including order processing and inventory management

### Data Layer
- **Medicines Collection**: Product catalog with details and pricing
- **Orders Collection**: Customer orders and transaction history
- **Inventory Management**: Stock levels and warehouse management
- **Users Database**: User profiles and permissions

### External Services
- **Google APIs**: Integration with Google services
- **Analytics**: Event tracking and usage analytics
- **Push Notifications**: External notification delivery service

## Key Features

- 🏥 **Medicine Inventory Management**: Track medicines from brands like Domina, Medicco, Al-Mutahida, Ibn Rushd, Lama, Happy Cure, and Celia
- 📦 **Order Processing**: Handle customer orders with real-time updates
- 🔒 **Secure Authentication**: Firebase-based user authentication
- 📱 **Cross-Platform**: Support for Android and web clients
- 🔔 **Real-time Notifications**: Push notifications for order updates
- 📊 **Analytics & Reporting**: Track warehouse metrics and business analytics

## Deployment

The application is deployed on Google Firebase infrastructure, leveraging:
- Firestore for real-time database
- Cloud Functions for backend logic
- Cloud Storage for assets
- Firebase Authentication for security
