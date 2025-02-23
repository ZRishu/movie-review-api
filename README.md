# Movie Review API

A RESTful API built with Spring Boot that manages movies and their reviews. The API uses MongoDB as its database and provides endpoints for retrieving movies and creating reviews.

## Technologies Used
- Spring Boot
- MongoDB
- Lombok
- Spring Data MongoDB

## API Endpoints

### Movies
- `GET /api/v1/movies`
  - Returns a list of all movies
  - Response includes movie details, including IMDB ID, title, release date, trailer link, poster, genres, and backdrops

- `GET /api/v1/movies/{imdbId}`
  - Returns a single movie by its IMDB ID
  - Example: `GET /api/v1/movies/tt1234567`

### Reviews
- `POST /api/v1/reviews`
  - Creates a new review for a movie
  - Request body should be JSON in the format:
    ```json
    {
        "reviewBody": "Your review text here",
        "imdbId": "movie's IMDB ID"
    }
    ```

## Data Models

### Movie
- `id`: ObjectId (MongoDB generated)
- `imdbId`: String
- `title`: String
- `releaseDate`: String
- `trailerLink`: String
- `poster`: String
- `genres`: List<String>
- `backdrops`: List<String>
- `reviewIds`: List<Review>

### Review
- `id`: ObjectId (MongoDB generated)
- `body`: String

## Setup and Installation

1. Ensure you have MongoDB installed and running
2. Clone the repository
3. Configure MongoDB connection in `application.properties`
4. Run the Spring Boot application:
   ```bash
   ./mvnw spring-boot:run

## Example Usage

### Get All Movies
```bash
curl http://localhost:8080/api/v1/movies
```

### Get Single Movie
```bash
curl http://localhost:8080/api/v1/movies/tt1234567
```

### Create Review
```bash
curl -X POST http://localhost:8080/api/v1/reviews \
-H "Content-Type: application/json" \
-d '{"reviewBody": "Great movie!", "imdbId": "tt1234567"}'
```
