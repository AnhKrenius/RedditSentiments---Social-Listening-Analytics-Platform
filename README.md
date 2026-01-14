# Social Media Listening Platform: AI-Powered Sentiment Analysis Case Study

> A comprehensive case study of building an enterprise-grade social media listening platform that extracts actionable insights from Reddit, YouTube, and Twitter using advanced NLP and AI technologies.

## 🎯 Project Overview

This case study documents the development of **RedditSentiments**, an AI-powered social media listening web application that helps brands, marketers, and researchers understand public sentiment, market signals, influencer trust, and customer-perceived value by analyzing large volumes of user-generated conversations in near real-time.

### Key Challenge
Traditional sentiment analysis tools rely on simple metrics like star ratings or emoji counts, missing the rich context and nuanced insights available in long-form discussions on platforms like Reddit. This project addresses the need for context-aware, multi-dimensional analysis that connects specific content to actual user conversations.

### Solution
A full-stack web application that combines:
- **Advanced NLP**: Ensemble sentiment analysis (VADER + ML + BERT)
- **Modern LLMs**: Groq API with Qwen3-32B for deep analysis
- **Multi-platform Support**: Reddit, YouTube, Twitter
- **Business-focused Features**: Market analysis, influencer trust assessment, customer value extraction

## 🏗️ Architecture Overview

```
┌─────────────────┐
│   React Frontend │  (Interactive Dashboard)
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Flask Backend  │  (RESTful API)
└────────┬────────┘
         │
    ┌────┴────┐
    ▼         ▼
┌─────────┐ ┌──────────┐
│ Reddit  │ │   Groq    │
│   API   │ │    API    │
└─────────┘ └──────────┘
```

**Tech Stack:**
- **Frontend**: React.js with modern UI components
- **Backend**: Flask (Python) with RESTful API design
- **Authentication**: Firebase Authentication
- **Database**: Firebase Firestore
- **AI/ML**: Groq API (Qwen3-32B), VADER, BERT, Scikit-learn
- **Deployment**: Docker, Render (Cloud hosting)

## ✨ Key Features

### 1. Keyword-based Reddit Scraping + Sentiment Analysis
- Scrapes 1000+ Reddit posts per keyword
- Ensemble sentiment analysis (VADER + ML + BERT)
- Trend tracking over time with metadata
- Multi-Criteria Decision Making (MCDM) for sentiment ranking

### 2. URL-based Comment Scraping → Market Analysis
- Multi-platform support (Reddit, YouTube, Twitter)
- 93% accuracy in comment collection
- Deep AI analysis: keyword extraction, persona analysis, motivation analysis
- Risk and opportunity identification

### 3. URL-based Comment Scraping → Influencer Trust
- Trust signal categorization (High Trust H1-H4, Low Trust L1-L4)
- Trust score calculation
- Multi-platform reaction analysis
- Reputation risk assessment

### 4. URL-based Comment Scraping → Customer-Delivered Value
- 4-dimensional value analysis (Image, Personal, Services, Product)
- 4-dimensional cost analysis (Monetary, Time, Energy, Psychic)
- Delivered Value Score calculation
- Actionable recommendations

## 📊 Key Metrics & Results

- **Accuracy**: 93% in comment collection and analysis
- **Scale**: Processes 1000+ posts per keyword search
- **Performance**: Near real-time analysis (5-15 seconds for 100 comments)
- **Coverage**: Multi-platform support across Reddit, YouTube, Twitter
- **User Base**: Deployed and accessible at [redditsentiments.com](http://redditsentiments.com)

## 🔧 Technical Highlights

### Data Pipeline
1. **Collection**: Reddit API, YouTube API, Twitter API with automatic platform detection
2. **Preprocessing**: Keyword filtering, language detection, deduplication
3. **Analysis**: Ensemble NLP models + LLM-powered deep analysis
4. **Visualization**: Interactive dashboards with charts, word clouds, and data tables

### AI/ML Implementation
- **Sentiment Classification**: Ensemble of VADER (rule-based), Machine Learning models, and BERT transformers
- **Deep Analysis**: Groq API with Qwen3-32B for keyword extraction, persona analysis, motivation analysis
- **Topic Clustering**: Automatic theme and topic grouping
- **Signal Detection**: Trust signals, risks, and opportunities identification

### System Design
- **Microservices Architecture**: Separated frontend and backend
- **RESTful API**: Clean API design with proper error handling
- **Authentication**: Firebase-based user management
- **Scalability**: Docker containerization for easy deployment

## 📁 Project Structure

```
portfolio/
│
├── README.md                # This file
├── ARCHITECTURE.md          # Detailed system architecture
├── METRICS.md               # Performance metrics and results
├── screenshots/             # UI screenshots and demos
│   ├── dashboard.png
│   ├── sentiment-analysis.png
│   ├── market-analysis.png
│   └── influencer-trust.png
└── diagrams/
    └── system_architecture.png
```

## 🎓 Learning Outcomes

### Technical Skills Demonstrated
- Full-stack development (React + Flask)
- RESTful API design and implementation
- Integration with multiple third-party APIs
- Advanced NLP and AI model integration
- Real-time data processing and analysis
- Cloud deployment and DevOps practices

### Business Impact
- Enables data-driven decision making for brands
- Provides actionable insights for marketing strategies
- Helps assess influencer partnership effectiveness
- Supports product roadmap alignment with customer needs

## 🔗 Related Documentation

- [ARCHITECTURE.md](./ARCHITECTURE.md) - Detailed system architecture
- [METRICS.md](./METRICS.md) - Performance metrics and results

## 📸 Screenshots

See the `screenshots/` directory for UI demonstrations and feature showcases.

## 🚀 Live Demo

The application is deployed and accessible at: [redditsentiments.com](http://redditsentiments.com)

---

**Note**: This is a case study repository for portfolio purposes. The actual codebase is maintained separately.
