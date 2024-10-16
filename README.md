﻿# Real-Time-Leaderboard
![image](https://github.com/user-attachments/assets/9d7db6b4-a0b9-41d7-bc0f-d0f550957a65)
![image](https://github.com/user-attachments/assets/9efe3fb8-e0e7-4eae-81a7-53d88ff0a8f7)



```markdown
# Real-Time Leaderboard

The Real-Time Leaderboard project is a backend service designed to manage and display real-time leaderboards for various games. It provides a comprehensive set of features for user authentication, game management, and score tracking. Users can sign up, log in, and submit their scores, which are then used to generate dynamic leaderboards. The service includes robust authentication and authorization mechanisms, ensuring secure access to protected routes.

## Features
- User authentication and authorization
- User management (create, update, delete, find)
- Game management (create, update, delete, find)
- Score submission and retrieval
- Real-time leaderboard for games
- Protected routes with JWT authentication
- Refresh tokens for session management
- Redis integration for caching
- PostgreSQL database for persistent storage
- TypeORM for object-relational mapping
- User ranking for games
- Top players report for games
- Leaderboard for games
- Top players report for games within a date range
- Top players across all leaderboards

## Project URL
[Real-Time Leaderboard on GitHub](https://github.com/harshraj6582/Real-Time-Leaderboard)

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/harshraj6582/Real-Time-Leaderboard
   ```

2. Navigate to the project directory:
   ```bash
   cd Real-Time-Leaderboard
   ```

3. Set up a `.env` file to configure the environment variables with the following parameters:
   ```plaintext
   DB_HOST=your_database_host
   DB_PORT=your_database_port
   DB_USERNAME=your_database_username
   DB_PASSWORD=your_database_password
   DB_DATABASE=your_database_name

   JWT_SECRET=your_jwt_secret
   ACCESSTOKEN_LIFETIME=access_token_lifetime_in_seconds
   REFRESHTOKEN_LIFETIME=refresh_token_lifetime_in_seconds
   REFRESH_TOKEN_SECRET=your_refresh_token_secret

   REDIS_PASSWORD=your_redis_password
   REDIS_HOST=your_redis_host
   REDIS_PORT=your_redis_port
   ```
   Make sure to replace the placeholders with your actual credentials and values for the environment variables.

4. Install the dependencies:
   ```bash
   npm install
   ```

## Usage
- Start the development server:
   ```bash
   npm run start:dev
   ```
   The application will be running at [http://localhost:3000](http://localhost:3000).

## Technology Stack
- TypeScript
- Node.js
- NestJS
- TypeORM
- PostgreSQL
- Redis
- Passport
- JWT

## API Endpoints

### Auth
- **POST /auth/signup**
  - **Description:** Sign up a new user.
  - **Body:** CreateUserDto

- **POST /auth/login**
  - **Description:** Log in a user.
  - **Body:** LoginDto

- **GET /auth/protected**
  - **Description:** Access a protected route.
  - **Headers:** Authorization: Bearer `<token>`

- **POST /auth/refreshToken**
  - **Description:** Refresh the authentication token.
  - **Body:** `{ "refreshToken": "string" }`

- **POST /auth/logout**
  - **Description:** Log out the current user.
  - **Headers:** Authorization: Bearer `<token>`

### User
- **GET /user**
  - **Description:** Find a user by email.
  - **Query:** email
  - **Headers:** Authorization: Bearer `<token>`

- **PATCH /user/:id**
  - **Description:** Update a user by ID.
  - **Params:** id
  - **Body:** UpdateUserDto
  - **Headers:** Authorization: Bearer `<token>`

- **DELETE /user/:id**
  - **Description:** Delete a user by ID.
  - **Params:** id
  - **Headers:** Authorization: Bearer `<token>`

- **GET /user/me**
  - **Description:** Get the current logged-in user.
  - **Headers:** Authorization: Bearer `<token>`

- **GET /user/ranking**
  - **Description:** Get the ranking of the current user for a specific game.
  - **Query:** gameName
  - **Headers:** Authorization: Bearer `<token>`

- **GET /user/ranking/:gameName**
  - **Description:** Get the top players for a specific game.
  - **Params:** gameName
  - **Headers:** Authorization: Bearer `<token>`

### Score
- **POST /score**
  - **Description:** Submit a score for a game.
  - **Body:** CreateScoreDto
  - **Query:** gameName
  - **Headers:** Authorization: Bearer `<token>`

- **GET /score**
  - **Description:** Get the highest scores for a game.
  - **Query:** gameName
  - **Headers:** Authorization: Bearer `<token>`

- **GET /score/top-players**
  - **Description:** Get a report of the top players for a game within a date range.
  - **Query:** gameId, startDate, endDate, limit
  - **Headers:** Authorization: Bearer `<token>`

### Game
- **POST /game**
  - **Description:** Create a new game.
  - **Body:** CreateGameDto

- **GET /game/:id**
  - **Description:** Find a game by ID.
  - **Params:** id

- **GET /game**
  - **Description:** Find a game by name.
  - **Query:** name

- **PATCH /game/:id**
  - **Description:** Update a game by ID.
  - **Params:** id
  - **Body:** UpdateGameDto

- **DELETE /game/:id**
  - **Description:** Delete a game by ID.
  - **Params:** id

### Leaderboard
- **GET /leaderboard**
  - **Description:** Get the highest scores.
  - **Headers:** Authorization: Bearer `<token>`

- **GET /leaderboard/game**
  - **Description:** Get the leaderboard for a specific game.
  - **Query:** gameName
  - **Headers:** Authorization: Bearer `<token>`

## Contributing
1. Fork the repository.
2. Create a new branch:
   ```bash
   git checkout -b feature-branch
   ```
3. Make your changes.
4. Commit your changes:
   ```bash
   git commit -m 'Add some feature'
   ```
5. Push to the branch:
   ```bash
   git push origin feature-branch
   ```
6. Open a pull request.
```

This README file provides a comprehensive overview of your project, including its features, installation instructions, usage, technology stack, API endpoints, and contribution guidelines. Feel free to modify any sections as necessary!
