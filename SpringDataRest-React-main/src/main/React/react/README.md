# Voiture App

This project consists of two parts: a **React** front-end and a **Spring Boot** back-end. Both parts are Dockerized and can be built, pushed, and run using Docker. Below are the steps to build the image of frontend part.

## Frontend: Voiture App (React)

### Prerequisites

- [Node.js](https://nodejs.org/) installed (recommended version: 18.x or above)
- [Docker](https://www.docker.com/get-started) installed
- [GitHub account](https://github.com/) for pushing the code

### Setup and Build Steps

1. **Clone the Repository**

   Clone the repository from GitHub and move into the project directory:
  - git clone https://github.com/ChakraHs/voiture-react.git
  - cd voiture-react

2. **Build Docker Image**

Build the Docker image for the front-end:
- docker build -t voiture-app-frontend .
