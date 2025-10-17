# Blind Map Quiz

An interactive web-based geography quiz that challenges users to locate cities on a blank world map.

## Overview

Blind Map Quiz is a simple, educational web application that tests your geographical knowledge. Players are given the name of a city and must click on a blank map to guess its location. The app provides instant feedback by showing the actual location and calculating the distance between the guess and the correct position.

## Features

- **Interactive Map**: Powered by Leaflet.js with a clean, label-free world map
- **Instant Feedback**: Visual markers show your guess vs. the actual location
- **Distance Calculation**: Uses the Haversine formula to calculate the distance between your guess and the correct location in kilometers
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

2. Open `map.html` in your web browser:
   ```bash
   open map.html
   # or simply double-click the file
   ```

That's it! The application will load and you can start playing.

## How to Play

1. Open the application in your browser
2. Read the location name displayed at the top (e.g., "Paris")
3. Click on the map where you think the location is
4. The app will show:
   - A blue marker for your guess
   - A red marker for the actual location
   - A line connecting the two points
   - The distance between your guess and the actual location in kilometers

## Project Structure

```
poposkoc_BlindMapQuiz/
├── map.html    # Main application file
├── map.md      # Project documentation
└── README.md   # This file
```

## How It Works

The application uses the Haversine formula to calculate the great-circle distance between two points on Earth given their latitude and longitude coordinates. This provides an accurate measure of how close your guess was to the actual location.

## Future Enhancements

Potential improvements could include:
- Multiple rounds with different locations
- Score tracking system
- Difficulty levels (continents, countries, cities)
- Timer-based challenges
- Leaderboard functionality
- Random location selection from a database

## License

This project is open source and available for educational purposes.

## Acknowledgments

- Map tiles by [CartoDB](https://carto.com/)
- Mapping library by [Leaflet](https://leafletjs.com/)
- Icons from [Flaticon](https://www.flaticon.com/)
