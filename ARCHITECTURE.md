# System Architecture

## Overview

This document provides a detailed overview of the system architecture for the Social Media Listening Platform.

## High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        Client Layer                           │
│  ┌──────────────────────────────────────────────────────┐   │
│  │              React Frontend Application                │   │
│  │  - Dashboard UI                                        │   │
│  │  - Data Visualization                                  │   │
│  │  - User Authentication (Firebase)                      │   │
│  └──────────────────────────────────────────────────────┘   │
└───────────────────────────┬───────────────────────────────────┘
                            │ HTTPS/REST API
┌───────────────────────────▼───────────────────────────────────┐
│                      API Gateway Layer                         │
│  ┌──────────────────────────────────────────────────────┐   │
│  │              Flask Backend Server                     │   │
│  │  - RESTful API Endpoints                              │   │
│  │  - Request Validation                                 │   │
│  │  - Authentication Middleware                          │   │
│  │  - Error Handling                                     │   │
│  └──────────────────────────────────────────────────────┘   │
└───────────────────────────┬───────────────────────────────────┘
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                     │
┌───────▼────────┐  ┌───────▼────────┐  ┌────────▼────────┐
│  Service Layer │  │  Service Layer │  │  Service Layer  │
│                │  │                │  │                  │
│ RedditService  │  │ CommentAnalysis│  │ InfluencerTrust  │
│ - Data Fetch   │  │ Service        │  │ Service         │
│ - Preprocessing│  │ - AI Analysis   │  │ - Trust Signals │
│ - Deduplication│  │ - Keyword Extract│ │ - Score Calc    │
└───────┬────────┘  └───────┬────────┘  └────────┬────────┘
        │                   │                     │
        └───────────────────┼─────────────────────┘
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
┌───────▼────────┐  ┌───────▼────────┐  ┌──────▼────────┐
│  External APIs │  │  External APIs │  │  External APIs │
│                │  │                │  │                │
│   Reddit API   │  │    Groq API    │  │  Firebase      │
│                │  │  (Qwen3-32B)   │  │  - Auth        │
│                │  │                │  │  - Firestore   │
└────────────────┘  └────────────────┘  └────────────────┘
```

## Component Details

### Frontend (React)

**Responsibilities:**
- User interface and user experience
- Data visualization (charts, word clouds, tables)
- User authentication UI
- API communication with backend

**Key Technologies:**
- React.js
- React Router for navigation
- Axios for API calls
- Chart.js / Recharts for visualizations
- Firebase SDK for authentication

### Backend (Flask)

**Responsibilities:**
- RESTful API endpoints
- Business logic orchestration
- Data processing coordination
- Authentication and authorization
- Error handling and logging

**Key Technologies:**
- Flask (Python web framework)
- Flask-CORS for cross-origin requests
- Firebase Admin SDK for server-side auth
- Python logging for error tracking

### Service Layer

#### RedditService
- **Purpose**: Reddit data collection and preprocessing
- **Key Functions**:
  - Keyword-based post searching
  - Comment extraction
  - Data cleaning and deduplication
  - Sentiment preprocessing

#### CommentAnalysisService
- **Purpose**: Deep AI-powered comment analysis
- **Key Functions**:
  - Keyword extraction
  - Sentiment analysis
  - Persona identification
  - Motivation analysis
  - Risk/opportunity detection

#### InfluencerTrustService
- **Purpose**: Trust signal analysis
- **Key Functions**:
  - High trust signal detection (H1-H4)
  - Low trust signal detection (L1-L4)
  - Trust score calculation
  - Multi-platform analysis

#### CustomerValueService
- **Purpose**: Customer value extraction
- **Key Functions**:
  - Value dimension analysis (4 dimensions)
  - Cost dimension analysis (4 dimensions)
  - Delivered Value Score calculation
  - Recommendation generation

## Data Flow

### Keyword-based Analysis Flow

```
User Input (Keyword)
    ↓
RedditService.search_subreddit()
    ↓
Reddit API (Fetch Posts)
    ↓
DataProcessor.clean_text()
    ↓
Sentiment Analysis (VADER + ML + BERT)
    ↓
Aggregation & Metadata
    ↓
Response to Frontend
```

### URL-based Analysis Flow

```
User Input (URL)
    ↓
Platform Detection
    ↓
Comment Extraction (Reddit/YouTube/Twitter)
    ↓
CommentAnalysisService / InfluencerTrustService / CustomerValueService
    ↓
Groq API (Qwen3-32B) - Deep Analysis
    ↓
Result Processing & Normalization
    ↓
Response to Frontend
```

## Database Schema

### Firebase Firestore Collections

**users**
```
{
  uid: string,
  email: string,
  plan_key: string,
  created_at: timestamp,
  usage: {
    searches_this_month: number,
    comments_exported: number
  }
}
```

**analyses** (Optional - for caching)
```
{
  id: string,
  user_id: string,
  analysis_type: string,
  input_data: object,
  results: object,
  created_at: timestamp
}
```

## API Endpoints

### Authentication
- `POST /api/auth/login` - User authentication
- `POST /api/auth/verify` - Token verification

### Data Collection
- `POST /api/search-reddit` - Keyword-based Reddit search
- `POST /api/export-comments` - URL-based comment export

### Analysis
- `POST /api/analyze-comments` - General comment analysis
- `POST /api/check-influencer-trust` - Influencer trust analysis
- `POST /api/analyze-customer-value` - Customer value analysis
- `POST /api/sentiment_counts` - Sentiment distribution

### User Management
- `GET /api/user/usage` - Get user usage statistics
- `GET /api/user/quota` - Check quota limits

## Security Considerations

1. **Authentication**: Firebase Authentication with JWT tokens
2. **API Security**: Token-based authentication middleware
3. **Rate Limiting**: Per-user quota management
4. **Input Validation**: Comprehensive input sanitization
5. **Error Handling**: Secure error messages (no sensitive data exposure)

## Scalability

### Current Implementation
- Single Flask server instance
- Stateless API design
- External API dependencies (Reddit, Groq, Firebase)

### Future Scalability Options
- Horizontal scaling with load balancer
- Redis caching for frequent queries
- Message queue for async processing
- Database optimization for large datasets

## Deployment

### Current Setup
- Frontend: Render (Static site hosting)
- Backend: Render (Docker container)
- Database: Firebase Firestore (Cloud)

### Docker Configuration
```dockerfile
# Backend Dockerfile
FROM python:3.9
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "server.py"]
```

## Monitoring & Logging

- **Application Logs**: Python logging module
- **Error Tracking**: Structured error logging
- **Performance Monitoring**: Request/response time tracking
- **API Usage**: User quota and usage tracking

## Technology Stack Summary

| Layer | Technology |
|-------|-----------|
| Frontend | React.js, React Router, Axios |
| Backend | Flask, Python 3.9+ |
| Authentication | Firebase Authentication |
| Database | Firebase Firestore |
| AI/ML | Groq API (Qwen3-32B), VADER, BERT, Scikit-learn |
| APIs | Reddit API, YouTube API, Twitter API |
| Deployment | Docker, Render |
| Version Control | Git |
