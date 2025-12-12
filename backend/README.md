# Ticket Booking System 
Ticket Booking System – Backend Service

This backend service provides all core functionalities for the Ticket Booking System, including show management, seat availability, booking creation, and booking lifecycle handling. It is designed for reliability, concurrency safety, and cloud deployment readiness.

1. Overview

The backend is responsible for managing all business logic and data operations associated with the ticket booking flow. It exposes a RESTful API that allows clients to fetch shows, check seat availability, create bookings, and track booking status.

A central design focus is ensuring concurrency-safe behavior during high-demand seat booking, preventing double booking through the use of database-level transactions and row-level locking.

2. Technology Stack

Node.js

Express.js

PostgreSQL

Cloud Deployment: Render

Database Concurrency: Transactions and row-level locks

API Architecture: REST

3. Folder Structure
backend/
├── controllers/      # Business logic
├── routes/           # API endpoints
├── models/           # Database queries
├── index.js          # Application entry point
├── package.json
└── README.md

4. Features
Show and Trip Management

Create and retrieve shows or trips.

Store seat layout information.

Seat Availability Management

Retrieve available seats.

Maintain real-time updates on booked or unavailable seats.

Booking Management

Create bookings with complete lifecycle support.

Prevent double booking through strict concurrency control.

Assign booking statuses such as Pending, Confirmed, or Failed.

Reliability Enhancements

Centralized error handling.

Input validation.

Logging for monitoring and debugging.

5. Environment Variables

The backend requires the following environment variables to be configured:

Variable	Description
DATABASE_URL	Connection string to PostgreSQL database
PORT	Application port (Render assigns automatically)
NODE_ENV	Runtime environment mode

These are configured in Render’s environment settings during deployment.

6. Deployment

The backend is deployed as a Web Service on Render.

Deployment steps include:

Connecting the GitHub repository to Render.

Configuring environment variables securely in Render’s dashboard.

Allowing Render to automatically install dependencies and start the server.

Connecting the backend to a managed PostgreSQL instance.

Render provides a public URL that serves as the base for all API requests.

7. API Summary

The following endpoints represent the primary interactions:

Method	Endpoint	Description
GET	/api/shows	Retrieve all shows
POST	/api/shows	Create a new show
GET	/api/shows/:id/seats	Retrieve seat layout
POST	/api/bookings	Create a booking
GET	/api/bookings/:id	Retrieve booking status

A detailed Postman collection is included in the repository.

8. Concurrency Handling

To prevent multiple users from booking the same seat simultaneously, the backend uses:

Database transactions

Row-level locking

Atomic validation of seat availability

Only one booking operation succeeds when simultaneous requests are made for the same seat. Others are gracefully rejected and marked as Failed. This mirrors real-world booking systems such as movie or bus ticket applications.

9. Local Development Instructions

Navigate to the backend folder.

Install dependencies using Node Package Manager.

Configure environment variables locally.

Start the development server.

The backend runs independently and can be tested using tools such as Postman or curl.

10. License

This backend is provided under the MIT License.
