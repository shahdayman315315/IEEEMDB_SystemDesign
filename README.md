# IEEEMDB_SystemDesign
IEEEMDB - Movie Discovery & Social Platform

#Overview:
IEEEMDB is an online platform that helps users discover movies, track their watch history, and share reviews with friends. It combines a personal movie diary with social features, enabling users to create collections, rate movies, and interact with other movie lovers.

This repository includes both the System Design and an Implementation demo.

Functional & Non-Functional Requirements

Refer to the system design diagrams in the /excalidraw folder for full details. هنا لينك الايكسل 

#Functional Requirements:

User management (signup, login, profile)

Movie management (add, update, store information)

Reviews & ratings

Collections (personal movie lists)

Search & discovery

Recommendations (black box)

Notifications for users

Non-Functional Requirements

Scalability to handle millions of users and movies

Availability (system operational 24/7)

Performance (fast search, recommendations, and retrieval)

Security (authentication and authorization for users and admins)

Consistency (reliable data access; eventual consistency acceptable for feeds)

#Data Model

Entities and relationships are described in the Excalidraw diagram in /excalidraw.

Entities:

User: user_id, name, email, profile_details

Movie: movie_id, title, description, trailer_url, cast[], tags[], release_date

Review: review_id, user_id, movie_id, rating, comment

Collection: collection_id, user_id, name, movie_ids[]

Follow: follower_id, followee_id

Relationships:

User ↔️ Review (1:N)

User ↔️ Collection (1:N)

Collection ↔️ Movie (M:N)

User ↔️ Follow (M:N)

#API Design

Core API endpoints are documented in the /excalidraw folder. Examples include:

POST /users/signup → Create user

POST /users/login → Authenticate user

GET /movies/search?query= → Search movies

POST /reviews → Add review

POST /collections → Create collection

GET /users/{id}/recommendations → Suggested movies

#High-Level Architecture

System components and interactions are illustrated in /excalidraw:

Clients: Web and mobile interfaces

API Gateway / Load Balancer

Services: User, Movie, Review, Collection, Recommendation, Notification, Admin

Databases: SQL (structured data), NoSQL (high-volume data)

Cache: Redis for frequently accessed data

Message Queue: Kafka/RabbitMQ for async tasks

Storage/CDN: Media files (trailers, images)

Flow example:

User searches a movie → API Gateway → Movie Service → DB/Cache → Response

User posts a review → Review Service → DB → Updates Recommendation Service → Triggers Notifications

#Deep Dives

Critical component details, trade-offs, and scaling strategies are included in   لينك deep_dive.md:

Database choices and partitioning

Caching strategy

Asynchronous updates & queues

Recommendations & notifications

Performance optimization & trade-offs

#Implementation

Core demo code is in the implementation/ folder.

Models/ → Data structures

Services/ → Business logic

Program.cs → Entry point

The demo includes:

User creation & profile management

Adding movies

Posting reviews & ratings

Creating collections and adding movies

The code is organized, clean, and follows good practices. You can extend it with additional features if needed.

#include Back-Of-The-Envelope Estimation (Optional)

Expected daily active users: 100,000

Async processing for notifications and feeds
