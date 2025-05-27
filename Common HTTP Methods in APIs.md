# Common HTTP Methods in APIs

1. GET
- Purpose: Retrieve data from the server.
- Example: GET /users/123 → fetch user with ID 123.
- Safe and idempotent (doesn’t change data).

2. POST
- Purpose: Send data to the server to create a new resource.
- Example: POST /users with a JSON body to create a new user.
- Not idempotent (repeating it creates multiple resources).

3. PUT
- Purpose: Update an existing resource or create it if it doesn’t exist.
- Example: PUT /users/123 with updated user data.
- Idempotent (repeating it has the same effect).

4. DELETE
- Purpose: Remove a resource from the server.
- Example: DELETE /users/123 → deletes user 123.
- Idempotent.

5. PATCH (Bonus!)
- Purpose: Partially update a resource.
- Example: PATCH /users/123 with just the fields to update.
