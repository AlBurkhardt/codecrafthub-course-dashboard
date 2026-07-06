# CodeCraftHub Course Dashboard

A lightweight, single-page HTML dashboard for managing learning courses. This dashboard provides a user-friendly interface to view, create, and delete courses tracked through the CodeCraftHub REST API.

## Overview

The **CodeCraftHub Course Dashboard** is a frontend client that connects to the [CodeCraftHub API](https://github.com/AlBurkhardt/codecraft-hub) to display and manage course data. It's built with vanilla JavaScript (no frameworks) for simplicity and quick deployment.

## Features

- **View Courses** - Displays all courses with details (name, description, target date, status)
- **Create Courses** - Add new learning courses via an intuitive form
- **Delete Courses** - Remove courses from the system
- **Real-time Feedback** - Success and error messages provide immediate user feedback
- **Loading Indicator** - Visual feedback during API calls
- **Responsive Design** - Works on desktop and mobile devices

## Requirements

- Modern web browser (Chrome, Firefox, Safari, Edge)
- [CodeCraftHub API](https://github.com/AlBurkhardt/codecraft-hub) running on `http://localhost:5000`

## Getting Started

### 1. Clone or download the dashboard

```bash
git clone https://github.com/AlBurkhardt/codecrafthub-course-dashboard.git
cd codecrafthub-course-dashboard
```

### 2. Serve the dashboard

Option A: Using Python (built-in)
```bash
python -m http.server 8000
```

Option B: Using Node.js `http-server`
```bash
npx http-server public/
```

Option C: Using VS Code Live Server extension
- Right-click on `public/index.html` and select "Open with Live Server"

### 3. Ensure the API is running

The dashboard expects the CodeCraftHub API to be running on `http://localhost:5000`.

```bash
cd ../codecraft-hub
npm start
```

### 4. Open the dashboard

Navigate to the served URL in your browser (e.g., `http://localhost:8000` or `http://localhost:5500` for Live Server).

## File Structure

```
codecrafthub-course-dashboard/
├── README.md                  # This file
├── public/
│   └── index.html            # Single-page dashboard with embedded CSS and JavaScript
└── .git/                      # Git repository
```

## API Integration

The dashboard communicates with the CodeCraftHub API at `http://localhost:5000/api/courses`.

### Endpoints Used

- **GET /api/courses** - Fetch all courses
- **POST /api/courses** - Create a new course
- **DELETE /api/courses/:id** - Remove a course

For full API documentation, see the [CodeCraftHub README](https://github.com/AlBurkhardt/codecraft-hub#readme).

## Form Fields

When creating a course, the following fields are required:

- **Course Name** - Title of the course
- **Description** - Detailed description of what will be learned
- **Target Date** - Expected completion date (format: YYYY-MM-DD)
- **Status** - One of: `Not Started`, `In Progress`, `Completed`

## Code Organization

### HTML Structure
- **Header** - Application title and branding
- **Form Section** - Course creation form
- **Courses List** - Dynamic area where courses are rendered

### JavaScript Functions

| Function | Purpose |
|----------|---------|
| `fetchCourses()` | Retrieves all courses from the API |
| `displayCourses(courses)` | Renders courses as interactive cards |
| `addCourse()` | Validates form and creates a new course |
| `deleteCourse(id)` | Removes a course from the system |
| `editCourse(id)` | Placeholder for future editing feature |
| `toggleLoading(show)` | Shows/hides the loading indicator |
| `showError(message)` | Displays an error alert (3 seconds) |
| `showSuccess(message)` | Displays a success alert (3 seconds) |

### CSS Classes

| Class | Purpose |
|-------|---------|
| `.btn-primary` | Purple button for form submission |
| `.btn-success` | Orange button for edit actions |
| `.btn-danger` | Red button for delete actions |
| `.course-card` | Container for individual course display |
| `.loading` | Loading indicator |
| `.error` | Error message alert |
| `.success` | Success message alert |

## CORS Configuration

The dashboard runs on a different port than the API, so CORS (Cross-Origin Resource Sharing) headers are required. The CodeCraftHub API includes CORS middleware to allow requests from any origin.

If you encounter CORS errors:
1. Ensure the API is running on `localhost:5000`
2. Check that the API has CORS headers enabled (see CodeCraftHub API documentation)
3. Check browser console (F12) for detailed error messages

## Future Enhancements

- [ ] Implement course editing functionality
- [ ] Add course filtering by status
- [ ] Display course statistics (total, by status)
- [ ] Add search functionality
- [ ] Implement pagination for large course lists
- [ ] Add authentication/user accounts
- [ ] Store preferences in browser localStorage

## Troubleshooting

### Courses not loading
- Check that the API is running on `http://localhost:5000`
- Open browser console (F12) and look for network errors
- Verify CORS headers are present in API responses

### Form submission fails
- Check that all required fields are filled
- Look at the browser console for validation error details
- Ensure the API is accessible and running

### "Edit functionality is not implemented" message
- The edit feature is currently a placeholder (TODO)

## License

ISC

## Related Projects

- [CodeCraftHub API](https://github.com/AlBurkhardt/codecraft-hub) - The backend REST API
