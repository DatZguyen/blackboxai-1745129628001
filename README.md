
Built by https://www.blackbox.ai

---

```markdown
# Tracking Link Website

## Project Overview

The Tracking Link Website is a Node.js application that allows users to create tracking links which can collect visitor location data. The application provides endpoints for creating these links, tracking visitor locations, and retrieving the stored visitor data. It also includes a simple web interface for users to create links and view the collected data on a map.

## Installation

To get started with the Tracking Link Website, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd tracking-link-website
   ```

2. **Install dependencies**:
   Make sure you have Node.js and npm installed. You can install the dependencies with:
   ```bash
   npm install
   ```

3. **Start the server**:
   Once the dependencies are installed, you can start the server by running:
   ```bash
   npm start
   ```

4. **Access the application**:
   Open your browser and go to `http://localhost:3000` to access the Tracking Link Website.

## Usage

1. **Create a Tracking Link**:
   Send a POST request to `/api/create-link` with a JSON body containing `redirectUrlAllowed` and `redirectUrlDenied` properties.

   Example:
   ```json
   {
     "redirectUrlAllowed": "https://allowed-url.com",
     "redirectUrlDenied": "https://denied-url.com"
   }
   ```

   This will return a JSON response with the generated `linkId` and tracking URL.

2. **Track Visitor Locations**:
   Send a POST request to `/api/track/:id` with the `id` parameter being the `linkId` returned when creating the link, along with the visitor's location data.

   Example:
   ```json
   {
     "lat": 34.0522,
     "lng": -118.2437,
     "permissionGranted": true
   }
   ```

   This will record the visitor's location if permission is granted.

3. **Retrieve Visitor Locations**:
   Send a GET request to `/api/locations/:id` with the `linkId` to retrieve all visitor locations associated with that tracking link.

## Features

- Create tracking links with allowed and denied redirect URLs.
- Log visitor locations with timestamps.
- Fetch stored visitor locations for each tracking link.
- Simple web interface for interaction.

## Dependencies

The project relies on the following dependencies, as specified in `package.json`:

- **express**: A web framework for Node.js, facilitating routing and handling of HTTP requests.
- **uuid**: A library for generating unique identifiers.

```json
"dependencies": {
  "express": "^4.18.2",
  "uuid": "^9.0.0"
}
```

## Project Structure

The project has the following structure:

```
tracking-link-website/
│
├── public/                # Contains static HTML files for the web interface
│   ├── index.html        # Main page for creating tracking links
│   ├── track.html        # Page for tracking links
│   └── map.html          # Page to display visitor locations on a map
│
├── package.json           # NPM manifest file
├── package-lock.json      # NPM lock file
└── server.js              # Main server file
```

In this structure, the `server.js` file contains the core logic for handling API requests and responses, including the creation of tracking links and logging visitor data.

## License

This project is licensed under the MIT License.
```