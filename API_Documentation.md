# API Documentation

## Base URL

The base URL for all event-related endpoints is:

```
{BASE_URL}/event
```

Replace `{BASE_URL}` with your application's actual base URL.

## EventController

### Endpoints

#### 1. Get All Events in a Period

**URL:** `GET /event`

**Description:** Retrieves all events within a specified period for the authenticated user.

**Query Parameters:**

- `startDate` (LocalDate, required): The start date of the period in the format `YYYY-MM-DD`.
- `dueDate` (LocalDate, required): The end date of the period in the format `YYYY-MM-DD`.

**Response:**

- **200 OK**: Returns a list of `EventResponse` objects.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the user does not exist.

**Example Request:**

```
axios.get(`${BASE_URL}/event`, {
  params: {
    startDate: "2024-01-01",
    dueDate: "2024-01-31"
  }
});
```

**Example Response:**

```
[
  {
    "id": 1,
    "title": "Event Title",
    "tag": { "id": 2, "title": "Work", "color": "#FF5733" },
    "hashtags": [{ "id": 3, "name": "Important" }],
    "description": "This is an event description",
    "startDateTime": "2024-01-01T09:00:00",
    "dueDateTime": "2024-01-01T10:00:00",
    "location": "Meeting Room"
  }
]
```

#### 2. Get Monthly Events

**URL:** `GET /event/month`

**Description:** Retrieves all events within a specific month for the authenticated user.

**Query Parameters:**

- `date` (LocalDate, required): A date within the month in the format `YYYY-MM-DD`.

**Response:**

- **200 OK**: Returns a list of `EventSummary` objects.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the user does not exist.

**Example Request:**

```
axios.get(`${BASE_URL}/event/month`, {
  params: {
    date: "2024-01-15"
  }
});
```

**Example Response:**

```
[
  {
    "id": 1,
    "title": "Event Title",
    "tagTitle": "Work",
    "tagColor": "#FF5733",
    "startDateTime": "2024-01-15T09:00:00",
    "dueDateTime": "2024-01-15T10:00:00"
  }
]
```

#### 3. Create an Event

**URL:** `POST /event/create`

**Description:** Creates a new event for the authenticated user.

**Request Body:**

- ```
  SaveEventRequest
  ```

   object containing:

  - `title` (string, required): The title of the event.
  - `tag` (Tag, optional): The tag associated with the event.
  - `hashtags` (Hashtag[], optional): A list of hashtags for the event.
  - `description` (string, optional): A description of the event.
  - `startDateTime` (LocalDateTime, optional): The start date and time of the event.
  - `dueDateTime` (LocalDateTime, optional): The due date and time of the event.
  - `location` (string, optional): The location of the event.

**Response:**

- **200 OK**: Returns the created `EventResponse` object.
- **403 Forbidden**: If the user is not authenticated.
- **400 Bad Request**: If the request body is invalid.

**Example Request:**

```
axios.post(`${BASE_URL}/event/create`, {
  title: "New Event",
  tag: { id: 2, title: "Work", color: "#FF5733" },
  hashtags: [{ id: 3, name: "Urgent" }],
  description: "Discuss quarterly results",
  startDateTime: "2024-01-20T09:00:00",
  dueDateTime: "2024-01-20T10:00:00",
  location: "Conference Room"
});
```

**Example Response:**

```
{
  "id": 1,
  "title": "New Event",
  "tag": { "id": 2, "title": "Work", "color": "#FF5733" },
  "hashtags": [{ "id": 3, "name": "Urgent" }],
  "description": "Discuss quarterly results",
  "startDateTime": "2024-01-20T09:00:00",
  "dueDateTime": "2024-01-20T10:00:00",
  "location": "Conference Room"
}
```

#### 4. Update an Event

**URL:** `PUT /event/update`

**Description:** Updates an existing event.

**Request Parameters:**

- `eventId` (Long, required): The ID of the event to be updated.

**Request Body:**

- `SaveEventRequest` object (see Create an Event).

**Response:**

- **200 OK**: Returns the updated `EventResponse` object.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the event or user does not exist.

**Example Request:**

```
axios.put(`${BASE_URL}/event/update`, {
  eventId: 1,
  title: "Updated Event",
  description: "Updated description",
  startDateTime: "2024-01-21T09:00:00",
  dueDateTime: "2024-01-21T10:00:00",
  location: "Updated Location"
});
```

**Example Response:**

```
{
  "id": 1,
  "title": "Updated Event",
  "tag": { "id": 2, "title": "Work", "color": "#FF5733" },
  "hashtags": [{ "id": 3, "name": "Urgent" }],
  "description": "Updated description",
  "startDateTime": "2024-01-21T09:00:00",
  "dueDateTime": "2024-01-21T10:00:00",
  "location": "Updated Location"
}
```

#### 5. Delete an Event

**URL:** `DELETE /event/delete`

**Description:** Deletes an event by its ID.

**Request Parameters:**

- `eventId` (Long, required): The ID of the event to be deleted.

**Response:**

- **200 OK**: If the event is successfully deleted.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the event or user does not exist.

**Example Request:**

```
axios.delete(`${BASE_URL}/event/delete`, {
  params: {
    eventId: 1
  }
});
```

**Example Response:**

```
{
  "status": 200,
  "message": "Event deleted successfully"
}
```

#### 6. Get an Event by ID

**URL:** `GET /event/{eventId}`

**Description:** Retrieves an event by its ID.

**Path Variables:**

- `eventId` (Long, required): The ID of the event to retrieve.

**Response:**

- **200 OK**: Returns the `EventResponse` object.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the event or user does not exist.

**Example Request:**

```
axios.get(`${BASE_URL}/event/1`);
```

**Example Response:**

```
{
  "id": 1,
  "title": "Event Title",
  "tag": { "id": 2, "title": "Work", "color": "#FF5733" },
  "hashtags": [{ "id": 3, "name": "Important" }],
  "description": "This is an event description",
  "startDateTime": "2024-01-01T09:00:00",
  "dueDateTime": "2024-01-01T10:00:00",
  "location": "Meeting Room"
}
```

#### 7. Get All Events for a User

**URL:** `GET /event/all`

**Description:** Retrieves all events for the authenticated user.

**Response:**

- **200 OK**: Returns a list of `EventResponse` objects.
- **403 Forbidden**: If the user is not authenticated.

**Example Request:**

```
axios.get(`${BASE_URL}/event/all`);
```

**Example Response:**

```
[
  {
    "id": 1,
    "title": "Event Title",
    "tag": { "id": 2, "title": "Work", "color": "#FF5733" },
    "hashtags": [{ "id": 3, "name": "Important" }],
    "description": "This is an event description",
    "startDateTime": "2024-01-01T09:00:00",
    "dueDateTime": "2024-01-01T10:00:00",
    "location": "Meeting Room"
  }
]
```

-----

## TagController

### Endpoints

#### 1. Save a New Tag

**URL:** `POST /api/tags`

**Description:** Creates a new tag for the authenticated user.

**Request Body:**

- ```
  SaveTagRequest
  ```

   object containing:

  - `title` (string, required): The title of the tag.
  - `color` (Color, required): The color associated with the tag.

**Response:**

- **200 OK**: Returns the created `TagResponse` object.
- **403 Forbidden**: If the user is not authenticated.
- **400 Bad Request**: If the request body is invalid.

**Example Request:**

```
axios.post(`${BASE_URL}/api/tags`, {
  title: "New Tag",
  color: { r: 255, g: 87, b: 51 }
});
```

**Example Response:**

```
{
  "id": 1,
  "title": "New Tag",
  "color": { "r": 255, "g": 87, "b": 51 }
}
```

#### 2. Get Tag by ID

**URL:** `GET /api/tags/{id}`

**Description:** Retrieves a tag by its ID.

**Path Variables:**

- `id` (Long, required): The ID of the tag to retrieve.

**Response:**

- **200 OK**: Returns the `TagResponse` object with the specified ID.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the tag with the specified ID does not exist.

**Example Request:**

```
axios.get(`${BASE_URL}/api/tags/1`);
```

**Example Response:**

```
{
  "id": 1,
  "title": "Work",
  "color": { "r": 255, "g": 87, "b": 51 }
}
```

#### 3. Get All Tags for the Authenticated User

**URL:** `GET /api/tags`

**Description:** Retrieves all tags associated with the authenticated user.

**Response:**

- **200 OK**: Returns a list of `TagResponse` objects.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the user does not exist.

**Example Request:**

```
axios.get(`${BASE_URL}/api/tags`);
```

**Example Response:**

```
[
  {
    "id": 1,
    "title": "Work",
    "color": { "r": 255, "g": 87, "b": 51 }
  },
  {
    "id": 2,
    "title": "Personal",
    "color": { "r": 51, "g": 102, "b": 255 }
  }
]
```

#### 4. Update a Tag by ID

**URL:** `PUT /api/tags/{id}`

**Description:** Updates an existing tag by its ID.

**Path Variables:**

- `id` (Long, required): The ID of the tag to update.

**Request Body:**

- `SaveTagRequest` object (see Save a New Tag).

**Response:**

- **200 OK**: Returns the updated `TagResponse` object.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the tag with the specified ID does not exist.

**Example Request:**

```
axios.put(`${BASE_URL}/api/tags/1`, {
  title: "Updated Tag",
  color: { r: 51, g: 153, b: 102 }
});
```

**Example Response:**

```
{
  "id": 1,
  "title": "Updated Tag",
  "color": { "r": 51, "g": 153, "b": 102 }
}
```

#### 5. Delete a Tag by ID

**URL:** `DELETE /api/tags/{id}`

**Description:** Deletes a tag by its ID.

**Path Variables:**

- `id` (Long, required): The ID of the tag to delete.

**Response:**

- **204 No Content**: If the tag is successfully deleted.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the tag with the specified ID does not exist.

**Example Request:**

```
axios.delete(`${BASE_URL}/api/tags/1`);
```

-----

## HashtagController

### Endpoints

#### 1. Create a New Hashtag

**URL:** `POST /hashtags`

**Description:** Creates a new hashtag for the authenticated user.

**Request Body:**

- 

  ```
  SaveHashtagRequest
  ```

   object containing:

  - `title` (string, required): The title of the hashtag.

**Response:**

- **200 OK**: Returns the created `HashtagResponse` object.
- **403 Forbidden**: If the user is not authenticated.
- **400 Bad Request**: If the request body is invalid.

**Example Request:**

```
axios.post(`${BASE_URL}/hashtags`, {
  title: "NewHashtag"
});
```

**Example Response:**

```
{
  "id": 1,
  "title": "NewHashtag"
}
```

#### 2. Get Hashtag by ID

**URL:** `GET /hashtags/{id}`

**Description:** Retrieves a hashtag by its ID.

**Path Variables:**

- `id` (Long, required): The ID of the hashtag to retrieve.

**Response:**

- **200 OK**: Returns the `HashtagResponse` object with the specified ID.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the hashtag with the specified ID does not exist.

**Example Request:**

```
axios.get(`${BASE_URL}/hashtags/1`);
```

**Example Response:**

```
{
  "id": 1,
  "title": "Important"
}
```

#### 3. Get All Hashtags for a User

**URL:** `GET /hashtags`

**Description:** Retrieves all hashtags associated with the authenticated user.

**Response:**

- **200 OK**: Returns a list of `HashtagResponse` objects.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the user does not exist.

**Example Request:**

```
axios.get(`${BASE_URL}/hashtags`);
```

**Example Response:**

```
[
  {
    "id": 1,
    "title": "Important"
  },
  {
    "id": 2,
    "title": "Work"
  }
]
```

#### 4. Update a Hashtag by ID

**URL:** `PUT /hashtags/{id}`

**Description:** Updates an existing hashtag by its ID.

**Path Variables:**

- `id` (Long, required): The ID of the hashtag to update.

**Request Body:**

- `SaveHashtagRequest` object (see Create a New Hashtag).

**Response:**

- **200 OK**: Returns the updated `HashtagResponse` object.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the hashtag with the specified ID does not exist.

**Example Request:**

```
axios.put(`${BASE_URL}/hashtags/1`, {
  title: "UpdatedHashtag"
});
```

**Example Response:**

```
{
  "id": 1,
  "title": "UpdatedHashtag"
}
```

#### 5. Delete a Hashtag by ID

**URL:** `DELETE /hashtags/{id}`

**Description:** Deletes a hashtag by its ID.

**Path Variables:**

- `id` (Long, required): The ID of the hashtag to delete.

**Response:**

- **204 No Content**: If the hashtag is successfully deleted.
- **403 Forbidden**: If the user is not authenticated.
- **404 Not Found**: If the hashtag with the specified ID does not exist.

**Example Request:**

```
javascript
코드 복사
axios.delete(`${BASE_URL}/hashtags/1`);
```

------
