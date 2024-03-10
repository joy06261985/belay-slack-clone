# Belay - A Slack Clone

## Introduction

Belay is a capstone project for Web Development, aimed at creating a modern, database-backed single-page application that functions similarly to Slack. This application allows users to send and receive real-time chat messages organized into channels, along with other features like message threading and emoji reactions.

## Getting Started

### Prerequisites

- Python 3.11+
- Flask
- SQLite3

### Installation

1. Clone the repository to your local machine
   ```
   git clone https://github.com/joy06261985/belay-slack-clone.git
   cd belay-slack-clone
   ```
2. Install the required dependencies
   ``` bash
   pip3 install -r requirements.txt
   ```
   
### Running the Application  
1. Start the Flask application:
   ``` bash
   flask run
   ```
2. Access the application via your web browser at the URL outputted by Flask, typically
   `http://127.0.0.1:5000/`

## Getting Started
- Unauthenticated UI: Allows new account creation and user sign-in.
- Authenticated UI: Supports various user activities like logging out, changing username/password, viewing channels, and messaging.
- Single-Page State: Maintains state without requiring page reloads, enhancing user experience.
- Responsive Styling: Adapts to different screen sizes for a consistent user experience across devices.
- Database Integration: Utilizes SQLite3 for data storage, ensuring persistent and organized data management.
- API Endpoints: Provides a structured and secure way for the front-end to communicate with the server.
