## Building Your Full Stack App: A Logical Sequence

### 1. Project Planning & Setup 

**Reason**: A solid foundation prevents rework later.

- You've already set up your project structure (React frontend, Node backend, Prisma/PostgreSQL)
- You've identified the external API (Spoonacular) and mapped out basic functionality

### 2. Set Up Environment & Configuration

**Reason**: Proper configuration early saves debugging headaches later.

- Complete your `.env` file with database credentials and Spoonacular API key
- Set up environment variables for different environments (development/production)
- Configure CORS to allow frontend/backend communication

### 3. Database Schema Design with Prisma

**Reason**: The database structure determines how your data will flow.

- Design your `schema.prisma` file for user data and favorites storage
- Run migrations to create your database tables
- This is like laying the foundation of a house before building walls

### 4. Backend API Development

**Reason**: Backend first enables testing your data flow before worrying about UI.

- Create API routes matching your diagram (`/api/recipes/search`, etc.)
- Build controllers to handle business logic
- Implement middleware for authentication (if needed)
- Add services to interact with the Spoonacular API
- Test your endpoints with a tool like Postman before connecting to frontend

### 5. Frontend Structure & State Management

**Reason**: Planning your UI structure before implementation clarifies data needs.

- Set up your React component hierarchy
- Decide on state management approach (context API, Redux, etc.)
- Create API service files to interact with your backend

### 6. Core Frontend Components

**Reason**: Building the essential UI elements first delivers value quicker.

- Implement search functionality
- Create recipe listing components
- Build recipe detail view
- This is like building the essential rooms of a house before adding decorations

### 7. User Authentication (Optional)

**Reason**: Add this after core functionality works to avoid complexity upfront.

- Implement login/signup if needed
- Create protected routes
- Connect user profiles to favorites

### 8. Favorites Functionality

**Reason**: This builds on core functionality and connects frontend to backend.

- Create UI for saving favorites
- Implement backend storage of favorites
- Build favorites retrieval and display

### 9. Error Handling & Edge Cases

**Reason**: Robust applications handle failures gracefully.

- Add loading states
- Implement error boundaries
- Handle API failures
- Deal with offline scenarios if applicable

### 10. Testing

**Reason**: Testing ensures functionality works across different scenarios.

- Unit tests for key functions
- Integration tests for API routes
- UI testing for critical user flows

### 11. Styling & UI Polish

**Reason**: Focusing on polish after functionality ensures a usable product first.

- Apply consistent styling with your CSS/Tailwind
- Add animations and transitions
- Ensure responsive design
- Implement accessibility features

### 12. Deployment

**Reason**: Getting your app to production is the ultimate goal.

- Deploy backend to a hosting service (Heroku, Render, etc.)
- Deploy frontend (Vercel, Netlify, etc.)
- Set up your PostgreSQL database in production
- Configure environment variables in production

This sequence works like building a house: first the foundation (database/backend), then the structure (core functionality), followed by walls and rooms (UI components), and finally the paint and decorations (styling and polish). Each phase builds upon the previous one, making the process more manageable.

## Steps to building the project:

This is a guide to setup a new Full stack Project using the following stack:
- FrontEnd: 
	- TypeScript
	- React
	- TailwindCSS
- Backend
	- TypeScript
	- Express.js
	- Prisma ORM
	- PostgreSQL

**For reference, the project is called 'my-project'**

- Step 1: First, let's verify the existing structure and create our basic folder organisation. Navigate to your 'my-project' directory and create the following base folders:

	- frontend (for the React app)
	- backend (for the Express app)
	- shared (for shared types/utilities)
- Step 2: Let's set up the frontend structure. Inside the frontend folder, create the following structure:

- src/
    - components/ (for React components)
    - pages/ (for page components)
    - api/ (for API client code)
    - hooks/ (for custom React hooks)
    - utils/ (utility functions)
    - types/ (TypeScript interfaces/types)
    - assets/ (for images, icons, etc.)
    - styles/ (for CSS/Tailwind customisations)
    
- Step 3: Inside the backend folder, create the following structure:
	- src/
	    - controllers/ (for route handlers)
	    - routes/ (API route definitions)
	    - services/ (business logic)
	    - models/ (data models, will work with Prisma)
	    - middleware/ (Express middleware)
	    - utils/ (utility functions)
	    - types/ (TypeScript interfaces/types)
	    - config/ (configuration files)

- Step 4 (adjusted): Let's initialise the Prisma configuration for the backend:
	1. Navigate to the backend directory
	2. Run `pnpm add prisma @prisma/client`
	3. Initialise Prisma with `npx prisma init`

This will create a prisma directory with a schema.prisma file and update your .env file with a DATABASE_URL variable.

Step 5: Configure the Prisma schema for our database models according to the functionality needed.

1. Open the `backend/prisma/schema.prisma` file
2. Define the models we need based on the architecture diagram

Step 6: Let's create the main Express application file:

1. Create a file named `index.ts` in the root of your backend directory
2. This file will:
    - Import and configure Express
    - Set up middleware (CORS, JSON parsing, etc.)
    - Connect to the database using Prisma
    - Import and use route handlers
    - Start the server on a specified port

Think of this file as the central nervous system of your backend – it coordinates all the different parts and makes sure they work together smoothly, similar to how a conductor leads an orchestra.

For the routes and controllers, here's what you should plan for based on your architecture diagram:

- Routes for recipe search (connecting to Spoonacular API)
- Routes for recipe details
- Routes for managing favorites (GET, POST, DELETE operations)

Set up the Express server configuration in your index.ts file. Express is like the traffic controller for your backend application - it decides what happens to incoming requests and routes them to the right destinations.

A few additional packages are imported and their usage is listed below: 

1. **`dotenv`** is a package that loads environment variables from a `.env` file into `process.env`, making those variables available to your application.

	It's required because:

	1. It keeps sensitive information secure - things like database connection strings, API keys (like your Spoonacular API key), and other secrets shouldn't be hardcoded in your source files
	2. It allows for different configurations in different environments - you can have different database URLs or API endpoints for development vs. production
	3. It simplifies configuration management - instead of hardcoding values that might change, you keep them in one centralised `.env` file

	Think of `.env` files like a control panel for your application. Instead of having settings scattered throughout your codebase, you keep all the adjustable knobs and switches in one place where they're easy to find and modify.

	Without `dotenv`, you'd have to manually set environment variables on your system or directly access `process.env` variables that might not be defined, making your application less portable and harder to configure.

2. **@types/express** and **@types/cors** adds type casting for express and cors  
3. CORS (Cross origin Resource Sharing) package: CORS (**Cross-Origin Resource Sharing**) is a security mechanism built into **browsers** that controls how resources (e.g., APIs, fonts, images) can be requested from a different **origin** (domain, protocol, or port). By default, **browsers block cross-origin requests** for security reasons. CORS allows **servers** to specify which origins are permitted to access their resources.  

**Why is CORS required?** 
Imagine you have:  
1️⃣ A **frontend** running at `http://frontend.com`  
2️⃣ A **backend API** running at `http://api.backend.com`

If your frontend tries to **fetch data** from the backend:
```javascript
fetch("http://api.backend.com/users")
  .then((res) => res.json())
  .then((data) => console.log(data))
  .catch((err) => console.error(err));
```

The **browser** blocks this request because it's a **cross-origin request**!
```terminal
Access to fetch at 'http://api.backend.com/users' from origin 'http://frontend.com' has been blocked by CORS policy.

```

🔴**Without CORS**, JavaScript running in the browser cannot fetch data from a different domain.

✅ **With CORS**, the backend explicitly allows specific origins to access its resources.
## **When is CORS Required?**

CORS is needed **only when the request is made from a browser** using JavaScript (like `fetch` or `XMLHttpRequest`).

|Request Type|CORS Needed?|
|---|---|
|Same-origin request (`frontend.com` → `frontend.com`)|❌ No|
|Different origin request (`frontend.com` → `api.backend.com`)|✅ Yes|
|Request from **Postman or Curl**|❌ No|
|Request from **server to server**|❌ No|

---

## **How Does CORS Work?**

CORS works by adding special **HTTP headers** in the server's response.

### **Example CORS Headers**

When a browser makes a **cross-origin request**, the backend responds with:


```http
`Access-Control-Allow-Origin: http://frontend.com
Access-Control-Allow-Methods: GET, POST
Access-Control-Allow-Headers: Content-Type`
```

✅ This tells the browser:  
✔ **Allow requests from `http://frontend.com`**  
✔ **Allow only `GET` and `POST` methods**  
✔ **Allow headers like `Content-Type`**

---
## Creating a separate port for backend Express server 
The port 3001 in this line of code is for your backend Express server, not the frontend.

Your setup will have two separate servers running during development:

1. The frontend Vite server on port 5173
2. The backend Express server on port 3001

This is a common setup for full-stack development. Your React frontend will make API calls to your Express backend using the backend's URL ([http://localhost:3001](http://localhost:3001)). They run as separate processes, with the frontend making HTTP requests to the backend.

In production, you might deploy them differently, but during development, having them on separate ports allows you to work on them independently while still allowing them to communicate with each other.

To make API calls from your frontend to your backend, you'll configure your frontend API client to point to the backend URL.



Here's how to set up your index.ts file:

```typescript
// Import necessary dependencies
import express from 'express';
import cors from 'cors';
import { PrismaClient } from '@prisma/client';
import dotenv from 'dotenv';

// Import routes (you'll create these later)
// import recipeRoutes from './routes/recipes';
// import favoriteRoutes from './routes/favorites';

// Initialize configuration
dotenv.config();
const app = express();
const prisma = new PrismaClient();
const PORT = process.env.PORT || 3001;

// Set up middleware
app.use(cors()); // Allows frontend to communicate with backend
app.use(express.json()); // Parses incoming JSON requests

// Simple test route to verify server is running
app.get('/', (req, res) => {
  res.send('Foodilicious API is running!');
});

// Apply routes (uncomment when you create these files)
// app.use('/api/recipes', recipeRoutes);
// app.use('/api/favorites', favoriteRoutes);

// Global error handler
app.use((err: any, req: express.Request, res: express.Response, next: express.NextFunction) => {
  console.error(err.stack);
  res.status(500).send('Something broke on the server!');
});

// Start the server
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});

// Handle Prisma connection
process.on('beforeExit', async () => {
  await prisma.$disconnect();
});
```


