# Skill Enhancement API Project

A RESTful API for managing skill enhancement courses built with Node.js and Express.js. This API provides comprehensive CRUD operations for course management with filtering, sorting, and pagination capabilities.

## Features

- **Full CRUD Operations**: Create, Read, Update, and Delete courses
- **Advanced Filtering**: Filter by category, publication status, and price range
- **Search Functionality**: Search courses by title or instructor name
- **Sorting**: Sort courses by title, fee, or duration
- **Pagination**: Built-in pagination for efficient data retrieval
- **Input Validation**: Comprehensive validation for all course fields
- **Unique Constraints**: Course titles must be unique
- **Error Handling**: Proper HTTP status codes and error messages

## Prerequisites

- Node.js (v14 or higher)
- npm or yarn package manager

## Installation & Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/Suji2007hub/skill-enhancement-backend-project.git
   cd skill-enhancement-backend-project
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the server**
   ```bash
   npm start
   ```
   Or directly:
   ```bash
   node index.js
   ```

4. **Access the API**
   The server will start on `http://localhost:8080` by default. You can modify the port by setting the `PORT` environment variable.

## API Endpoints

### Base URL
All endpoints are prefixed with `/api`

### Create a Course
```http
POST /api/courses
```

**Request Body:**
```json
{
  "title": "Introduction to Python",
  "instructor": "John Doe",
  "category": "programming",
  "fee": 299.99,
  "durationHours": 40,
  "published": true
}
```

**Valid Categories:**
- `programming`
- `design`
- `business`
- `data-science`
- `personal-development`

### Get All Courses (with filtering, sorting, and pagination)
```http
GET /api/courses
```

**Query Parameters:**
- `page` (default: 1) - Page number for pagination
- `limit` (default: 10, max: 50) - Number of items per page
- `category` - Filter by category
- `published` - Filter by publication status (true/false)
- `minFee` - Minimum course fee
- `maxFee` - Maximum course fee
- `sort` - Sort by field (title, fee, durationHours)
- `order` - Sort order (asc/desc)
- `search` - Search in title and instructor fields

### Get a Single Course
```http
GET /api/courses/:id
```

### Update a Course (Full Update)
```http
PUT /api/courses/:id
```
Requires all mandatory fields in the request body.

### Update a Course (Partial Update)
```http
PATCH /api/courses/:id
```
Only include the fields you want to update.

### Delete a Course
```http
DELETE /api/courses/:id
```

## Field Validations

| Field | Requirements |
|-------|--------------|
| title | String, 3-100 characters, unique |
| instructor | String, 2-50 characters |
| category | Must be one of the predefined categories |
| fee | Number, greater than 0, maximum 10000 |
| durationHours | Integer, 1-500 hours |
| published | Boolean (true/false) |

## Response Formats

### Success Response (GET /api/courses)
```json
{
  "data": [
    {
      "id": 1,
      "title": "Introduction to Python",
      "instructor": "John Doe",
      "category": "programming",
      "fee": 299.99,
      "durationHours": 40,
      "published": true
    }
  ],
  "page": 1,
  "limit": 10,
  "total": 1,
  "totalPages": 1
}
```

### Error Response
```json
{
  "error": "Error message description"
}
```

## HTTP Status Codes

- `200` - Success
- `201` - Resource created successfully
- `204` - Resource deleted successfully
- `400` - Bad request / validation error
- `404` - Resource not found
- `500` - Internal server error

## Project Structure

```
skill-enhancement-api-project/
├── server.js          # Main application logic
├── index.js           # Application entry point
├── package.json       # Project dependencies and scripts
├── package-lock.json  # Dependency lock file
└── README.md          # Project documentation
```

## Dependencies

- **express**: ^5.3.0 - Web application framework

## Scripts

- `npm start` - Start the server
- `npm test` - Run tests (currently configured for basic test output)

## License

This project is licensed under the ISC License.