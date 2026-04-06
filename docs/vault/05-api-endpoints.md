# API Endpoints

## Authentication
- **POST /api/auth/login**  
  - Description: Log in a user  
  - Request Body: { username: String, password: String }  
  - Response: { token: String }

- **POST /api/auth/register**  
  - Description: Register a new user  
  - Request Body: { username: String, password: String, email: String }  
  - Response: { success: Boolean }

## Properties
- **GET /api/properties**  
  - Description: Get a list of properties  
  - Query Params: { location: String, check_in: Date, check_out: Date, guests: Integer }
  - Response: [{ id: String, name: String, price: Number }]

- **GET /api/properties/{id}**  
  - Description: Get details of a specific property  
  - Response: { id: String, name: String, description: String, price: Number, amenities: [String] }

## Bookings
- **POST /api/bookings**  
  - Description: Create a new booking  
  - Request Body: { propertyId: String, check_in: Date, check_out: Date, guests: Integer }
  - Response: { bookingId: String, success: Boolean }

- **GET /api/bookings/{id}**  
  - Description: Get a specific booking  
  - Response: { id: String, propertyId: String, userId: String, check_in: Date, check_out: Date }

## Calendar
- **GET /api/calendar/{propertyId}**  
  - Description: Get availability calendar for a property  
  - Response: [{ date: String, available: Boolean }]

## Pricing
- **GET /api/pricing/{propertyId}**  
  - Description: Get pricing details for a property  
  - Response: { propertyId: String, standardRate: Number, peakRate: Number }

## Activities
- **GET /api/activities**  
  - Description: Get a list of activities available  
  - Response: [{ id: String, name: String, description: String }]

- **POST /api/activities**  
  - Description: Create a new activity  
  - Request Body: { name: String, description: String }
  - Response: { activityId: String, success: Boolean }

## Reviews
- **GET /api/reviews/{propertyId}**  
  - Description: Get reviews for a property  
  - Response: [{ reviewer: String, rating: Number, comment: String }]

- **POST /api/reviews/{propertyId}**  
  - Description: Submit a review for a property  
  - Request Body: { rating: Number, comment: String }
  - Response: { success: Boolean }

---

Generated on: 2026-04-06 20:26:44 UTC