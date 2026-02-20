# Property Booking API

## Overview

A **RESTful Property Listing and Booking API** built with **ASP.NET Core**, designed to manage room listings, bookings, and cancellations for properties near universities.

The project integrates **external services** for distance calculation and weather data and is **deployed on an Azure Linux Virtual Machine**, demonstrating real-world backend development and cloud deployment practices.

---

## Key Features

- **Room Listings**
  - Retrieve detailed property information including location, price, associated university, and distance

- **Booking & Cancellation**
  - Book and cancel rooms using unique room identifiers
  - Track booked and canceled rooms via dedicated endpoints

- **Distance Calculation**
  - Integrates with the **OSRM API** to calculate distances between properties and universities using GPS coordinates

- **Weather Integration**
  - Fetches real-time weather data for property locations via an external weather service

- **Cloud Deployment**
  - Deployed on an **Azure Linux VM**, exposing the API publicly via a static IP

---

## Architecture & Design

- **Framework:** ASP.NET Core 6.0 (C#)
- **API Style:** RESTful architecture with clear resource-based endpoints
- **Data Format:** JSON serialization for client compatibility
- **Data Modeling:** Custom `Room` struct for structured data representation

The API is designed to be modular, extensible, and suitable for integration with web or mobile frontends.

---

## External Integrations

### Distance Calculation (OSRM API)

Calculates the distance between a property and its associated university based on GPS coordinates.

**Example endpoint:**
GET /api/Room/distance/{roomID}


---

### Weather Information

Retrieves real-time weather data for the geographic location of a room.

**Example endpoint:**
GET /api/Room/weather/{roomID}


---

## API Endpoints

### Room Management

- GET /api/Room
  - Returns all available rooms with location, university, price, and distance data.

- GET /api/Room/bookedRooms
  - Returns all booked rooms.

- GET /api/Room/canceledRooms
  - Returns all canceled room bookings.

---

### Booking & Cancellation

- POST /api/Room/book/{roomID}
  - Books a room using its unique ID.

- POST /api/Room/cancel/{roomID}
  - Cancels a booking for the specified room.

---

### Calculations & Information

- GET /api/Room/distance/{roomID}
  - Calculates the distance between a room and its university.

- GET /api/Room/weather/{roomID}
  - Fetches weather data for the room’s location.

---

## Deployment

The API is deployed on an **Azure Linux Virtual Machine**.

Deployment steps included:
- Installing the required **.NET runtime**
- Publishing the application locally
- Transferring files to the VM using **SCP**
- Binding the API to `0.0.0.0` for public accessibility
- Verifying endpoint availability from external clients

---

## Challenges & Solutions

### External API Reliability
Integrating OSRM and weather services required careful handling of API responses, timeouts, and error states to ensure stability.

### Cloud Deployment
Deploying to a Linux VM required configuring networking, runtime dependencies, and public access while maintaining application reliability.

---

## Skills Demonstrated

- RESTful API design and implementation
- ASP.NET Core backend development
- External API integration
- Cloud deployment on Azure (Linux VM)
- JSON serialization and structured data modeling
- Real-world problem solving and system design

---

## Future Improvements

- Add authentication and authorization
- Introduce filtering and sorting (price, distance, city)
- Add persistence with a database (e.g. PostgreSQL or SQL Server)
- Perform load testing using tools like Azure Load Testing or JMeter
