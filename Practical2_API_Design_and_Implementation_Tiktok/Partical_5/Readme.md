#  Practical 5: Migrating to Cloud Storage with Supabase – Reflection

In this practical, I focused on enhancing the TikTok clone application by transitioning media storage from local file systems to **Supabase Storage**, a scalable and secure cloud storage solution. This shift supports better content delivery, removes scalability constraints, and aligns with best practices for modern web development.

## Key Learning Outcomes

### Why Cloud Storage Matters
Prior to using Supabase, the application stored user-uploaded content like videos and thumbnails locally. I quickly learned the drawbacks of this approach, which included:
* Limited disk capacity
* No redundancy or backups
* Lack of accessibility in distributed environments
* Risk of data loss during server crashes or redeployments

Cloud storage eliminates these limitations by offering durability, CDN-based performance, and fine-grained access controls.

###  Supabase Storage Integration Process

####  Backend Configuration
* Created a **Supabase project** and set up two storage buckets: `videos` and `thumbnails`.
* Used environment variables to manage sensitive credentials.
* Integrated Supabase SDK into the backend using `@supabase/supabase-js`.
* Refactored backend logic to:
   * Upload files directly to Supabase
   * Store URLs and metadata in the PostgreSQL database via Prisma
   * Replace local storage paths with public URLs from Supabase

####  Frontend Refactor
* Set up Supabase client in the frontend using public keys.
* Implemented an upload component allowing direct browser-to-cloud uploads.
* Updated video display logic to pull media files from Supabase URLs instead of the local server.

### Access Management and Policies
Configuring **storage policies** was critical to ensure secure but functional access:
* **Authenticated Uploads:** Only signed-in users can upload media.
* **Public Viewing:** Video and thumbnail assets can be publicly accessed without exposing sensitive operations.

Understanding how Supabase's Row-Level Security (RLS) and policies work gave me insights into secure file handling in production-grade systems.

###  Testing and Migration

####  Verification Steps
* Uploaded test videos and verified direct delivery from Supabase CDN.
* Confirmed real-time playback performance improvements.
* Ensured thumbnails were correctly generated and referenced.
* Ran a migration script to move existing media to Supabase.

#### Final Outcome
The migration was successful, and the application is now more resilient, scalable, and efficient in serving user-generated media content.

##  What I Learned
* **Cloud storage is essential** for any modern web app dealing with large or user-generated media.
* **Supabase makes it easier** to implement such a system without heavy DevOps work.
* **Frontend-backend coordination** is crucial when transitioning from local to remote file handling.
* **Access control and CDN performance** are equally important as storage capacity when choosing a cloud provider.

##  Conclusion
This practical was a significant step in moving the TikTok clone closer to a production-ready architecture. By offloading file management to Supabase Storage, I learned to build a more maintainable and scalable system, which reflects industry standards and prepares me for real-world development challenges.