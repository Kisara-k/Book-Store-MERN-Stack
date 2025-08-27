# Book Store MERN Stack Application

A full-stack web application for managing a book store built with the MERN stack (MongoDB, Express.js, React, Node.js). This application allows users to perform CRUD operations on a book collection with a modern and intuitive user interface.
<!--
## Screenshots

![Book Store Application](https://via.placeholder.com/800x400?text=Book+Store+Application)
-->
## Features

- **Complete CRUD Operations**: Create, Read, Update, and Delete books
- **Modern UI**: Built with React and styled with Tailwind CSS
- **Responsive Design**: Works seamlessly on desktop and mobile devices
- **Multiple View Options**: Toggle between table and card view for book listings
- **Real-time Updates**: Instant UI updates after operations
- **RESTful API**: Well-structured backend API endpoints
- **MongoDB Integration**: Persistent data storage with MongoDB
- **CORS Enabled**: Cross-origin resource sharing configured for development

## Tech Stack

### Frontend

- **React** 18.2.0 - UI library
- **Vite** - Build tool and development server
- **React Router DOM** - Client-side routing
- **Axios** - HTTP client for API requests
- **Tailwind CSS** - Utility-first CSS framework
- **React Icons** - Icon library
- **Notistack** - Notification system

### Backend

- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling
- **CORS** - Cross-origin resource sharing
- **Nodemon** - Development auto-restart

## Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (version 14 or higher)
- **npm** or **yarn**
- **MongoDB** (local installation or MongoDB Atlas account)
- **Git**

## Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/mohammad-taheri1/Book-Store-MERN-Stack.git
cd Book-Store-MERN-Stack
```

### 2. Backend Setup

```bash
cd backend
npm install
```

Create a `config.js` file in the backend directory:

```javascript
export const PORT = 5555;
export const mongoDBURL = "mongodb://localhost:27017/bookstore";
// Or for MongoDB Atlas:
// export const mongoDBURL = 'mongodb+srv://username:password@cluster.mongodb.net/bookstore';
```

Start the backend server:

```bash
npm run dev
```

The backend will run on `http://localhost:5555`

### 3. Frontend Setup

Open a new terminal and navigate to the frontend directory:

```bash
cd frontend
npm install
npm run dev
```

The frontend will run on `http://localhost:5173`

### 4. Database Setup

Make sure MongoDB is running on your system. The application will automatically create the necessary database and collections.

## Project Structure

```
Book-Store-MERN-Stack/
├── backend/                 # Backend API server
│   ├── config.js           # Database and server configuration
│   ├── index.js            # Main server file
│   ├── package.json        # Backend dependencies
│   ├── models/             # MongoDB schemas
│   │   └── bookModel.js    # Book model definition
│   └── routes/             # API routes
│       └── booksRoute.js   # Book-related endpoints
├── frontend/               # React frontend application
│   ├── public/             # Static assets
│   ├── src/                # Source code
│   │   ├── components/     # Reusable components
│   │   ├── pages/          # Page components
│   │   ├── App.jsx         # Main App component
│   │   └── main.jsx        # Application entry point
│   ├── package.json        # Frontend dependencies
│   └── vite.config.js      # Vite configuration
├── Chapters.md             # Development chapters/notes
└── README.md               # This file
```

## API Endpoints

| Method | Endpoint     | Description         |
| ------ | ------------ | ------------------- |
| GET    | `/books`     | Get all books       |
| GET    | `/books/:id` | Get a specific book |
| POST   | `/books`     | Create a new book   |
| PUT    | `/books/:id` | Update a book       |
| DELETE | `/books/:id` | Delete a book       |

### Book Schema

```javascript
{
  title: String (required),
  author: String (required),
  publishYear: Number (required),
  createdAt: Date (auto-generated),
  updatedAt: Date (auto-generated)
}
```

## Application Pages

- **Home** (`/`) - Display all books with table/card view toggle
- **Create Book** (`/books/create`) - Add a new book to the collection
- **Show Book** (`/books/details/:id`) - View detailed information about a book
- **Edit Book** (`/books/edit/:id`) - Update book information
- **Delete Book** (`/books/delete/:id`) - Remove a book from the collection

## UI Components

- **BooksTable** - Tabular view of books
- **BooksCard** - Card-based view of books
- **BookSingleCard** - Individual book card component
- **BookModal** - Modal for quick book actions
- **BackButton** - Navigation helper
- **Spinner** - Loading indicator

## Development

### Backend Development

```bash
cd backend
npm run dev  # Starts with nodemon for auto-restart
```

### Frontend Development

```bash
cd frontend
npm run dev  # Starts Vite development server
```

### Building for Production

```bash
# Frontend
cd frontend
npm run build

# Backend
cd backend
npm start
```

## Environment Variables

Create a `config.js` file in the backend directory:

```javascript
export const PORT = process.env.PORT || 5555;
export const mongoDBURL =
  process.env.MONGODB_URL || "mongodb://localhost:27017/bookstore";
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the ISC License.

## Author

**MamadTaheri68**

## Acknowledgments

- React team for the amazing framework
- MongoDB team for the excellent database
- Express.js team for the web framework
- Tailwind CSS for the utility-first CSS framework

## Support

If you have any questions or run into issues, please open an issue on GitHub.

---

**Happy Coding!**
