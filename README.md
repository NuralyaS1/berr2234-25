# berr2234-25

# Week 1 Exercise: Environment Setup, Git Workflows & Hello MongoDB

## Objective
This project sets up core development tools, introduces basic Git workflows, and creates a simple Node.js script that connects to MongoDB.

## Tools Required
- **VSCode**: Code editor ([Download](https://code.visualstudio.com/))
- **Node.js & npm**: JavaScript runtime and package manager ([Download](https://nodejs.org/))
- **MongoDB**: Database ([Installation Guide](https://www.mongodb.com/docs/manual/administration/install-community/))
- **Git**: Version control system ([Download](https://git-scm.com/))
- **MongoDB Compass** *(Optional)*: GUI for MongoDB ([Download](https://www.mongodb.com/products/compass))

---
## Installation Steps

### 1. Install Development Tools
#### **VSCode**
- Download and install from [here](https://code.visualstudio.com/).
- Install the recommended extension: MongoDB for VSCode.

#### **Node.js & npm**
- Download the LTS version from [nodejs.org](https://nodejs.org/).
- Verify installation using:
  ```sh
  node -v
  npm -v
  ```

#### **MongoDB**
- Follow the [MongoDB Community Server installation guide](https://www.mongodb.com/docs/manual/administration/install-community/).
- Start MongoDB service using:
  ```sh
  mongod --dbpath <your-db-path>
  ```

#### **Git**
- Download and install from [git-scm.com](https://git-scm.com/).
- Configure Git username and email:
  ```sh
  git config --global user.name "Your Name"
  git config --global user.email "your.email@example.com"
  ```

#### **MongoDB Compass (Optional)**
- Download and install from [here](https://www.mongodb.com/products/compass).

---
## 2. Git Basics & Repository Setup

### Create a GitHub Repository
1. Sign up at [GitHub](https://github.com/) if you don’t have an account.
2. Create a new repository named `week1-exercise`.
3. Clone the repository:
   ```sh
   git clone https://github.com/your-username/week1-exercise.git
   ```
4. Navigate to the cloned folder:
   ```sh
   cd week1-exercise
   ```

### Initialize Git & Create a Branch
```sh
git init
git checkout -b feature/setup
```

### Create README.md File
```sh
touch README.md
git add README.md
git commit -m "Added README"
```

### Push to GitHub
```sh
git push origin feature/setup
```

---
## 3. Create a "Hello MongoDB" Node.js Script

### Initialize a Node.js Project
```sh
npm init -y
```

### Install MongoDB Driver
```sh
npm install mongodb
```

### Create `index.js`
```javascript
const { MongoClient } = require("mongodb");
const uri = "mongodb://localhost:27017";
const client = new MongoClient(uri);

async function run() {
  try {
    await client.connect();
    console.log("Connected to MongoDB!");
    
    const database = client.db("testDB");
    const collection = database.collection("users");
    
    const doc = { name: "John Doe", age: 30 };
    const result = await collection.insertOne(doc);
    console.log("Inserted document ID:", result.insertedId);
  } finally {
    await client.close();
  }
}
run().catch(console.dir);
```

### Run the Script
```sh
node index.js

```

---
## 4. Push Code to GitHub

### Create `.gitignore`
```sh
echo "node_modules" > .gitignore
git add .gitignore
git commit -m "Added .gitignore"
```

### Commit and Push Code
```sh
git add .
git commit -m "Added MongoDB connection script"
git push origin feature/setup
```

---
## 5. Verification & Queries

### Check in MongoDB Compass
- Open MongoDB Compass and connect to `mongodb://localhost:27017`.
- Navigate to the `testDB` database and verify the `users` collection.

### MongoDB Shell Queries
```sh
mongo
use testDB
db.users.find().pretty()
```

### Check Installed Dependencies
```sh
cat package-lock.json | grep mongodb
```

---
## Submission Requirements

- A GitHub repository containing:
  - `README.md` documenting installation steps.
  - `index.js` script.
  - `.gitignore` file.
- Screenshots of:
  - Successful MongoDB connection in Node.js.
  - The inserted document in MongoDB Compass.

---
## Troubleshooting & FAQs

### **Common Errors & Fixes**
#### **MongoDB Connection Error**
```sh
ECONNREFUSED 127.0.0.1:27017
```
- Ensure MongoDB service is running:
  ```sh
  mongod --dbpath <your-db-path>
  ```

#### **Git Push Error**
```sh
fatal: remote origin already exists.
```
- Fix by running:
  ```sh
  git remote set-url origin https://github.com/your-username/week1-exercise.git
  ```

---
## Author
Your Name (Your GitHub Username)

