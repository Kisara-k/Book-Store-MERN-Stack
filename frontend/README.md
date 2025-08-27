# Frontend - Book Store React Application

A modern, responsive React frontend for the Book Store application. Built with React 18, Vite, and Tailwind CSS, providing an intuitive interface for managing books with full CRUD operations.

## Technology Stack

- **React** 18.2.0 - Component-based UI library
- **Vite** - Next-generation frontend build tool
- **React Router DOM** - Declarative routing for React
- **Axios** - Promise-based HTTP client
- **Tailwind CSS** - Utility-first CSS framework
- **React Icons** - Popular icon library
- **Notistack** - Notification system for React

## Features

- **Modern UI/UX:** Clean, intuitive interface with Tailwind CSS
- **Responsive Design:** Mobile-first approach, works on all devices
- **Multiple View Modes:** Toggle between table and card views
- **Real-time Updates:** Instant UI feedback for all operations
- **Form Validation:** Client-side validation for book data
- **Loading States:** Spinner components for better UX
- **Navigation:** Seamless routing with React Router
- **Notifications:** User feedback for actions and errors

## Project Structure

```
frontend/
├── public/                    # Static assets
│   └── vite.svg              # Vite logo
├── src/                      # Source code
│   ├── assets/               # Images and static resources
│   │   └── react.svg         # React logo
│   ├── components/           # Reusable components
│   │   ├── BackButton.jsx    # Navigation back button
│   │   ├── Spinner.jsx       # Loading spinner
│   │   └── home/             # Home page components
│   │       ├── BookModal.jsx     # Book modal dialog
│   │       ├── BooksCard.jsx     # Card view for books
│   │       ├── BookSingleCard.jsx # Individual book card
│   │       └── BooksTable.jsx    # Table view for books
│   ├── pages/                # Page components (routes)
│   │   ├── CreateBooks.jsx   # Create new book page
│   │   ├── DeleteBook.jsx    # Delete book confirmation
│   │   ├── EditBook.jsx      # Edit book page
│   │   ├── Home.jsx          # Home page with book list
│   │   └── ShowBook.jsx      # Book details page
│   ├── App.jsx               # Main application component
│   ├── index.css             # Global styles and Tailwind imports
│   └── main.jsx              # Application entry point
├── index.html                # HTML template
├── package.json              # Dependencies and scripts
├── postcss.config.js         # PostCSS configuration
├── tailwind.config.js        # Tailwind CSS configuration
└── vite.config.js            # Vite build configuration
```

## Getting Started

### Prerequisites

- Node.js (version 14 or higher)
- npm or yarn package manager
- Backend API running on `http://localhost:5555`

### Installation

1. **Navigate to the frontend directory:**

   ```bash
   cd frontend
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Start the development server:**

   ```bash
   npm run dev
   ```

4. **Open your browser:**
   Navigate to `http://localhost:5173`

## Application Pages

### 1. Home Page (`/`)

- **Purpose:** Display all books in the collection
- **Features:**
  - Toggle between table and card view
  - Quick action buttons (View, Edit, Delete)
  - Add new book button
  - Loading spinner during data fetch
- **Components Used:** `BooksTable`, `BooksCard`, `Spinner`

### 2. Create Book Page (`/books/create`)

- **Purpose:** Add new books to the collection
- **Features:**
  - Form with title, author, and publish year fields
  - Form validation
  - Success/error notifications
  - Back navigation
- **API Integration:** POST `/books`

### 3. Book Details Page (`/books/details/:id`)

- **Purpose:** View detailed information about a specific book
- **Features:**
  - Complete book information display
  - Action buttons (Edit, Delete)
  - Back navigation
- **API Integration:** GET `/books/:id`

### 4. Edit Book Page (`/books/edit/:id`)

- **Purpose:** Update existing book information
- **Features:**
  - Pre-populated form with current book data
  - Form validation
  - Success/error notifications
  - Back navigation
- **API Integration:** GET `/books/:id`, PUT `/books/:id`

### 5. Delete Book Page (`/books/delete/:id`)

- **Purpose:** Confirm book deletion
- **Features:**
  - Book information display
  - Confirmation dialog
  - Safe deletion with confirmation
  - Back navigation
- **API Integration:** GET `/books/:id`, DELETE `/books/:id`

## Components

### Core Components

#### `App.jsx`

Main application component that sets up routing:

```jsx
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/books/create" element={<CreateBook />} />
  <Route path="/books/details/:id" element={<ShowBook />} />
  <Route path="/books/edit/:id" element={<EditBook />} />
  <Route path="/books/delete/:id" element={<DeleteBook />} />
</Routes>
```

#### `BackButton.jsx`

Reusable navigation component:

- Provides consistent back navigation
- Uses React Router's navigation
- Styled with Tailwind CSS

#### `Spinner.jsx`

Loading indicator component:

- Shows during API calls
- Improves user experience
- Animated CSS spinner

### Home Page Components

#### `BooksTable.jsx`

Tabular display of books:

- Responsive table design
- Sortable columns
- Action buttons for each book
- Mobile-friendly layout

#### `BooksCard.jsx`

Card-based display container:

- Grid layout for book cards
- Responsive design
- Better visual appeal

#### `BookSingleCard.jsx`

Individual book card:

- Book information display
- Action buttons
- Hover effects
- Image placeholders

#### `BookModal.jsx`

Modal dialog for quick actions:

- Overlay interface
- Quick book operations
- Keyboard navigation support

## Styling

### Tailwind CSS Configuration

```javascript
// tailwind.config.js
export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

### Global Styles

```css
/* index.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

/* Custom styles and overrides */
```

### Responsive Design

- Mobile-first approach
- Breakpoint-based design
- Flexible grid layouts
- Touch-friendly interfaces

## API Integration

### Base Configuration

```javascript
const API_BASE_URL = "http://localhost:5555";
```

### API Endpoints Used

- **GET** `/books` - Fetch all books
- **GET** `/books/:id` - Fetch single book
- **POST** `/books` - Create new book
- **PUT** `/books/:id` - Update book
- **DELETE** `/books/:id` - Delete book

### Example API Call

```javascript
useEffect(() => {
  setLoading(true);
  axios
    .get("http://localhost:5555/books")
    .then((response) => {
      setBooks(response.data.data);
      setLoading(false);
    })
    .catch((error) => {
      console.log(error);
      setLoading(false);
    });
}, []);
```

## Available Scripts

```json
{
  "dev": "vite", // Development server
  "build": "vite build", // Production build
  "lint": "eslint src --ext js,jsx", // Code linting
  "preview": "vite preview" // Preview production build
}
```

### Development

```bash
npm run dev     # Start development server
```

### Production

```bash
npm run build   # Build for production
npm run preview # Preview production build
```

### Code Quality

```bash
npm run lint    # Check code quality
```

## Configuration Files

### Vite Configuration (`vite.config.js`)

```javascript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
});
```

### PostCSS Configuration (`postcss.config.js`)

```javascript
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
};
```

## State Management

### Local State with React Hooks

- `useState` for component state
- `useEffect` for side effects
- `useParams` for route parameters
- `useNavigate` for programmatic navigation

### Example State Management

```javascript
const [books, setBooks] = useState([]);
const [loading, setLoading] = useState(false);
const [showType, setShowType] = useState("table");
```

## Error Handling

### API Error Handling

```javascript
.catch((error) => {
  console.log(error);
  setLoading(false);
  // Show error notification
});
```

### Form Validation

- Client-side validation for required fields
- User-friendly error messages
- Prevent invalid submissions

## Responsive Features

### Breakpoints

- **sm:** 640px and up
- **md:** 768px and up
- **lg:** 1024px and up
- **xl:** 1280px and up

### Mobile Optimizations

- Touch-friendly buttons
- Responsive typography
- Optimized layouts
- Swipe gestures support

## Development

### Adding New Features

1. Create component in appropriate directory
2. Add routing if needed in `App.jsx`
3. Implement API integration
4. Add styling with Tailwind CSS
5. Test responsiveness

### Best Practices

- Component composition
- Custom hooks for shared logic
- Consistent naming conventions
- Proper error boundaries
- Performance optimization

## Dependencies

### Production Dependencies

```json
{
  "axios": "^1.4.0",
  "notistack": "^3.0.1",
  "react": "^18.2.0",
  "react-dom": "^18.2.0",
  "react-icons": "^4.10.1",
  "react-router-dom": "^6.14.1"
}
```

### Development Dependencies

```json
{
  "@vitejs/plugin-react": "^4.0.1",
  "autoprefixer": "^10.4.14",
  "eslint": "^8.44.0",
  "postcss": "^8.4.25",
  "tailwindcss": "^3.3.2",
  "vite": "^4.4.0"
}
```

## Deployment

### Build for Production

```bash
npm run build
```

### Deployment Options

- **Netlify:** Connect GitHub repository
- **Vercel:** Automatic deployments
- **GitHub Pages:** Static hosting
- **Traditional hosting:** Upload `dist` folder

### Environment Variables

Create `.env` file for environment-specific variables:

```
VITE_API_BASE_URL=http://localhost:5555
```

## Testing

### Manual Testing Checklist

- [ ] All pages load correctly
- [ ] CRUD operations work
- [ ] Responsive design on different devices
- [ ] Error handling works
- [ ] Navigation functions properly

### Future Testing Setup

- Jest for unit testing
- React Testing Library for component testing
- Cypress for end-to-end testing

## Contributing

1. Follow React best practices
2. Use Tailwind CSS for styling
3. Maintain responsive design
4. Add proper error handling
5. Update documentation

## Author

**MamadTaheri68**

---

**Ready to manage your book collection with style!**
