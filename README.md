# db-system

Web application for creating and managing databases and tables. Each table gets a REST API for CRUD operations, secured with its own access token.

## Features

- Registration and login with JWT authentication
- Create, edit and delete databases
- Create, edit and delete tables, columns and constraints
- Change column types and constraints
- Database access tokens with a configurable lifetime, separate from UI login tokens
- REST API for creating, reading, updating and deleting rows in any created table

Planned: custom queries, more column types and constraint options.

## Tech stack

| Layer | Technology |
| --- | --- |
| Backend | Java 21, Spring Boot 3, Spring Security, JPA |
| Frontend | Angular 17, Bootstrap 5 |
| Database | InterSystems IRIS |
| Cache | Redis |
| Auth | JWT (UI tokens and database access tokens) |
| Deployment | Docker Compose |

## Project structure

```
server/   Spring Boot API
client/   Angular application
docker-compose.yml
```

## Running

Requires Docker.

```
docker-compose up --build
```

| Service | Address |
| --- | --- |
| Client | http://localhost:4200 |
| Server | http://localhost:8080 |
| IRIS management portal | http://localhost:9092 |

## Data API

After creating a database and a table, create an access token for the database in the UI. Send it as a bearer token to the data endpoints:

| Method | Endpoint | Action |
| --- | --- | --- |
| GET | `/queries/{table}/getAll` | List all rows |
| GET | `/queries/{table}/getByColumn` | Find rows matching a condition |
| POST | `/queries/{table}/save` | Insert a row |
| PUT | `/queries/{table}/update` | Update rows matching a condition |
| DELETE | `/queries/{table}/delete` | Delete rows matching a condition |

## License

MIT
