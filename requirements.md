# Backend Feature Requirement Specifications

This document outlines the technical and functional requirements for some of the most important backend features in the Airbnb Clone project.
## 1. User Authentication

**API Endpoints:**
- `POST /api/register`  
  Registers a new user.
- `POST /api/login`  
  Authenticates a user and returns a JWT token.

- `PUT /api/user`
    Edits User Information

**Input:**
- Registration: `first_name`, `last_name`, `email`, `password,`, `phone number`, `role`
- Login: `email`, `password`

**Output:**
- Registration: Success message or error
- Login: JWT token, user profile, or error

**Validation Rules:**
- Email must be unique and valid format
- Password must be at least 8 characters, hashed
- All fields required

**Performance Criteria:**
- Registration and login should respond within 1 second

---

## 2. Property Management

**API Endpoints:**
- `POST /api/properties`  
  Create a new property listing
- `PUT /api/properties/{id}`  
  Update an existing property
- `DELETE /api/properties/{id}`  
  Delete a property

**Input:**
- `name`, `description`, `location`, `price_per_night`, `images`, `host_id`

**Output:**
- Property object or error message

**Validation Rules:**
- All fields required except images (optional)
- Price must be a positive number
- Only the host who created the property can edit or delete it

**Performance Criteria:**
- CRUD operations should complete within 2 seconds

---

## 3. Booking System

**API Endpoints:**
- `POST /api/bookings`  
  Create a new booking
- `GET /api/bookings/{user_id}`  
  Get all bookings for a user
- `DELETE /api/bookings/{id}`  
  Cancel a booking

**Input:**
- `property_id`, `user_id`, `start_date`, `end_date`, `total_price`

**Output:**
- Booking confirmation, booking object, or error message

**Validation Rules:**
- Dates must be valid and not overlap with existing bookings
- User must be authenticated
- Total price must match property price and number of nights

**Performance Criteria:**
- Booking creation and cancellation should respond within 2 seconds

## 4. Payment Integration
- `POST /api/payments`
    Make a payment for a booking
- `GET /api/payments/{user_id}`
    Get all payments for a user

**Input**
- `booking_id  `, `amount`, `payment_method` (credit_card, paypal, stripe)

**Output**
- Payment confirmation, payment object or error message

**Validation Rules:**
- Amount must match booking total
- Payment method must be supported
- Booking must exist and belong to user

**Performanc Criteria**
- payment processinf should respond within 3 seconds

---
## 5. Notification System

**API Endpoints:**
- `POST /api/notifications`
    Send a notification to a user
- `GET /api/notifications/{user_id}`
    Get all notifications for a user

**Input:**
- `user_id`,`type` (booking, payment, cancellation), `message`
**Output:**
    - Notification object or error message

**Validation Rules:**
    - User must exist
    - Type Must be valid
**Performance Criteria:**
- Notification should be sent within 1 second

---

## 6. Messaging System

**API Endpoints:**
- `POST /api/messages`
Send a message from one user to another
- `GET /api/messages/{user_id}`
 Get all messages from a user


**Input:**
- `sender_id`, `recipient_id`, `message_body`

**Output**
- Message object or error message

**Validation Rules:**
- Both users must exist
- Message body cannot be empty

**Performance Criteria**
- Message should be delivered within 1 second

---

## 7. Review/Feedback System

**API Endpoints:**
-  `POST /api/reviews`
Add a review for a property
- `GET /api/reviews/{property_id}`
Get all reviews for a property

**Input:**
- `property_id`, `user_id`, `rating`, `comment`

**Output:**
- Review object or error message

**Validation rules:**
- Rating must be between 1 and 5
- COmment cannot be empty
- User must have booked the property

**Performance Criteria:**
- Review should be saved within 1 second

---

## 8. Admin Dashboard

**API Endpionts:**
- `GET /api/admin/users`
    List all users
- `GET /api/admin/properties`
List all properties
- `GET /api/admin/bookings`
    List all bookings
- `GET /api/admin/payments`
    List all payments
- `PUT /api/admin/users/{id}`
    Edit user details


**Input:**
- Dependes on the action (user, property, booking, payment data)

**Output:**
- List of objects or confirmation message

**Validation Rules:**
- Only admin users can access these endpoints

**Performance criteria:**
- Admin actions should respond within 2 seconds

---