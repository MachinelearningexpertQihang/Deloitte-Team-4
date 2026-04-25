# Deloitte Decision Intelligence Platform
**Capstone Project 2026 — Team 4**
Kyle Chen · Sadgee Pandey · Anastasia Raicevic · Ruo Yu Wang

## Overview
An AI-powered business decision platform that predicts investment ROI in under 10 seconds by combining ensemble machine learning with Claude AI market signal extraction.

## Architecture
- **Frontend**: React (port 3000), deployed on AWS EC2
- **Backend**: FastAPI + uvicorn (port 8000), deployed on AWS EC2
- **ML Model**: GBM + XGBoost + LightGBM voting ensemble, trained on 120,000 decisions, stored on S3
- **AI Layer**: Claude Sonnet 4.5 via AWS Bedrock — extracts market signals from news text and generates executive reports
- **Infrastructure**: AWS S3, Glue, SageMaker, Bedrock, Athena, EC2

## How It Works
1. Consultant inputs company profile, decision parameters, and macro indicators
2. Claude AI reads pasted market news and extracts 3 signals: consumer sentiment, competitive pressure, external risk
3. Ensemble ML model predicts ROI; AI signals adjust the base estimate
4. Claude generates an executive intelligence report with risks, recommendations, and timing

## Model Performance
- Directional accuracy: 75.2%
- Training data: 120,000 synthetic business decisions
- Industries: Manufacturing, SaaS, Retail, Healthcare, Finance
- Decision types: Marketing, Pricing, Expansion, R&D, Hiring

## Deployment
Backend runs on EC2 at port 8000. Frontend served via `serve` at port 3000.
IAM Role `deloitte-ec2-role` provides S3 and Bedrock access without hardcoded credentials.

## Limitations
- Current model trained on synthetic data
- Production deployment would require retraining on real Deloitte client data
- Directional signal only — not a precise financial forecast
