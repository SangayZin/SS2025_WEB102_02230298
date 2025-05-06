# Reflection on Practical 2: TikTok API Development

## Lessons Learned

This practical allowed me to dive deep into RESTful API development and gave me hands-on experience with real-world scenarios. Here’s what I took away from the process:

- **Understanding REST Principles**: I developed a stronger grasp of RESTful architecture, particularly in organizing endpoints and applying HTTP methods (GET, POST, PUT, DELETE) correctly.

- **Middleware for Error Handling** : I learned how middleware functions can be leveraged to manage errors globally, leading to consistent and helpful error messages across the application.

- **Handling Resource Relationships** : Creating features like “likes” and “followers” introduced me to handling many-to-many relationships and simulating real-world data interactions.

- **API Testing Techniques** : Using tools like curl to test my endpoints helped me validate responses, troubleshoot issues, and ensure the API behaved as intended.

## Obstacles Encountered

### 1. Resource Relationship Complexity

Building connections like likes and follows added complexity, as I had to maintain consistent state between different data objects.

- **How I Resolved It** : I maintained these relationships using arrays within mock objects and implemented functions to manage additions and removals cleanly.

### 2. Handling Errors Gracefully

At first, providing clear and informative feedback for different error scenarios was challenging.

- **What I Did** : I set up centralized error-handling middleware that captured thrown errors and returned user-friendly responses with appropriate status codes.

### 3. Request Data Validation

It was crucial to ensure incoming requests contained all necessary information, especially for creating or updating resources.

- **Approach Taken** : I implemented simple checks inside controllers to validate incoming data and reject incomplete or malformed requests.

## Highlights and Enjoyable Moments

- Real-World Simulation: Designing an API for a TikTok-style platform was enjoyable because it felt practical and applicable. It was exciting to map out how a social app functions behind the scenes.

- Solving Logical Problems: Debugging issues and solving challenges related to logic and data flow was both engaging and satisfying.

- Command-Line Testing: Using curl to interact directly with my API made testing more dynamic and gave me confidence in the implementation.