# Backend Documentation

## Purpose
The backend provides API services, data storage, and AI chatbot integration for the Kyrgyz Heritage Platform.

## Architecture Overview
- Frontend → Backend → Database
- Backend → LLM API (if time allows)

## Core API Endpoints

### GET /articles
Returns all articles (sacred sites, petroglyphs, calendar content).
- Query params: type (sacred-sites, petroglyphs, calendar) to filter
- Returns: list of articles with id, title, content, type, etc.

### POST /chat
Accepts user chat queries and returns LLM responses.
- Input: user message, optional context/topic tag
- Output: chatbot answer

### Admin Endpoints (protected, admin-only)
These endpoints allow admins to manage articles. Access via footer link with authentication.

#### GET /admin/articles
Returns all articles for admin management.

#### POST /admin/articles
Creates a new article.
- Input: title, content, type, etc.

#### PUT /admin/articles/:id
Updates an existing article.

#### DELETE /admin/articles/:id
Deletes an article.

## Data Model Concepts

### Article
- id
- title
- content (rich text or markdown)
- type (sacred-sites, petroglyphs, calendar)
- imageUrl (optional)
- createdAt
- updatedAt
- dateModern
- description
- culturalNotes

### Quiz
- id
- section
- questions
- choices
- correctAnswer

## Non-Functional Requirements
- Performance: < 2s response time
- Scalability: support moderate concurrent users
- Usability: simple API contract, clear validation errors
- Security: sanitize input, validate payloads

## Integration Notes
- Use a cloud or hosted LLM API for chatbot responses
- Keep chatbot basic: answer cultural questions, no advanced domain reasoning required
- Avoid overbuilding the chat experience in the MVP
- Implement basic authentication for admin endpoints (e.g., simple password or token)
- Admin access via footer link, leading to a simple admin dashboard for CRUD operations
