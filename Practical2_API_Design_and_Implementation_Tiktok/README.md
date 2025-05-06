# Practical 2: API Design and Implementation (TikTok)

## Overview

This practical involved developing a RESTful API for a TikTok-inspired social media application. The API was designed to handle key features like user accounts, videos, comments, likes, and followers. The backend was built using Node.js and Express, with in-memory storage used for managing data during development.

## Objectives

**Create RESTful Endpoints** : Define clean and meaningful URIs for core entities such as users, videos, and comments.

**Develop CRUD Functionality** : Build the essential create, read, update, and delete operations for each resource.

**Model Entity Relationships** : Implement features to support relationships like video likes and user followings.

**Error Management** : Integrate structured error handling for edge cases and invalid operations.

**Perform API Testing** : Validate functionality using tools like Postman or terminal-based curl requests.

## Steps Taken

### 1. Project Initialization

- To begin, I created a fresh Node.js project using Express. The initial setup included:

- Setting up the project directory and initializing it with npm init.

- Installing dependencies: express for the server, cors for CORS handling, morgan for logging, and body-parser for parsing JSON requests.

- Establishing a modular structure with folders for controllers, routes, models, and middleware.

- Configuring environment variables through a .env file to manage settings like the server port.

### 2. API Design

- I defined RESTful routes for three main resources:

- Videos: Routes for uploading, editing, listing, and removing videos.

- Users: Endpoints for creating and managing user accounts, as well as following and followers functionality.

- Comments: Features for users to leave and manage comments on videos.

Each resource supported standard operations. For example:

- GET /api/videos – Fetch all video entries.

- POST /api/videos – Submit a new video record.

- PUT /api/videos/:id – Update a specific video.

### 3. API Implementation

The Express framework served as the backbone of the API. Key components included:

- **Controllers** : Defined logic for handling requests to each resource (videos, users, comments).

- **Routes** : Linked HTTP requests to appropriate controller functions.

- **Middleware** : Introduced middlewares for parsing requests, error handling, and logging.

- **Mock Data** : Simulated application data through in-memory objects located in src/models/index.js.

## 4. Feature Development

- **Likes and Follows** : Added capabilities for users to like videos and follow others, enriching the interaction model.

- **Error Responses** : Developed centralized error handling to manage invalid operations and return consistent messages.

- **Input Validation** : Integrated simple checks to verify required fields in incoming requests.