# Belay API Documentation

## Authentication

### Login

- **Endpoint:** `/api/login`
- **Method:** `POST`
- **Description:** Authenticate a user and return an API key.
- **Body:**
  - `user`: The username.
  - `pass`: The password.
- **Success Response:**
  - **Code:** 200
  - **Content:** `{'Success': True, 'user_id': '...', 'user_name': '...', 'api_key': '...'}`

### Sign Up

- **Endpoint:** `/api/signup`
- **Method:** `POST`
- **Description:** Create a new user account.
- **Body:**
  - `user`: Desired username.
  - `pass`: Desired password.
- **Success Response:**
  - **Code:** 200
  - **Content:** `{"Success": True, "api_key": "...", "user_name": "...", "user_id": "..."}`

## Users

### Update Username

- **Endpoint:** `/api/update_username`
- **Method:** `POST`
- **Description:** Update the username of an authenticated user.
- **Headers:**
  - `X-API-Key`: User's API key.
- **Body:**
  - `new_name`: The new username.
- **Success Response:**
  - **Code:** 200
  - **Content:** `{"success": True, "message": "Username updated successfully."}`

### Update Password

- **Endpoint:** `/api/update_password`
- **Method:** `POST`
- **Description:** Update the password of an authenticated user.
- **Headers:**
  - `X-API-Key`: User's API key.
- **Body:**
  - `new_password`: The new password.
  - `confirm_password`: Confirmation of the new password.
- **Success Response:**
  - **Code:** 200
  - **Content:** `{"success": True, "message": "Password updated successfully."}`

## Channels

### Create Channel

- **Endpoint:** `/api/create_channel`
- **Method:** `POST`
- **Description:** Create a new channel.
- **Headers:**
  - `X-API-Key`: User's API key.
- **Body:**
  - `channelName`: Name of the channel.
- **Success Response:**
  - **Code:** 201
  - **Content:** `{"Success": True, "channel": {...}}`

### Get Channels

- **Endpoint:** `/api/channels`
- **Method:** `GET`
- **Description:** Retrieve all channels.
- **Success Response:**
  - **Code:** 200
  - **Content:** `{"Success": True, "channels": [{...}, {...}]}`

## Messages

### Post Message

- **Endpoint:** `/api/channels/<channel_id>/messages/post`
- **Method:** `POST`
- **Description:** Post a new message to a channel.
- **Headers:**
  - `X-API-Key`: User's API key.
- **URL Parameters:**
  - `channel_id`: The ID of the channel.
- **Body:**
  - `userid`: The user's ID.
  - `content`: The message content.
- **Success Response:**
  - **Code:** 201
  - **Content:** `{'Success': 'Message posted successfully'}`

### Get Channel Messages

- **Endpoint:** `/api/channels/<channel_id>/messages`
- **Method:** `GET`
- **Description:** Get messages from a specific channel.
- **URL Parameters:**
  - `channel_id`: The ID of the channel.
- **Success Response:**
  - **Code:** 200
  - **Content:** `{"Success": True, "message": [{...}]}`

## Reactions

### Post Reaction

- **Endpoint:** `/api/reactions/post`
- **Method:** `POST`
- **Description:** Post a reaction to a message.
- **Headers:**
  - `X-API-Key`: User's API key.
- **Body:**
  - `user_id`: The user's ID.
  - `message_id`: The ID of the message.
  - `emoji`: The emoji used as a reaction.
- **Success Response:**
  - **Code:** 201
  - **Content:** `{'Success': 'Reaction posted successfully'}`

### Get Reaction Users

- **Endpoint:** `/api/reactions/<message_id>/<emoji>`
- **Method:** `GET`
- **Description:** Get the users who reacted to a message with a specific emoji.
- **URL Parameters:**
  - `message_id`: The ID of the message.
  - `emoji`: The emoji used for the reaction.
- **Success Response:**
  - **Code:** 200
  - **Content:** `{"Success": True, "users": [...]}`

## Unread Messages

### Mark Message as Seen

- **Endpoint:** `/api/channels/<channel_id>/messages/<max_id>/mark_seen`
- **Method:** `POST`
- **Description:** Mark a message as seen for a user in a specific channel.
- **Headers:**
  - `X-API-Key`: User's API key.
- **URL Parameters:**
  - `channel_id`: The ID of the channel.
  - `max_id`: The ID of the message to mark as seen.
- **Body:**
  - `user_id`: The user's ID.
- **Success Response:**
  - **Code:** 200
  - **Content:** `{'Success': True, 'message': 'Last read message updated'}`

### Get Unread Message Counts

- **Endpoint:** `/api/users/<user_id>/unread_message_counts`
- **Method:** `GET`
- **Description:** Get counts of unread messages for each channel for a user.
- **URL Parameters:**
  - `user_id`: The ID of the user.
- **Success Response:**
  - **Code:** 200
  - **Content:** `{"Success": True, "unread_message_counts": [{"channel_id": "...", "channel_name": "...", "unread_message_count": "..."}, ...]}`
