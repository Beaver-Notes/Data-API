# Data-API
The DATA API in Beaver Notes enables third-party applications to interact with the platform. It provides functionalities for creating notes, deleting notes, and adding labels, allowing for efficient management and organization of information within Beaver Notes.

The Following documentation is related on how to use said API if you are looking on building a plugin for beaver notes using the Data API consider checkign out the [Beaver-API-playground](https://github.com/Beaver-Notes/Data-API).

## API Documentation

### Base URL
`http://localhost:3000`

### Authentication

#### Request Authentication

**Endpoint:** `POST /request-auth`

**Description:** Sends an authentication request to the renderer process in Electron.

**Request:**
- **Headers:** `Content-Type: application/json`
- **Body:**
  ```json
  {
    "platform": "your-platform",
    "id": "your-id"
  }
  ```

**Example `curl` Command:**
```bash
curl --location 'http://localhost:3000/request-auth' \
--header 'Content-Type: application/json' \
--data '{
    "platform": "your-platform",
    "id": "your-id"
}'
```

#### Verify Authentication

**Endpoint:** `GET /confirm-auth`

**Description:** Verifies the authentication token.

**Request:**
- **Headers:**
  - `Authorization: Bearer your-token`
  - `Content-Type: application/json`

**Example `curl` Command:**
```bash
curl --location --request GET 'http://localhost:3000/confirm-auth' \
--header 'Authorization: Bearer your-token' \
--header 'Content-Type: application/json' \
--data '{
    "platform": "your-platform",
    "id": "your-id"
}' 
```

### Notes Management

#### Add Note

**Endpoint:** `POST /add-note`

**Description:** Adds a new note and broadcasts it to all connected clients.

**Request:**
- **Headers:**
  - `Authorization: Bearer your-token`
  - `Content-Type: application/json`
- **Body:**
  ```json
  {
    "title": "Sample Note",
    "content": "This is a sample note content."
  }
  ```

**Example `curl` Command:**
```bash
curl --location 'http://localhost:3000/add-note' \
--header 'Authorization: Bearer your-token' \
--header 'Content-Type: application/json' \
--data '{
    "title": "Sample Note",
    "content": "This is a sample note content."
}'
```

#### Delete Note

**Endpoint:** `POST /delete-note`

**Description:** Deletes a note and broadcasts the deletion to all connected clients.

**Request:**
- **Headers:**
  - `Authorization: Bearer your-token`
  - `Content-Type: application/json`
- **Body:**
  ```json
  {
    "id": "note-id"
  }
  ```

**Example `curl` Command:**
```bash
curl --location 'http://localhost:3000/delete-note' \
--header 'Authorization: Bearer your-token' \
--header 'Content-Type: application/json' \
--data '{
    "id": "note-id"
}'
```

#### Add Label to Note

**Endpoint:** `POST /add-label`

**Description:** Adds a label to a note and broadcasts the update to all connected clients.

**Request:**
- **Headers:**
  - `Authorization: Bearer your-token`
  - `Content-Type: application/json`
- **Body:**
  ```json
  {
    "id": "note-id",
    "labelId": "label-id"
  }
  ```

**Example `curl` Command:**
```bash
curl --location 'http://localhost:3000/add-label' \
--header 'Authorization: Bearer your-token' \
--header 'Content-Type: application/json' \
--data '{
    "id": "note-id",
    "labelId": "label-id"
}'
```

