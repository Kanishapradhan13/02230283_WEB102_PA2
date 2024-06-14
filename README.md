To install dependencies:
```sh
bun install
```

To run:
```sh
bun run dev
```

open http://localhost:3000


## API Endpoints
1. User Registration
Endpoint: POST /register

Registers a new user with an email and password.

URL: http://localhost:3000/register
Method: POST
Headers: Content-Type: application/json
Body:

  {
    "email": "user@example.com",
    "hashedpassword": "asdfgh345dfg"
  }

Response:

Success:

  {
    "message": "user@example.com created successfully"
  }
  
Error (Email already exists):

  {
    "message": "Email already exists"
  }
  
2. User Login
Endpoint: POST /login

Authenticates a user and returns a JWT token.

URL: http://localhost:3000/login
Method: POST
Headers: Content-Type: application/json
Body:

  {
    "email": "user@example.com",
    "password": "asdfg1234rtyu"
  }
  
Response:

Success:

  {
    "message": "Login successful",
    "token": "your_jwt_token"
  }
  
Error (User not found):

  {
    "message": "User not found"
  }
  
Error (Invalid credentials):

  {
    "message": "Invalid credentials"
  }
  
3. Get Pokémon Details
Endpoint: GET /pokemon/:name

Fetches details of a specified Pokémon from an external API.

URL: http://localhost:3000/pokemon/{name}
Method: GET
Headers: None
Path Variable: name - Name of the Pokémon (e.g., pichu)
Response:

Success:

{
  "data": { "name": "pichu", ... }
}

Error (Pokémon not found):

{
  "message": "Your Pokémon was not found!"
}

4. Catch a Pokémon
Endpoint: POST /protected/catch

Saves a Pokémon to the user's caught list. Requires JWT authentication.

URL: http://localhost:3000/protected/catch
Method: POST
Headers:
Content-Type: application/json
Authorization: Bearer your_jwt_token
Body:

  {
    "name": "pikachu"
  }
  
Response:

Success:

  {
    "message": "Pokemon caught",
    "data": { "userId": "1", "pokemonId": "25" }
  }
  
Error (Unauthorized):

  {
    "message": "YOU ARE UNAUTHORIZED"
  }
  
5. Release a Pokémon
Endpoint: DELETE /protected/release/:id

Releases a Pokémon from the user's caught list. Requires JWT authentication.

URL: http://localhost:3000/protected/release/{id}
Method: DELETE
Headers:
Authorization: Bearer your_jwt_token
Path Variable: id - ID of the caught Pokémon

Response:

Success:

  {
    "message": "Pokemon is released"
  }
  
Error (Not found or not owned):

  {
    "message": "Pokemon not found or not owned by user"
  }
  
6. List Caught Pokémon
Endpoint: GET /protected/caught

Retrieves the list of Pokémon caught by the authenticated user. Requires JWT authentication.

URL: http://localhost:3000/protected/caught
Method: GET
Headers:
Authorization: Bearer your_jwt_token

Response:

Success:

  {
    "data": [{ "id": "1", "name": "pikachu", ... }]
  }
  
Error (Unauthorized):

  {
    "message": "YOU ARE UNAUTHORIZED"
  }
  


