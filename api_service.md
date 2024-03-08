## Deployment of API Service (Backend)

### Step 1: Upload files into a  GitHub Repository
- Create a new GitHub repository and upload the files into the repository.
- If you are already working in a github repo, just commit and push the files.

### Step 2: Deploy on Render
- Log in to [Render](https://render.com/).
- Navigate to "Web Services" and create a new web service.
- Choose "Build and deploy from a GitHub repo."
- Connect with GitHub, authorize the user and then select the repository from your github account which we created earlier.
- Fill in service details(name of the web service), set build command as `npm install`, and start command as `npm start` .
    - In our case we are using npm for managing the packages. It would be installing all the required packages ( dependencies mentioned in package.json) of our application.
    - The start command will start running our application.
- Create the service. After successful deployment we can use the link at the top left of the page to access our web service.
