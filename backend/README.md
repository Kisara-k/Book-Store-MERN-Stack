# Backend - Book Store API

A robust REST API for the Book Store application built with Node.js, Express.js, and MongoDB. This backend service provides all the necessary endpoints for managing books in the store.

## Technology Stack

- **Node.js** - JavaScript runtime environment
- **Express.js** - Fast, unopinionated web framework
- **MongoDB** - NoSQL document database
- **Mongoose** - MongoDB object modeling for Node.js
- **CORS** - Cross-Origin Resource Sharing middleware
- **Nodemon** - Development tool for auto-restarting

## Project Structure

```
backend/
├── config.js           # Database and server configuration
├── index.js            # Main server file with middleware setup
├── package.json        # Dependencies and scripts
├── models/             # Database schemas and models
│   └── bookModel.js    # Book model with Mongoose schema
└── routes/             # API route definitions
    └── booksRoute.js   # Book-related CRUD operations
```

## Getting Started

### Prerequisites

- Node.js (version 14 or higher)
- MongoDB (local installation or MongoDB Atlas)
- npm or yarn package manager

### Installation

1. **Navigate to the backend directory:**

   ```bash
   cd backend
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Configure the database:**
   Create a `config.js` file:

   ```javascript
   export const PORT = 5555;
   export const mongoDBURL = "mongodb://localhost:27017/bookstore";

   // For MongoDB Atlas (cloud):
   // export const mongoDBURL = 'mongodb+srv://username:password@cluster.mongodb.net/bookstore';
   ```

4. **Start the development server:**

   ```bash
   npm run dev
   ```

   Or for production:

   ```bash
   npm start
   ```

The server will start on `http://localhost:5555`

## API Endpoints

### Base URL

```
http://localhost:5555
```

### Books Endpoints

#### 1. Get All Books

- **GET** `/books`
- **Description:** Retrieve all books from the database
- **Response:**
  ```json
  {
    "count": 2,
    "data": [
      {
        "_id": "64a1b2c3d4e5f6789abcdef0",
        "title": "The Great Gatsby",
        "author": "F. Scott Fitzgerald",
        "publishYear": 1925,
        "createdAt": "2023-07-01T10:00:00.000Z",
        "updatedAt": "2023-07-01T10:00:00.000Z"
      }
    ]
  }
  ```

#### 2. Get Single Book

- **GET** `/books/:id`
- **Description:** Retrieve a specific book by ID
- **Parameters:** `id` (MongoDB ObjectId)
- **Response:**
  ```json
  {
    "_id": "64a1b2c3d4e5f6789abcdef0",
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "publishYear": 1925,
    "createdAt": "2023-07-01T10:00:00.000Z",
    "updatedAt": "2023-07-01T10:00:00.000Z"
  }
  ```

#### 3. Create New Book

- **POST** `/books`
- **Description:** Add a new book to the database
- **Request Body:**
  ```json
  {
    "title": "To Kill a Mockingbird",
    "author": "Harper Lee",
    "publishYear": 1960
  }
  ```
- **Response:** Created book object with generated ID and timestamps

#### 4. Update Book

- **PUT** `/books/:id`
- **Description:** Update an existing book
- **Parameters:** `id` (MongoDB ObjectId)
- **Request Body:** Any combination of `title`, `author`, `publishYear`
- **Response:** Updated book object

#### 5. Delete Book

- **DELETE** `/books/:id`
- **Description:** Remove a book from the database
- **Parameters:** `id` (MongoDB ObjectId)
- **Response:** Success message

## Data Model

### Book Schema

```javascript
{
  title: {
    type: String,
    required: true
  },
  author: {
    type: String,
    required: true
  },
  publishYear: {
    type: Number,
    required: true
  }
}
```

**Auto-generated fields:**

- `_id`: MongoDB ObjectId (primary key)
- `createdAt`: Timestamp of creation
- `updatedAt`: Timestamp of last modification

## Configuration

### Environment Setup

The application uses a `config.js` file for configuration:

```javascript
// config.js
export const PORT = process.env.PORT || 5555;
export const mongoDBURL =
  process.env.MONGODB_URL || "mongodb://localhost:27017/bookstore";
```

### CORS Configuration

CORS is configured to allow all origins for development. For production, modify the CORS settings in `index.js`:

```javascript
// Allow specific origins
app.use(
  cors({
    origin: "http://localhost:3000",
    methods: ["GET", "POST", "PUT", "DELETE"],
    allowedHeaders: ["Content-Type"],
  })
);
```

## Available Scripts

```json
{
  "start": "node index.js", // Production server
  "dev": "nodemon index.js" // Development server with auto-restart
}
```

## Error Handling

The API includes comprehensive error handling:

- **400 Bad Request:** Missing required fields
- **404 Not Found:** Book not found
- **500 Internal Server Error:** Database or server errors

Example error response:

```json
{
  "message": "Send all required fields: title, author, publishYear"
}
```

## Middleware

### 1. Express JSON Parser

Parses incoming JSON requests:

```javascript
app.use(express.json());
```

### 2. CORS Middleware

Handles cross-origin requests:

```javascript
app.use(cors());
```

## Database Connection

MongoDB connection is established using Mongoose:

```javascript
mongoose
  .connect(mongoDBURL)
  .then(() => {
    console.log("App connected to database");
    app.listen(PORT, () => {
      console.log(`App is listening to port: ${PORT}`);
    });
  })
  .catch((error) => {
    console.log(error);
  });
```

## Testing the API

### Using cURL

**Get all books:**

```bash
curl -X GET http://localhost:5555/books
```

**Create a new book:**

```bash
curl -X POST http://localhost:5555/books \
  -H "Content-Type: application/json" \
  -d '{"title":"1984","author":"George Orwell","publishYear":1949}'
```

**Update a book:**

```bash
curl -X PUT http://localhost:5555/books/64a1b2c3d4e5f6789abcdef0 \
  -H "Content-Type: application/json" \
  -d '{"title":"Animal Farm","author":"George Orwell","publishYear":1945}'
```

**Delete a book:**

```bash
curl -X DELETE http://localhost:5555/books/64a1b2c3d4e5f6789abcdef0
```

### Using Postman

1. Import the collection with base URL: `http://localhost:5555`
2. Test all endpoints with appropriate headers and request bodies
3. Set `Content-Type: application/json` for POST and PUT requests

## Development

### Code Structure Best Practices

- **Modular routing:** Routes are separated into dedicated files
- **Model separation:** Database schemas are in separate model files
- **Error handling:** Consistent error responses across all endpoints
- **Async/await:** Modern JavaScript async patterns

### Adding New Features

1. Define new routes in the `routes/` directory
2. Create corresponding models in the `models/` directory
3. Import and use routes in `index.js`
4. Test endpoints thoroughly

## Dependencies

### Production Dependencies

```json
{
  "cors": "^2.8.5",
  "express": "^4.18.2",
  "mongoose": "^7.3.1"
}
```

### Development Dependencies

```json
{
  "nodemon": "^2.0.22"
}
```

## Deployment

### Local Production Build

```bash
npm start
```

### Environment Variables for Production

Set the following environment variables:

- `PORT`: Server port (default: 5555)
- `MONGODB_URL`: MongoDB connection string

## Contributing

1. Follow the existing code structure
2. Add error handling for new endpoints
3. Update this README for new features
4. Test all endpoints before submitting

## ‍Author

**MamadTaheri68**

---

**The backend is now ready to serve your Book Store application!**
