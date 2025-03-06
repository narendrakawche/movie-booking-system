# Movie Booking Application

This is an advanced movie booking application built using the **MERN stack (MongoDB, Express.js, React, Node.js)**. The application provides functionalities for both administrators and regular users to manage and book movies.

## Overview

This application allows users to browse available movies, book seats, and view their booking history. Administrators have the privilege to create, update, and delete movie listings. The front-end is built with React and styled using Material UI, providing a responsive and user-friendly interface. Redux is used for state management, particularly for handling user authentication status. The back-end, built with Node.js and Express.js, provides a RESTful API to manage data stored in a MongoDB database. Security is implemented using JWT for authentication and bcrypt.js for password hashing.

## Key Features

*   **User Authentication:** Secure login and signup functionality for regular users. The user authentication state is managed using Redux.
*   **Admin Authentication:** Secure login and signup functionality for administrators.
*   **Movie Browsing:** Users can view the latest movie releases on the home page.
*   **View All Movies:** A dedicated page to display all available movies.
*   **Movie Booking:** Logged-in users can book seats for their chosen movies. Users can select seat numbers and booking dates.
*   **Booking Management (User):** Logged-in users can view their booking history.
*   **Admin Movie Management:** Authenticated administrators can add new movies with details like title, description, release date, poster URL, and actors. Administrators can also mark movies as featured to display them on the home page. Administrators can delete movies.
*   **Profile Pages:** Separate profile pages for users and administrators. User profiles display booking history. Admin profiles display movies added by them.
*   **Responsive Design:** The application UI is designed to be responsive using Material UI components.
*   **API Powered:** The front-end interacts with a RESTful API built with Node.js and Express.js.

## Technologies Used

This project utilises the following key technologies:

*   **MERN Stack:**
    *   **MongoDB:** A NoSQL database is used to store application data in collections and documents.
    *   **Express.js:** A flexible Node.js web application framework that provides a robust set of features for building APIs.
    *   **React:** A JavaScript library for building dynamic and interactive user interfaces. React Router is used for managing frontend routes.
    *   **Node.js:** A JavaScript runtime environment that allows JavaScript to be run on the server-side.
*   **Frontend:**
    *   **Material UI (MUI):** A popular React UI framework that provides pre-built and customizable components for rapid development and consistent styling.
    *   **Redux:** A predictable state container for JavaScript applications, used here for managing user and admin authentication states.
    *   **Redux Toolkit** is used to simplify Redux development. **React-Redux** provides bindings to connect React components to the Redux store.
    *   **Axios:** A promise-based HTTP client used to make API requests from the front-end to the back-end.
*   **Backend:**
    *   **JSON Web Tokens (JWT):** Used for implementing secure authentication and authorization for users and administrators.
    *   **bcrypt.js:** A library for hashing and salting passwords to securely store them in the database.
    *   **dotenv:** A zero-dependency module that loads environment variables from a `.env` file into `process.env`.
    *   **Mongoose:** An elegant MongoDB object modelling tool designed to work in an asynchronous environment, providing schema validation and more.
    *   **nodemon:** A tool that automatically restarts the Node.js server upon detecting file changes during development.
*   **API Testing:**
    *   **Postman:** Used for testing the back-end API endpoints.

## Installation

To run this project locally, follow these steps:

1.  **Prerequisites:** Ensure you have **Node.js** and **npm (Node Package Manager)** installed on your system. You can download them from [https://nodejs.org/](https://nodejs.org/).

2.  **Clone the Repository:** Clone this GitHub repository to your local machine.

3.  **Backend Setup:**
    *   Navigate to the `backend` directory in your project folder using the terminal (`cd backend`).
    *   Initialise a Node.js project (if not already done): `npm init -y`.
    *   Install the necessary backend dependencies:
        ```bash
        npm install express mongoose bcryptjs jsonwebtoken dotenv
        ```
        This will install Express.js for the server, Mongoose for MongoDB interaction, bcrypt.js for password hashing, jsonwebtoken for authentication, and dotenv for managing environment variables.
    *   Create a `.env` file in the `backend` directory.
    *   Add your MongoDB connection string to the `.env` file. You can obtain this from MongoDB Atlas after creating a project and a cluster. The `.env` file should look something like this:
        ```
        MONGO_URI=your_mongodb_connection_string_here
        JWT_SECRET=your_secret_key_for_jwt
        ```
        Replace `your_mongodb_connection_string_here` with your actual MongoDB connection string and `your_secret_key_for_jwt` with a secret key for signing JWT tokens (you might need to install the `dotenv` package: `npm install dotenv`).
    *   Modify the entry point in your `package.json` in the `backend` folder to `app.js`.
    *   You might want to add a `start` script to your `package.json` in the `backend` folder to run the server, potentially using `nodemon` for development:
        ```json
        "scripts": {
          "start": "nodemon app.js"
        }
        ```
        To use `nodemon`, you might need to install it globally or as a dev dependency (`npm install -D nodemon`).

4.  **Frontend Setup:**
    *   Navigate to the root directory of your project.
    *   If you haven't created the React app yet, create it using `npx create-react-app client` (assuming your frontend code is in a folder named `client`). If you have a `frontend` folder or a different name, adjust accordingly.
    *   Navigate to the frontend directory (`cd client`).
    *   Install the necessary frontend dependencies:
        ```bash
        npm install @mui/material @emotion/react @emotion/styled @mui/icons-material react-router-dom redux react-redux axios @reduxjs/toolkit
        ```
        This will install Material UI core components and styling utilities, Material UI icons, React Router for navigation, Redux and React-Redux for state management, Redux Toolkit to simplify Redux, and Axios for making API calls.

## Running the Application

1.  **Start the Backend Server:**
    *   Open a terminal, navigate to the `backend` directory (`cd backend`).
    *   Run the server using the `start` script defined in your `package.json`:
        ```bash
        npm start
        ```
        The backend server will likely start on a port you've defined in your `app.js` file (e.g., `http://localhost:5000`). You should see a message in the console indicating that the server is running and connected to the database.

2.  **Start the Frontend Development Server:**
    *   Open a new terminal, navigate to the frontend directory (`cd client`).
    *   Run the React development server:
        ```bash
        npm start
        ```
        This will typically start the frontend application in your browser at `http://localhost:3000`.

Now you should have both the backend API and the frontend application running, allowing you to use the movie booking application.

## API Endpoints (Examples)

While the specific endpoints might vary based on your exact implementation, here are some common examples based on the project's functionality:

*   `POST /api/user/signup`: Register a new user. (Assuming a base URL of `/api`).
*   `POST /api/user/login`: Log in an existing user and receive a JWT token [1].
*   `POST /api/admin/signup`: Register a new administrator.
*   `POST /api/admin/login`: Log in an existing administrator and receive a JWT token.
*   `GET /api/movies`: Get a list of all movies.
*   `POST /api/movies`: Add a new movie (requires admin authentication and a valid JWT token in the `Authorization` header as a Bearer token).
*   `DELETE /api/movies/:movieId`: Delete a specific movie (requires admin authentication).
*   `POST /api/bookings`: Create a new booking (requires user authentication).
*   `DELETE /api/bookings/:bookingId`: Delete a specific booking (requires user authentication).
*   `GET /api/users/:userId/bookings`: Get all bookings for a specific user.
*   `GET /api/admins/:adminId`: Get details of a specific administrator and the movies they have added.

**Note:** You might need to adjust these endpoints based on how you have defined your routes in the backend.

## Environment Variables

The application uses environment variables for configuration, such as:

*   **`MONGO_URI` (Backend `.env`):** The connection string for your MongoDB database.
*   **`JWT_SECRET` (Backend `.env`):** A secret key used to sign and verify JSON Web Tokens.

Ensure these variables are properly set in your `.env` file in the `backend` directory for the application to function correctly. **Do not commit your `.env` file to your repository if it contains sensitive information.**

## Further Development

This project provides a solid foundation for a movie booking application. Potential areas for further development include:

*   Implementing functionality to update movie details.
*   Adding seat selection during the booking process.
*   Implementing payment gateway integration for bookings.
*   Adding more detailed user and admin dashboards.
*   Implementing search and filtering options for movies.
*   Adding unit and integration tests.
*   Improving error handling and validation.
*   Optimising performance.
