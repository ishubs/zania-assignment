# Running the Project

To run the project, follow these steps:

1. Build and start the Docker containers:
    ```bash
    docker-compose up --build
    ```

2. Navigate to [http://localhost:5173](http://localhost:5173) in your web browser.

# API Design

## GET Request for Retrieving Docs

- Implemented a handler for GET requests to the `/docs` endpoint.
- Logic was added to check if documents were stored in the local storage.
- If no documents were found, initialized them with default data and stored them locally.
- Returned the documents as a JSON response.

## PUT Request for Updating Docs

- Set up a handler for PUT requests to the `/update-docs` endpoint.
- Updated documents in the local storage with new data provided in the request payload.
- If the documents are large, only the object specifying the source and destination ID of the drag and drop transaction can be sent over the API call, and the rest of the logic can be implemented on the backend to sync the data.
- Returned the updated documents as a JSON response.

## Endpoints

- **GET /docs**:
  - Retrieve all documents.
  - This endpoint will return a list of all documents currently stored.
  
- **POST /docs**:
  - Add a new document.
  - Allows clients to add a new document. The request body should contain the details of the new document to be added.

- **PUT /update-docs**:
  - Updates the positions of current docs.
  - Allow clients to save the updated positions of the docs. The request body can contain the entire array of docs or only the specific occurred transactions depending on the size of the document JSON.

- **DELETE /docs/:id**:
  - Remove a document.
  - This endpoint will allow clients to delete a document identified by its ID.

## Error Handling

- error handling to handle scenarios such as invalid requests, missing data, or failed database operations.
- Return appropriate HTTP status codes and error messages to indicate the outcome of each request.

## Authentication and Authorization

- Mechanisms to ensure that only authorized users can perform CRUD operations on documents.
- Implementing role-based access control to restrict access to certain endpoints based on user roles or permissions.

## Versioning

- Versioning the API to allow for future updates and changes without breaking existing client implementations.
- Use semantic versioning or another versioning scheme to clearly communicate changes and ensure compatibility with client applications.

