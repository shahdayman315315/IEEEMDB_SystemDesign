Critical Components Analysis:

User Service & Authentication:

SQL database for structured data

JWT tokens for auth

Rate limiting to prevent abuse

Movie Service & Search:

NoSQL DB for fast retrieval

Text indexing for search by title, genre, cast

Cache popular searches

Review Service:

NoSQL for high-write volume

Batch writes to avoid DB overload

Async update to Recommendation Service

Recommendation Service:

Treat as black box: input = user data & watch history → output = movie list

Precompute recommendations for active users in cache

Notification Service:

Queue system for push notifications

Retry mechanism on failure

Scalability:

Horizontal scaling: multiple instances of each service

Load balancing for high traffic

Sharding for large tables (Movies, Reviews)

Trade-offs:

SQL for consistency (Users, Follows)
