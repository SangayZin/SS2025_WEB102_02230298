# Practical 1: RESTful API Design and Implementation

## Summary

In this project, I developed a RESTful API for a basic social media platform modeled after Instagram. The primary objective was to build endpoints for managing entities such as users, posts, comments, likes, and followers. The API adheres to REST principles, correctly utilizes HTTP methods, and incorporates features such as pagination, error handling, and content negotiation.

## Project Goals

1. Design REST-Compliant Endpoints: Structure intuitive and resource-oriented URIs.

2. Enable CRUD Operations: Implement functionality to create, read, update, and delete resources.

3. Implement Robust Error Handling: Gracefully manage errors like missing resources or access violations.

4. Support Pagination: Handle large datasets with pagination parameters.

5. Enable Content Negotiation: Allow clients to choose between JSON and XML formats.

6. Create API Documentation: Provide clear and accessible documentation in HTML format.

## Implementation Process

### 1. Initial Setup

The project was initialized using Node.js and Express. The setup included:

* Creating the project directory and initializing it with npm init.

* Installing essential dependencies such as express, morgan (for logging), cors, and helmet (for security).

* Structuring the project with dedicated folders for controllers, routes, middleware, and utils.

* Using a .env file to manage environment-specific settings like the server port.

### 2. API Design

Endpoints were designed for the following key resources:

* Users – manage profile data.

* Posts – create and manage user posts.

* Comments – allow commenting on posts.

* Likes – support liking posts.

* Followers – handle user follow/unfollow relationships.

Each resource was equipped with standard RESTful endpoints such as:

* GET /users – Retrieve a list of users.

* POST /users – Add a new user.

* PUT /users/{id} – Modify a user’s details.

* DELETE /users/{id} – Remove a user.

### 3. API Development
Using Express, I developed the logic for each feature:

* Controllers handled the business logic for each resource.

* Routes connected HTTP methods with controller functions.

* Middleware was added for custom error handling, request logging, and content negotiation.

* Mock Data was created in utils/mockData.js to simulate backend storage, as no database was used in this project.

### 4. Advanced Features

* Pagination: Implemented using page and limit query parameters for list endpoints.

* Error Handling: Developed a middleware function to manage and respond to errors consistently.

* Content Negotiation: Implemented logic to return either JSON or XML responses depending on the client's Accept header.

### 5. API Documentation
To ensure usability, I created a basic HTML documentation file (public/docs.html) outlining all available endpoints, including sample requests and responses.