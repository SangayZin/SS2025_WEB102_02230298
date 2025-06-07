# 🧠 Reflection Report – Practical 4 Connecting TikTok to PostgreSQL using Prisma ORM

##  Overview
This practical involved transitioning a TikTok clone application from using in-memory data structures to a fully integrated PostgreSQL database, managed via Prisma ORM. The objective was to establish a persistent data layer, implement secure user authentication, and refactor the API logic to interact with the database reliably and efficiently.

##  What I Learned

### 1. Database Setup and Connectivity
I learned how to properly configure a PostgreSQL database from scratch, create a user with appropriate privileges, and connect it to a Node.js application using Prisma. The process deepened my understanding of database authentication, connection strings, and environment variable management.

### 2. Schema Modeling with Prisma
Using the Prisma schema language allowed me to define models that mirror real-world relationships like users, videos, comments, likes, and followers. I gained confidence in handling one-to-many and many-to-many relationships and learned how Prisma handles these internally using join tables.

### 3. Migration and Seeding Workflow
I became familiar with Prisma's migration system. I now understand how to create migrations to version-control schema changes and use seeding scripts to populate the database with realistic sample data for testing and development.

### 4. Authentication Implementation
This task introduced me to handling user authentication securely. I implemented password hashing using bcrypt, and JWT-based authentication for stateless session management. Middleware was set up to protect sensitive API routes, a concept I found very applicable for real-world applications.

### 5. Database-Driven API Refactoring
One of the key tasks was to refactor the existing API logic to fetch and persist data using Prisma. This required learning how to write and optimize database queries and use transactions where multiple tables were involved. It also pushed me to write cleaner and more robust error handling.

##  Challenges and How I Overcame Them

###  Database Connection Errors
Initially, I faced issues connecting to the PostgreSQL server due to incorrect credentials in the .env file. After reviewing the PostgreSQL logs and verifying permissions for the user, I corrected the database URL and restarted the PostgreSQL service, which resolved the issue.

###  Modeling Many-to-Many Relationships
Understanding how to model many-to-many relationships (e.g., user likes, follows) was not intuitive at first. After reviewing the Prisma documentation and examples, I learned to use explicit relation tables and configure the schema correctly with @relation directives.

###  Token Validation and Middleware Debugging
Integrating JWT authentication presented challenges such as expired token handling and inconsistent header formats. I implemented detailed error responses and updated the middleware logic to ensure reliable route protection and better debugging during testing.

###  Data Seeding Complexity
Writing the seed script involved generating dependent data (e.g., comments tied to videos, likes tied to users), which required a sequential and structured approach. I used loops and conditional logic to maintain relational integrity, and it significantly improved my understanding of foreign keys in practice.

##  Personal Takeaways
Working with ORM tools like Prisma not only reduced boilerplate code but also encouraged me to think more carefully about data modeling and its implications on performance.

Authentication is more than just login/logout — it involves securely storing passwords, managing tokens, and ensuring only authorized users can access protected resources.

Migrating from in-memory to persistent storage is a vital step in moving an application from prototype to production-ready.

##  Conclusion
This practical helped me bridge backend development concepts with real-world database management and security practices. The experience of integrating PostgreSQL with Prisma has given me a clearer view of scalable backend design and the discipline required to maintain data integrity and security throughout the development process.