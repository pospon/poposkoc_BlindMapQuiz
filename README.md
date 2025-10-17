# Blind Map Quiz

An interactive web-based geography quiz that challenges users to locate cities on a blank world map.

## Overview

Blind Map Quiz is a simple, educational web application that tests your geographical knowledge. Choose from multiple quiz themes, each with different sets of locations. Players are given the name of a city and must click on a blank map to guess its location. The app provides instant feedback by showing the actual location and calculating the distance between the guess and the correct position.

## Available Quizzes

- **🌍 World Capitals** - Identify major capital cities around the world (Medium)
- **🏙️ Major World Cities** - Find the most populous and famous cities globally (Medium)
- **🇪🇺 European Cities** - Test your knowledge of European cities (Easy)
- **🌏 Asian Cities** - Locate major cities across Asia (Hard)
- **🇺🇸 United States Cities** - Find major US cities from coast to coast (Easy)

## Features

- **Multiple Quiz Types**: Choose from 5 different quiz themes with unique location sets
- **Interactive Map**: Powered by Leaflet.js with a clean, label-free world map
- **Multiple Rounds**: Play through 10 rounds with randomly selected cities
- **Score Tracking**: Earn up to 1000 points per round based on accuracy
- **Difficulty Levels**: Easy, Medium, and Hard quizzes to match your knowledge
- **Instant Feedback**: Visual markers show your guess vs. the actual location
- **Distance Calculation**: Uses the Haversine formula to calculate the distance between your guess and the correct location in kilometers
- **Game Statistics**: Track your progress with round counter, cumulative score, and average distance
- **Beautiful Landing Page**: Modern, gradient-styled quiz selection interface
- **Simple UI**: Minimalist design focused on the learning experience
- **No Backend Required**: Runs entirely in the browser
- **Responsive Design**: Works on both desktop and mobile devices

## Technologies

- HTML5
- Vanilla JavaScript
- [Leaflet.js](https://leafletjs.com/) (v1.9.4) - Interactive mapping library
- [CartoDB](https://carto.com/) - No-label map tiles
- [Flaticon](https://www.flaticon.com/) - Custom marker icons

## Getting Started

### Prerequisites

No installation required! Just a modern web browser.

### Running the Application

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd poposkoc_BlindMapQuiz
   ```

2. Open `index.html` in your web browser:
   ```bash
   open index.html
   # or simply double-click the file
   ```

3. Choose a quiz from the landing page and start playing!

That's it! The application will load and you can start playing.

## How to Play

1. Open `index.html` in your browser
2. Choose a quiz from the landing page (e.g., "World Capitals", "European Cities")
3. Read the location name displayed at the top (e.g., "Paris")
4. Click on the map where you think the location is
5. The app will show:
   - A blue marker for your guess
   - A red marker for the actual location
   - A line connecting the two points
   - The distance between your guess and the actual location in kilometers
   - Your score for that round (max 1000 points based on accuracy)
6. Click "Next Round" to continue to the next location
7. Complete all 10 rounds to see your final score and average distance
8. Choose to play again or select a different quiz

## Project Structure

```
poposkoc_BlindMapQuiz/
├── index.html           # Landing page with quiz selection
├── map.html             # Main quiz game interface
├── quizzes/             # Quiz data files
│   ├── world-capitals.js
│   ├── major-cities.js
│   ├── european-cities.js
│   ├── asian-cities.js
│   └── us-cities.js
├── map.md               # Original project documentation
└── README.md            # This file
```

## How It Works

The application uses the Haversine formula to calculate the great-circle distance between two points on Earth given their latitude and longitude coordinates. This provides an accurate measure of how close your guess was to the actual location.

### Scoring System

Points are awarded based on accuracy:
- **Perfect guess** (0 km away): 1000 points
- **Close guess** (100 km away): ~950 points
- **Moderate guess** (500 km away): ~750 points
- **Far guess** (1000+ km away): <500 points

The formula is: `max(0, 1000 - (distance / 20))`

### Quiz System

The game uses a modular quiz system where each quiz is defined in a separate JavaScript file. Each quiz includes:
- **Quiz ID**: Unique identifier for the quiz
- **Title**: Display name of the quiz
- **Description**: What the quiz covers
- **Difficulty**: Easy, Medium, or Hard
- **Total Rounds**: Number of rounds (typically 10)
- **Locations**: Array of cities with coordinates

Each game randomly selects locations from the quiz's dataset for variety.

### Adding New Quizzes

To add a new quiz, create a new file in the `quizzes/` directory with the following structure:

```javascript
const QUIZ_DATA = {
  id: "your-quiz-id",
  title: "Your Quiz Title",
  description: "Description of your quiz",
  difficulty: "Easy", // Easy, Medium, or Hard
  totalRounds: 10,
  locations: [
    { name: "City Name", lat: 40.7128, lng: -74.0060 },
    // Add more locations...
  ]
};
```

Then add a link to the quiz on the landing page (index.html).

## Future Enhancements

Potential improvements could include:
- ✅ ~~Multiple rounds with different locations~~ (Implemented!)
- ✅ ~~Score tracking system~~ (Implemented!)
- ✅ ~~Multiple quiz types~~ (Implemented!)
- ✅ ~~Difficulty levels~~ (Implemented!)
- Timer-based challenges
- Leaderboard functionality with localStorage
- More quiz themes (South American cities, African capitals, etc.)
- Hints system (show continent, region, etc.)
- Multiplayer mode
- Custom quiz creator

## License

This project is open source and available for educational purposes.

## Acknowledgments

- Map tiles by [CartoDB](https://carto.com/)
- Mapping library by [Leaflet](https://leafletjs.com/)
- Icons from [Flaticon](https://www.flaticon.com/)
