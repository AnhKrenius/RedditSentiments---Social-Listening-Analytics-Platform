# Social Media Listening Platform: AI-Powered Sentiment Analysis Case Study

> A comprehensive case study of building a social media listening platform that extracts actionable insights from Reddit, Facebook, Instagram, Tiktok, YouTube, and X (Twitter) using advanced Natural Language Processing and AI technologies.

## 🎯 Project Overview

This case study documents the development of **RedditSentiments**, an AI-powered social media listening web application that helps brands, marketers, and researchers understand public sentiment, market signals, influencer trust, and customer-perceived value by analyzing large volumes of user-generated conversations in near real-time.

### Key Challenge
Traditional sentiment analysis tools rely on simple metrics like star ratings or emoji counts, missing the rich context and nuanced insights available in long-form discussions. This project addresses the need for context-aware, multi-dimensional analysis that connects specific content to actual user conversations.
On the other hand, while many of these platforms have become increasingly strict about data access, RedditSentiments is designed to work within these constraints and still surface meaningful, comparable insights across channels

### Solution
A full-stack web application that combines:
- **Advanced NLP**: Ensemble sentiment analysis (VADER + ML + BERT)
- **Modern and fast LLMs**
- **Multi-platform Support**: Reddit, YouTube, Twitter, Facebook, Instagram, Tiktok
- **Business-focused Features**: Market analysis, influencer trust assessment, customer value extraction

## 🏗️ Tech Stack:
- **Frontend**: React.js with modern UI components
- **Backend**: Flask (Python) with RESTful API design
- **Authentication**: Firebase Authentication
- **Database**: Firebase Firestore
- **AI/ML**: Groq API, VADER, BERT, Scikit-learn
- **Deployment**: Docker, Render (Cloud hosting)
- **Data Scraping**: Public social platform data access via official APIs and compliant data collection services
- **Payments & Billing**: Stripe (subscription and usage-based billing)


## ✨ Key Features

### 1. Keyword-based Reddit Scraping + Sentiment Analysis
- Scrapes up to 1000+ Reddit posts per keyword
- Ensemble sentiment analysis (VADER + ML + BERT)
- Trend tracking over time with metadata
- Identifies the most frequently mentioned keywords/themes by a wordcloud

### 2. URL-based Comment Scraping → Market Analysis
- Identifies recurring themes, concerns, and motivations in organic discussions
- Surfaces unmet needs, risks, and emerging opportunities
- Helps explain why people react the way they do
This is useful for understanding broader market signals beyond surface-level sentiment

### 3. URL-based Comment Scraping → Influencer Trust
- Analyzes audience reactions to influencer-related or influencer-linked content
- Distinguishes genuine trust and validation from skepticism, criticism, or backlash
- Focuses on credibility and perceived authenticity, not just engagement volume
This helps teams assess influence quality rather than relying only on reach or likes

### 4. URL-based Comment Scraping → Customer-Delivered Value
- 4-dimensional value analysis (Image, Personal, Services, Product) and 4-dimensional cost analysis (Monetary, Time, Energy, Psychic) -> Delivered Value Score calculation
- Extracts what users say they actually gained from a product or experience
- Compares perceived value with perceived costs
This helps teams identify gaps between marketing claims and real user experience, supports clearer positioning, messaging, and product improvement decisions.

## 📊 Key Metrics & Results

- **Accuracy**: 93% in comment collection and analysis
- **Scale**: Processes up to 1000+ posts per keyword search
- **Performance**: Near real-time analysis (5-15 seconds for 100 comments)
- **Coverage**: Multi-platform support across Reddit, YouTube, Twitter, Facebook, Instagram, Tiktok
- **User Base**: Deployed and accessible at [redditsentiments.com](http://redditsentiments.com)

## 🔧 Technical Highlights

### Data Pipeline
<img width="940" height="496" alt="image" src="https://github.com/user-attachments/assets/f910e66b-d5aa-4ffb-961c-c9e823311acf" />

1. **Collection**: Keyword-based and URL-based collection with automatic platform detection
2. **Preprocessing**: Keyword filtering, language detection, deduplication, preparing text for analysis and aggregation
3. **Analysis**: Combines multiple analytical modules to provide a more complete picture of how people perceive content,, brands, products, or creators
4. **Insight Delivery**: Interactive dashboards with charts, word clouds, and data tables

### AI/ML Implementation
- **Sentiment Classification**: Ensemble of VADER (rule-based), Machine Learning models, and BERT transformers
- **Deep Analysis**: LLM for keyword extraction, persona analysis, motivation analysis
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
│   ├── pricing.png
│   ├── customer_delivered_value.png
│   ├── market_analysis.png
│   └── influencer_trust.png
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
