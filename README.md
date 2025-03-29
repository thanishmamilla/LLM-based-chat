# Chat API

This repository contains a FastAPI-based backend for fetching user chats, summarizing chat conversations, storing chats, deleting chats, and displaying chat history. Other chat-related functionalities are available at [ChatRepo API](https://chatrepo-bza8.onrender.com/).



THE FRONTEND GITHUB REPO IS :-    https://github.com/thanishmamilla/streamlit_chat (THE PUBLIC URL)
THE BACKEND IS RUNNING ON :-      https://chatrepo-bza8.onrender.com/

## Features

### 1. Store a Single Chat
Allows storing an individual chat in the database.
```http
POST /
```
#### Request Body:
```json
{
    "conversation_id": "12345",
    "user_id": "user_1",
    "messages": [
        {"sender": "user_1", "message": "Hello!", "timestamp": "2025-03-29T10:00:00Z"},
        {"sender": "user_2", "message": "Hi there!", "timestamp": "2025-03-29T10:01:00Z"}
    ]
}
```
#### Response:
```json
{
    "message": "Chat stored successfully",
    "id": "unique_chat_id"
}
```

### 2. Bulk Insert Chats
Allows storing multiple chats at once.
```http
POST /bulk
```
#### Request Body:
```json
[
    {
        "conversation_id": "12345",
        "user_id": "user_1",
        "messages": [...]
    },
    {
        "conversation_id": "12346",
        "user_id": "user_2",
        "messages": [...]
    }
]
```
#### Response:
```json
{
    "message": "Bulk chats stored",
    "inserted_ids": ["id1", "id2"]
}
```

### 3. Fetch Chat by Conversation ID
Retrieve a specific chat using its conversation ID.
```http
GET /{conversation_id}
```
#### Response:
```json
{
    "conversation_id": "12345",
    "user_id": "user_1",
    "messages": [...]
}
```

### 4. Summarize Chat Conversation
Generates a summary of a chat conversation.
```http
POST /chats/summarize
```
#### Request Body:
```json
{
    "conversation_id": "12345"
}
```
#### Response:
```json
{
    "conversation_id": "12345",
    "summary": "User 1 and User 2 greeted each other."
}
```

### 5. Get User Chat History (Paginated)
Fetch paginated chat history for a user.
```http
GET /{user_id}/chats?page=1&limit=10
```
#### Response:
```json
{
    "page": 1,
    "limit": 10,
    "data": [...]
}
```

### 6. Soft Delete a Chat
Marks a chat as deleted without permanently removing it.
```http
DELETE /{conversation_id}
```
#### Response:
```json
{
    "message": "Chat marked as deleted"
}
```

## Frontend - Streamlit UI
A simple Streamlit-based frontend is available to interact with the API.

### Features:
- **Store a Single Chat**: Add a new chat to the database.
- **Fetch a Single Chat**: Enter a conversation ID and retrieve chat details.
- **Summarize a Chat**: Generate a summary for a given chat conversation.
- **Fetch User's Chat History**: Retrieve paginated chat history for a user.
- **Soft Delete a Chat**: Mark a chat as deleted.

### Installation and Usage
1. Install dependencies:
   ```sh
   pip install streamlit requests
   ```
2. Run the Streamlit app:
   ```sh
   streamlit run app.py
   ```
3. Interact with the UI to fetch, store, summarize, and delete chats.

## Additional API Features
For storing chats, bulk insertion, soft deleting, and other operations, visit [ChatRepo API](https://chatrepo-bza8.onrender.com/).

## Setup Instructions
1. Clone the repository:
   ```sh
   git clone https://github.com/your-repo.git
   ```
2. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
3. Run the FastAPI server:
   ```sh
   uvicorn main:app --reload
   ```
4. Access the API documentation at:
   ```
   http://127.0.0.1:8000/docs
   ```

## License
This project is licensed under the MIT License.

