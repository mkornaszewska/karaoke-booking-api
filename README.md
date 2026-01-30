# 🎤 Karaoke Booking API

A mock REST API for a Japanese karaoke room booking system, perfect for learning API testing with Playwright and TypeScript.

## 📋 Description

This is a test database for practicing API automation and E2E testing. It simulates a karaoke booking platform inspired by popular Japanese karaoke chains like Karaoke Kan, featuring rooms, bookings, users, songs, and menu items.

## 🚀 Getting Started

### Using with my-json-server (No Installation Required)

Access the API directly via my-json-server:

```
https://my-json-server.typicode.com/mkornaszewska/karaoke-booking-api
```

### Running Locally with JSON Server

1. Install JSON Server:
```bash
npm install -g json-server
```

2. Clone this repository:
```bash
git clone https://github.com/mkornaszewska/karaoke-booking-api.git
cd karaoke-booking-api
```

3. Start the server:
```bash
json-server --watch db.json --port 3000
```

The API will be available at `http://localhost:3000`

## 📚 API Endpoints

### Rooms
- `GET /rooms` - Get all karaoke rooms
- `GET /rooms/:id` - Get a specific room
- `GET /rooms/:id/reviews` - Get reviews for a specific room
- `POST /rooms` - Create a new room
- `PUT /rooms/:id` - Update a room
- `PATCH /rooms/:id` - Partially update a room
- `DELETE /rooms/:id` - Delete a room

### Bookings
- `GET /bookings` - Get all bookings
- `GET /bookings/:id` - Get a specific booking
- `POST /bookings` - Create a new booking
- `PUT /bookings/:id` - Update a booking
- `DELETE /bookings/:id` - Cancel a booking

### Users
- `GET /users` - Get all users
- `GET /users/:id` - Get a specific user
- `POST /users` - Create a new user
- `PUT /users/:id` - Update user info

### Songs
- `GET /songs` - Get all available songs
- `GET /songs/:id` - Get a specific song
- `POST /songs` - Add a new song

### Menu Items
- `GET /menu_items` - Get all food & drink items
- `GET /menu_items/:id` - Get a specific menu item

## 🔍 Query Examples

### Filter rooms by size
```
GET /rooms?size=medium
```

### Filter bookings by status
```
GET /bookings?status=confirmed
```

### Filter songs by difficulty
```
GET /songs?difficulty=expert
```

### Get rooms with rating above 4.5
```
GET /rooms?average_rating_gte=4.5
```

### Sort songs by popularity
```
GET /songs?_sort=times_sung&_order=desc
```

### Pagination
```
GET /rooms?_page=1&_limit=2
```

### Full-text search
```
GET /songs?q=Queen
```

### Expand nested reviews
```
GET /rooms?_embed=reviews
```

## 📊 Database Structure (db.json)

The `db.json` file contains all the mock data for this API. It includes 5 collections:

### Rooms (3 items)
```json
{
  "id": 1,
  "name": "Shibuya Small",
  "size": "small",
  "capacity": 4,
  "hourly_rate": 1500,
  "weekend_rate": 1800,
  "amenities": ["m2", "tmb", "bl"],
  "has_window": false,
  "is_available": true,
  "average_rating": 4.2,
  "reviews": [...]
}
```
**Sizes:** small, medium, vip  
**Themes:** modern, retro, luxury  
**Note:** Reviews are nested within each room

### Bookings (3 items)
```json
{
  "id": 1,
  "user_id": 1,
  "room_id": 2,
  "date": "2026-02-01",
  "start_time": "18:00",
  "duration_hours": 2,
  "party_size": 6,
  "total_price": 5000,
  "status": "confirmed"
}
```
**Statuses:** pending, confirmed, completed

### Users (3 items)
```json
{
  "id": 1,
  "username": "karaoke_lover",
  "email": "karaoke@example.com",
  "total_bookings": 12,
  "loyalty_points": 350,
  "is_active": true
}
```
Loyalty points, preferences, and booking history

### Songs (5 items)
```json
{
  "id": 5,
  "title": "Kurenai",
  "artist": "X Japan",
  "genre": "Visual Kei Rock",
  "difficulty": "expert",
  "times_sung": 3156,
  "average_rating": 4.9,
  "is_available": true
}
```
Japanese and English songs

### Menu Items (3 items)
```json
{
  "id": 3,
  "name": "Karaage Plate",
  "category": "food",
  "price": 800,
  "description": "Fried chicken",
  "available": true
}
```
Food and beverage packages

### Data Types Included
- **Integers**: IDs, prices, counts, duration
- **Floats**: Ratings (4.7, 4.9)
- **Booleans**: is_available, would_recommend, is_active
- **Strings**: Names, emails, status enums
- **Arrays**: Amenities (shortened codes like "m2", "db", "nl")
- **Timestamps**: ISO 8601 format (2026-01-25T10:30:00Z)
- **Nested Objects**: Reviews nested within rooms
- **Nulls**: Optional fields

### Amenity Codes
- **m2/m4**: microphones_2, microphones_4
- **tmb**: tambourine
- **mb**: maracas
- **db**: disco_ball
- **nl**: neon_lights
- **bl**: basic_lighting
- **ps**: premium_sound
- **lc**: leather_couches
- **mb**: mini_bar

## 🎌 Japanese Connection

This project was inspired by a year studying in Japan and experiencing the amazing karaoke culture. Features include:
- Authentic Japanese karaoke room themes
- Popular J-Pop and City Pop songs
- Classic Japanese snacks (karaage)
- Room names based on Tokyo neighborhoods (Shibuya, Harajuku, Roppongi)
