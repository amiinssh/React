Here is a README file for your movie search app:

---

# MovieLand - Movie Search App

MovieLand is a simple movie search web application that allows users to search for movies using the OMDb (Open Movie Database) API. It provides information about movies such as title, year, type, and poster image. The app allows users to search for movies and displays the results in a user-friendly format.

## Features

- Search for movies by title
- Displays movie details like title, year, type, and poster image
- Responsive design for mobile and desktop devices
- Error handling for cases where no movies are found

## Technologies Used

- **React**: JavaScript library for building user interfaces
- **OMDb API**: Used to fetch movie data based on search queries
- **CSS**: For styling the app and creating a responsive design
- **React Hooks**: `useState` and `useEffect` for state management and side effects

## Setup

### 1. Install Dependencies

Make sure you have Node.js installed, then run:

```bash
npm install
```

### 2. Start the Development Server

```bash
npm start
```

The application should now be running on `http://localhost:3000`.

## File Structure

```
src/
  ├── App.js          # Main application component
  ├── MovieCard.jsx    # Component for displaying individual movie information
  ├── index.js         # Entry point for React
  ├── App.css          # Styles for the app
  ├── search.svg       # Search icon
```

### App.js

- The main component of the app that handles the search functionality and fetches movie data from the OMDb API.
- It uses `useState` to manage state (movies and searchTerm) and `useEffect` to fetch movies when the component mounts.
- Displays an input field for searching and a list of movies in a container.

### MovieCard.jsx

- A component that represents each movie in the search results.
- Displays the movie's year, poster, type, and title.
- If a poster is not available, a placeholder image is displayed.

### index.js

- The entry point of the React app where the `App` component is rendered into the DOM.

### App.css

- The CSS file that provides styling for the app. It includes responsive styles for mobile and desktop devices.
- The app has a modern look with a shadowed search bar, gradient heading, and hover effects on movie cards.

## Usage

1. **Search for Movies**: Type the name of a movie in the search bar and click the search icon to see the results.
2. **No Movies Found**: If no movies are found, the app will display a message saying "No movies found."

## OMDb API

The app uses the OMDb API to fetch movie details. The API is accessed via a URL and includes an API key for authentication. The key used here is `954a998c`. You can replace it with your own API key if needed.

API URL format:

```
http://www.omdbapi.com/?apikey=your-api-key&s=movie-title
```

### Sample API Response

```json
{
  "Response": "True",
  "Search": [
    {
      "Title": "Batman Begins",
      "Year": "2005",
      "imdbID": "tt0372784",
      "Type": "movie",
      "Poster": "https://m.media-amazon.com/images/M/MV5BODIyMDdhNTgtNDlmOC00MjUxLWE2NDItODA5MTdkNzY3ZTdhXkEyXkFqcGc@._V1_SX300.jpg"
    },
    {
      "Title": "Batman v Superman: Dawn of Justice",
      "Year": "2016",
      "imdbID": "tt2975590",
      "Type": "movie",
      "Poster": "https://m.media-amazon.com/images/M/MV5BMTc0OTg3NDU1NV5BMl5BanBnXkFtZTgwNTY1MDAzNzE@._V1_SX300.jpg"
    }
  ]
}
```

## Troubleshooting

- **No Search Results**: If you search for a movie and no results are found, ensure that your search term is correct. Try different movie titles.
- **API Limit**: The OMDb API has rate limiting, so avoid excessive requests within a short period.
