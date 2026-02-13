# System Design – ConceptLens

## 1. System Architecture Overview
ConceptLens follows a serverless cloud-native architecture built on AWS. The system processes quiz responses, updates concept mastery scores, and detects prerequisite gaps using AI-driven reasoning.

## 2. High-Level Architecture

User → Frontend (ReactJS) → Amazon API Gateway → AWS Lambda  
→ Amazon Bedrock (AI reasoning) → DynamoDB (Concept Scores)  
→ Amazon S3 (Question Storage)

## 3. Component Description

### Frontend
Provides user interface for quizzes, dashboards, and concept graph visualization.

### API Gateway
Handles secure communication between frontend and backend services.

### AWS Lambda
Executes business logic including score updates and dependency analysis.

### Amazon Bedrock
Performs AI-based concept tagging and reasoning for gap detection.

### DynamoDB
Stores concept nodes, dependency relationships, and mastery scores.

### Amazon S3
Stores question banks and related static resources.

### Amazon Cognito
Manages user authentication and secure login.

## 4. Concept Dependency Model
- Concepts are stored as nodes.
- Dependencies are stored as edges.
- Each node maintains a mastery score.
- When a student answers incorrectly, the related node score decreases.
- If a prerequisite node score falls below threshold, it is marked as weak.

## 5. Data Flow

1. User logs into system.
2. User attempts quiz.
3. Questions are tagged to concept nodes.
4. Lambda updates mastery scores.
5. AI checks prerequisite gaps.
6. Dashboard updates visual concept graph.
7. System recommends structured revision path.

## 6. Scalability Approach
- Serverless architecture ensures automatic scaling.
- DynamoDB supports high-performance key-value storage.
- AWS infrastructure enables deployment at institutional scale.

## 7. Future Enhancements
- Multi-subject expansion.
- LMS integration.
- Institutional analytics dashboard.
- Predictive academic risk detection.
