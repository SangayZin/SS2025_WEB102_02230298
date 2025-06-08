# Practical 6: Token-Based Authentication (Email & Password) – Reflection 

##  Summary of Key Concepts

### 1. Authentication vs Authorization
Authentication is the process of verifying who a user is (email/password), while authorization defines what an authenticated user can access.

- **Authentication**: Like presenting your ID at a secure checkpoint 
- **Authorization**: Like using a keycard to access a specific room 

### 2. Password Protection via Hashing
Storing plain text passwords is a critical vulnerability. Instead, we apply hashing:

- Bcrypt is used for its one-way encryption capability.
- Salt rounds increase resistance to brute-force attacks.
- Passwords are verified by comparing hashes, not by reversing them.

### 3. Using JWT for Stateless Authentication
JSON Web Tokens (JWT) provide secure, stateless authentication:

- **Format**: Header.Payload.Signature
- Payload includes user ID and expiration
- Signed with a secret key to ensure integrity

### 4. Middleware for Route Protection
Authentication logic is abstracted into middleware to:

- Verify JWTs before reaching protected routes
- Maintain clean separation of responsibilities
- Reuse token verification logic across multiple endpoints

### 5. Relational Database Modeling
Using Prisma, we established a 1:N relationship:

- One user → multiple accounts
- Enforced using foreign key constraints
- Prisma ORM ensures type safety and clean schema relationships

##  What I Learned

###  Security Best Practices
I gained a better understanding of why storing passwords securely matters:

- Bcrypt with salting ensures strong, one-way encryption.
- Proper error messages avoid leaking account info.
- Storing only hashed versions is essential to avoid data breaches.

###  Authentication Lifecycle
I understood the full authentication flow, from registration to authorization:

- **Register** → Hash password + store user + create account
- **Login** → Validate credentials + issue JWT
- **Access** → Verify JWT + extract identity + grant access

This approach ensures both usability and protection.

###  Middleware Design
Middleware helped implement token-based protection cleanly:

- Authentication was decoupled from the core business logic.
- It allowed token checks before protected endpoints were reached.
- This led to a more maintainable codebase.

###  Database Design Takeaways
Relational principles helped ensure data integrity:

- Foreign keys helped enforce user-account relationships.
- Normalized structure reduced redundancy.
- Prisma's select optimization improved query performance.

## Challenges & Solutions

### 1. Understanding JWT Structure
**Problem**: Unsure what data to include in the token payload.

**Solution**:
Researched JWT practices and learned that tokens are only encoded, not encrypted. Now I know to:

- Include only essential, non-sensitive data.
- Never place passwords or private info in the payload.

### 2. Handling Authentication Errors
**Problem**: Overly specific error messages could reveal valid emails.

**Solution**:
Implemented generic error responses and standardized timing to avoid giving attackers clues.

### 3. TypeScript and Middleware
**Problem**: Difficulty accessing JWT data from the request context.

**Solution**:
Imported correct type definitions and extended the Hono context appropriately. This reinforced the importance of strong typing in complex flows.

### 4. Evolving Database Schema
**Problem**: Added a new hashPassword field after initial setup.

**Solution**:
Used `bunx prisma db push` to migrate and `bunx prisma generate` to sync types. I learned to carefully plan changes in real-world databases.

##  Insights & Takeaways

### 1. Security Requires Layers
Authentication isn't just about checking credentials. It's a layered process involving:

- Input validation
- Rate limiting
- Secure transport (HTTPS)
- Defensive error handling

### 2. Usability Matters
Good security shouldn't harm user experience. Things like:

- Friendly but secure error feedback
- Reasonable token lifespans
- Robust TypeScript support for safer development

...all contribute to a smoother developer and user journey.

### 3. Stateless Authentication is Powerful
Using JWTs for authentication brings advantages:

- Easier horizontal scaling (no session state)
- Compatibility with mobile apps and microservices
- Simpler infrastructure needs

### 4. Follow Best Practices
Stick with proven standards like:

- JWT RFC 7519
- bcrypt (not MD5 or SHA1)
- Proper use of HTTP status codes for error clarity

##  Future Improvements
Here are areas I'd like to expand on next:

- **Refresh Tokens**: Extend session life securely
- **Rate Limiting**: Defend against abuse and brute force
- **Email Verification**: Confirm user identity before activating accounts