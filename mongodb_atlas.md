## Connecting with MongoDB Atlas (Database)

### Introduction to MongoDB Atlas
MongoDB Atlas is a cloud-based database service that allows us to host and manage MongoDB databases. In this section, we will walk through the steps to set up a MongoDB Atlas cluster and connect it to our application.

### Step 1: MongoDB Atlas Setup
- Visit [MongoDB Atlas](https://cloud.mongodb.com/) and log in.
- Navigate to the "Database" section and choose either "Build a Database" or select the "Create" option.

### Step 2: Configure Network Access
- In "Network Access," click add an IP address and choose the option allow access from anywhere.

### Step 3: Set Up Database User
- Go to "Database Access" and add a new database user.
- Enter username and password. Scroll down to assign a role to the user. (Choose the option read and write database)
- Create user.


### Connect Atlas Cluster to MongoDB Compass
As of now we have seen how to create a cluster in atlas. We can connect the cluster with our application and perform various operations as our requirements. The database can be visualized in the atlas (in the browser), otherwise we can connect the cluster with compass and visualize the database through compass. Follow through the steps to connect the cluster with compass,
- In the "Database" section, click "Connect".
- In the "Access your data through tools" option, select "Compass" and copy the provided connection string.
- Use this connection string in compass to connect with the atlas cluster.
- Replace your actual password in the connection string and then click connect.
