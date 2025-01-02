# OAuth 2.0 PKCE Authentication Example

This project demonstrates how to implement an **OAuth 2.0 Authorization Code Flow with PKCE (Proof Key for Code Exchange)** using Node.js and Express.

## Overview
The PKCE flow enhances the security of OAuth 2.0 by introducing a dynamically generated code verifier and code challenge, ensuring secure token exchanges for public clients like mobile apps or single-page applications.

## Features
- Generates `code_verifier` and `code_challenge` dynamically.
- Implements OAuth 2.0 endpoints for authorization and token exchange.
- Lightweight and simple to extend.

## Prerequisites
1. **Node.js** installed (v14 or higher recommended).
2. A registered client with an OAuth 2.0 Authorization Server.
3. Replace the placeholders in the code with your:
   - `client_id`
   - `redirect_uri`
   - Authorization and Token URLs.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/eversonsa/pkce-oauth-node.git
   cd oauth-pkce-node
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Update the configuration in `app.js`:
   - Replace `sua_client_id`, `https://seu-auth-server.com/authorize`, and `https://seu-auth-server.com/token` with your actual values.

4. Start the server:
   ```bash
   node app.js
   ```

## Usage
### Step 1: Start the Authentication Flow
Visit the `/auth` endpoint to begin the OAuth flow:
```bash
http://localhost:3000/auth
```
You will be redirected to the authorization server for user login and consent.

### Step 2: Handle the Redirect
After authorization, the server redirects to `/callback` with an `authorization_code`. The app automatically exchanges this code for an access token using the pre-generated `code_verifier`.

### Step 3: Receive the Access Token
The server responds with the access token JSON object, which can be used for API requests.

## Project Structure
```plaintext
.
├── app.js           # Main application logic
├── package.json     # Dependencies and scripts
└── README.md        # Documentation
```

## Dependencies
- **Express**: Web framework for handling routes.
- **Axios**: For making HTTP requests to the token endpoint.
- **Crypto**: For generating secure `code_verifier` and `code_challenge`.

## Security Considerations
- Always use HTTPS for communication to avoid man-in-the-middle attacks.
- PKCE is designed for public clients (like SPAs or mobile apps), ensuring the authorization code cannot be used by malicious actors without the `code_verifier`.

## Further Reading
- [OAuth 2.0 for Browser-Based Apps](https://oauth.net/2/browser-apps/)
- [RFC 7636: Proof Key for Code Exchange](https://datatracker.ietf.org/doc/html/rfc7636)

## License
This project is licensed under the MIT License. See [LICENSE](LICENSE) for more information.

## Contributing
Feel free to fork the repository, create a branch, and submit a pull request with your improvements or fixes!

