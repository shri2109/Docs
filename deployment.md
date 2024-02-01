This documentation provides a comprehensive guide to deploy a web application, covering MongoDB Atlas setup, API service deployment on Render, and React application deployment on Vercel.

## Connecting with MongoDB Atlas (Database)

### Introduction to MongoDB Atlas
MongoDB Atlas is a cloud-based database service that allows you to host and manage MongoDB databases. In this section, we will walk through the steps to set up a MongoDB Atlas cluster and connect it to our application.

### Step 1: MongoDB Atlas Setup
- Visit [MongoDB Atlas](https://cloud.mongodb.com/) and log in.
- Navigate to the "Database" section and choose either "Build a Database" or select the "Create" option.

### Step 2: Configure Network Access
- In "Network Access," add an IP address and allow access from anywhere.

### Step 3: Set Up Database User
- Go to "Database Access" and add a new database user.
- Enter a username, password, and assign a role to the user.

### Step 4: Obtain Connection URI
- In the "Database" section, click "Connect".
- In the "Connect Your Application" option, select the "Drivers" option and copy the provided connection string.

### Step 5: Verify Database Connectivity
- Paste the connection URI into the `connect('')` function in the server code.
- Replace `<username>` and `<password>` with the actual credentials created earlier.
- Start the server and use Postman to verify the connectivity.

### Step 6: Optional - Connect Atlas Cluster to MongoDB Compass
- Connect the Atlas cluster to MongoDB Compass for real-time monitoring of changes in the database.
- This step is optional but can be useful for viewing and managing the data.
- In the "Database" section, click "Connect".
- In the "Access your data through tools" option, select the "Compass" option and copy the provided connection string.
- Use this connection string in compass to connect with the atlas cluster.

## Testing the API Endpoints

### Step 1: Include Database Name
- Before testing the API, ensure that the database name is included in the connection string after 'mongodb.net/'. (In the connection string that we have included in the server code earlier)
- If the specified database name doesn't exist, it will be created automatically.

### Step 2: Use Postman for Testing
- Test various APIs using Postman to ensure proper functionality.
- Real-time changes in the database can be monitored using MongoDB Compass.

## Deployment of API Service (Backend)

### Step 1: Push required code in a Github Repo
- Make sure you are already having all the required files in a github repo, otherwise create a new GitHub repository to deploy the API service.
- Push the required files to the repository. Consider the following files for example,  
    - `package.json` - containing the dependencies of the project
    - `server.cjs` - code for handling various end points
    - `db.cjs` - ensuring the db connectivity . 
    - More files may be there based on use case.
- The file names may be different in your case except the package.json file.
- Don't include node_modules and package_lock.json in the github repo.

### Step 2: Deploy on Render
- Log in to [Render](https://render.com/).
- Navigate to "Web Services" and create a new web service.
- Choose "Build and deploy from a GitHub repo."
- Connect with GitHub, authorize the user and then select the repository from your github account which we created earlier.
- Fill in service details(name of the web service), set build command as `npm install`, and start command as `node server.cjs`. (Change the file name as that of you included. This is the file that should contain the server code for handling various end points)
    - In our case we are using npm for managing the packages. It would be installing all the required packages ( dependencies mentioned in package.json) of our application.
    - The start command may vary if the main server file (in our case server.cjs) is not in the root directory of the github repo.
- Create the service. After successful deployment we can use the link at the top right of the page, to access our web service.

## Where to use the Deployed Web Service

Before deploying the React application, let's understand the use case of the deployed web service. The API service is responsible for handling data in the MongoDB database. It allows fetching data, adding entries, and more.

#### Axios for Sending Requests

To interact with the deployed web services from the react application, we will use Axios, a promise-based HTTP client. It's crucial to understand where and how to use Axios in your React application. Whether it's editing an entry, deleting an entry, or creating a new one, Axios is the tool to communicate with our deployed web service.

Below is a code snippet illustrating how to use Axios in a React application:

```jsx
import axios from 'axios';

// Replace 'api' with the link we got, right after deploying the web service
// Also replace the end-points in this code snippet '/get-entries', '/add-entry' with your actual end points.

// Fetching data from the API
axios.get('api/get-entries').then(response => {
  console.log(response.data);
});

// Adding a new entry to the database
axios.post('api/add-entry', {
     category: 'travel',
     amount: 850 })
  .then(response => {
  console.log(response.data);
});

// Other operations (editing, deleting, etc.) can be similarly implemented.
```

After understanding the use case, make sure to write requests to the API service using Axios wherever needed. For example, if you were to display all the entries, send a request to the API, fetch all the data, render them in the UI. Or if you want to delete an entry, send the request to the API with the id of the entry that you want to delete and then again render the UI with the current entries after deletion.

## Deployment of React Application (Frontend)

### Step 1: Complete and Test React Application

Ensure that the React web application is complete and tested. Verify all the functionalities that a user can be performing in your application. It is to be ensured that the API service that we deployed is correctly handled in the react application.

### Step 2: Build the Application

Run `npm run build` to generate either a `build` or `dist` folder containing the production-ready files. The folder name depends on the project configuration (e.g., a normal React app generates a `build` folder, while Vite generates `dist`).

### Step 3: Create GitHub Repository

Create a new GitHub repository and push the files that are inside the `build` or `dist` folder.

### Step 4: Deploy on Vercel

- Visit [Vercel](https://vercel.com/), you can be able to continue sign-up using github account. Otherwise you can sign-up with email and then later on connect with github.
- Import the project from the github repo.
- If you are not able to find the github repo, there would be an option like `Missing Git repository? Adjust GitHub App Permissions →` you can just add the required github repo to vercel.
- Follow the prompts to deploy the React application.


