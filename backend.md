# Backend Documentation

## Purpose
The backend provides API services, data storage, and AI chatbot integration for the Kyrgyz Heritage Platform.

## Architecture Overview
- Frontend → Backend → Database
- Backend → LLM API (if time allows)

## Core API Endpoints

### GET /sacred-sites
Returns metadata and content for sacred places.

### GET /petroglyphs
Returns petroglyph images, descriptions, and historical context.

### GET /calendar
Returns traditional calendar data and modern calendar comparisons.

### POST /chat
Accepts user chat queries and returns LLM responses.
- Input: user message, optional context/topic tag
- Output: chatbot answer

### POST /quiz/submit
Accepts quiz answers and returns quiz score.
- Input: quiz id, user answers
- Output: score, feedback, optionally leaderboard placement

## Data Model Concepts

### SacredSite
- id
- name
- location
- description
- culturalMeaning
- practices

### Petroglyph
- id
- title
- imageUrl
- description
- interpretation

### CalendarEntry
- id
- dateTraditional
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

## Future Backend Enhancements
- Add content management for admins
- Store quiz results for progress tracking
- Add leaderboard support
- Add caching for static content responses
