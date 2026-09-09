# Freelancer Matching System

A backend application that helps recruiters find suitable freelancers by matching project requirements with freelancer skills, experience, budget, and ratings.

## Overview

The Freelancer Matching System is built using **Node.js, Express.js, and MySQL**. It provides REST APIs for user authentication, freelancer profiles, recruiter profiles, project creation, skill management, and automated freelancer matching.

The project demonstrates how database concepts can be integrated with backend development to solve a real-world recruitment problem.

## Features

### Authentication

* User registration
* User login
* Freelancer and recruiter roles
* Password hashing using bcrypt

### Freelancer Module

* Create freelancer profiles
* Update freelancer information
* Add skills
* Automatically create a skill if it does not already exist
* View freelancer details

### Recruiter Module

* Create recruiter profiles
* Create projects
* Add required project skills

### Matching Engine

* Generate matches for a project
* Calculate matching scores
* Rank freelancers
* Return the top matching candidates
* Store matching results in the database

### Database Integration

* MySQL database
* Relational database design
* Primary and foreign keys
* Stored procedures
* Triggers
* Views
* Joins
* Aggregation
* Indexing

## Tech Stack

| Technology | Purpose                         |
| ---------- | ------------------------------- |
| Node.js    | Backend runtime                 |
| Express.js | REST API development            |
| MySQL      | Database management             |
| JavaScript | Backend programming             |
| bcrypt     | Password hashing                |
| dotenv     | Environment variable management |
| CORS       | Cross-origin request handling   |

## Project Structure

```text
skill-match-project-main/
│
├── server.js          # Express server and API routes
├── db.js              # MySQL connection pool
├── package.json       # Project dependencies and scripts
├── package-lock.json  # Dependency lock file
├── .env               # Database configuration
└── README.md          # Project documentation
```

## How the System Works

```text
User Registration
       ↓
Freelancer / Recruiter Profile
       ↓
Recruiter Creates Project
       ↓
Project Requirements Added
       ↓
Matching Engine Runs
       ↓
Freelancers Ranked
       ↓
Matching Results Returned
```

## Main Matching Procedure

The backend calls the MySQL stored procedure:

```sql
generate_project_matches
```

The procedure is responsible for generating matching results for a project. The backend then retrieves the ranked freelancers and returns their names and matching scores.

## API Endpoints

### Authentication

| Method | Endpoint             | Description     |
| ------ | -------------------- | --------------- |
| POST   | `/api/auth/register` | Register a user |
| POST   | `/api/auth/login`    | Login a user    |

### Freelancer

| Method | Endpoint                          | Description                 |
| ------ | --------------------------------- | --------------------------- |
| POST   | `/api/freelancer/create`          | Create a freelancer profile |
| PUT    | `/api/freelancer/update/:id`      | Update freelancer details   |
| POST   | `/api/freelancer/add-skill`       | Add a skill                 |
| POST   | `/api/freelancer/add-skill-smart` | Add or create a skill       |
| GET    | `/api/freelancer/:userId`         | Fetch freelancer details    |
| GET    | `/api/freelancer/by-user/:userId` | Fetch freelancer by user ID |

### Recruiter

| Method | Endpoint                 | Description                |
| ------ | ------------------------ | -------------------------- |
| POST   | `/api/recruiter/profile` | Create a recruiter profile |

### Projects

| Method | Endpoint                 | Description                   |
| ------ | ------------------------ | ----------------------------- |
| POST   | `/api/project/create`    | Create a project              |
| POST   | `/api/project/add-skill` | Add required project skills   |
| GET    | `/api/project/:id/match` | Generate and retrieve matches |

### Additional

| Method | Endpoint           | Description                          |
| ------ | ------------------ | ------------------------------------ |
| GET    | `/api/health`      | Check server and database connection |
| GET    | `/api/freelancers` | Retrieve freelancer dashboard data   |
| GET    | `/api/projects`    | Retrieve projects                    |

## Installation

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd skill-match-project-main
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a `.env` file in the project root:

```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=your_database_name
PORT=5000
```

Replace the database values with your own MySQL configuration.

### 4. Start the Server

```bash
npm start
```

The server will run on:

```text
http://localhost:5000
```

## Database Requirements

The application requires a MySQL database containing the tables and database objects used by the backend, including:

* `users`
* `freelancer_profile`
* `recruiter_profile`
* `skill`
* `freelancer_skill`
* `project`
* `project_required_skill`
* `match_result`
* `trending_skills`

The matching functionality also requires the stored procedure:

```sql
generate_project_matches
```

**Note:** The SQL schema and database setup script are not included in the current uploaded project files. Add them to the repository if you want others to run the project easily.

## Future Improvements

* JWT-based authentication
* Frontend dashboard
* Advanced matching algorithms
* AI-powered freelancer recommendations
* Real-time notifications
* Admin dashboard
* Improved profile management


