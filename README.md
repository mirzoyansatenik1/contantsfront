# contantsfront

A minimal single-file front-end for a simple contacts app.

This repository contains a lightweight UI (`index.html`) that lets a user register/login and create, edit, list, and delete contacts. The front-end is intentionally minimal — everything is in one HTML file with inline styles and JavaScript for easy editing and quick demos.

How to run the front-end locally

1. Open the `index.html` file in your browser. For some browser features (fetch to `http://localhost:3000`) you may need to serve it over HTTP rather than the `file://` protocol.

	 A quick way to serve the file locally (Python 3):

	 ```bash
	 cd /path/to/contantsfront
	 python3 -m http.server 8080
	 # then open http://localhost:8080 in your browser
	 ```

API contract (what the UI expects)

The UI expects an API available at `http://localhost:3000` with these endpoints:

- POST /auth/register  { email, password } -> 201 on success
- POST /auth/login     { email, password } -> { token }
- GET /contacts        (auth) -> [ { id, name, phone, email } ]
- POST /contacts       (auth) -> create contact
- PUT /contacts/:id    (auth) -> update contact
- DELETE /contacts/:id (auth) -> delete contact

Auth: send header `Authorization: Bearer <token>` (token from login)

Notes

- The repo currently only contains the front-end (`index.html`). If you'd like, I can:
	- split CSS/JS into separate files,
	- add a small static dev server configuration,
	- or scaffold a minimal backend server that implements the endpoints above (in-memory for dev).
- If you plan to publish this publicly, consider moving secrets and persistent storage to a proper backend.

Contributing

Open a PR or create an issue if you want features, the server scaffold, or a rewrite in your preferred tooling.
