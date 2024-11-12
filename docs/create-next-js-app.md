# Create Your First Next.js App

## Step 1: Create a Next.js Project
Open your terminal and run the following command to create a new Next.js project:
    `npx create-next-app@latest next-demo`
This will create a new folder called next-demo with the required files and dependencies for a Next.js app.

## Step 2: Navigate to the Project Directory
After the project is created, move into the newly created directory:
    `cd next-demo`

## Step 3: Start the Development Server
Run the following command to start the development server and open your app in the browser:
    `npm run dev`
This will start the development server at `http://localhost:3000`. You should see the default Next.js landing page.

## Project Structure Overview
```
next-demo/                        # Root folder of your project
├── node_modules/                 # Folder containing all project dependencies (automatically managed by npm)
├── public/                       # Public static assets (served as is)
│   ├── favicon.ico               # Favicon for the app
│   └── ...                       # Other static assets (images, icons, etc.)
├── pages/                        # All the pages of your Next.js application
│   └── index.js                  # Main page (your React component with the button)
├── styles/                       # Folder containing CSS styles for the app
│   └── Home.module.css           # CSS Module for the Home page (scoped styles for the index page)
├── .gitignore                    # Git ignore file (specifies files/folders to be ignored by git)
├── package.json                  # Project metadata, dependencies, and scripts
├── package-lock.json             # Dependency version lock file
└── README.md                     # Project documentation (usually auto-generated)
```

## Step 4. Create a Button to Make API Call
Now, let's modify the default Next.js files to create the button and simulate an API call.
Open the `pages/index.js` file in your code editor and replace its contents with the following:

```
import { useState } from 'react';
import Head from 'next/head';
import styles from '../styles/Home.module.css';

export default function Home() {
const [message, setMessage] = useState('');

// Function to simulate an API call
const handleClick = async () => {
    try {
    setMessage('Loading...');  // Show loading state
    const data = await new Promise((resolve) => {
        setTimeout(() => {
        resolve({ message: 'API call was successful!' });
        }, 2000); // 2 seconds delay
    });

    setMessage(data.message);  // Update the state with the response
    } catch (error) {
    setMessage('Error occurred while making the API call.');
    }
};

return (
    <div className={styles.container}>
    <Head>
        <title>Next.js Dummy API Call</title>
        <meta name="description" content="Next.js app with a button that calls a dummy API" />
        <link rel="icon" href="/favicon.ico" />
    </Head>

    <main className={styles.main}>
        <h1 className={styles.title}>
        Welcome to Next.js!
        </h1>

        <button onClick={handleClick} className={styles.button}>
        Call Dummy API
        </button>

        <p className={styles.message}>{message}</p>
    </main>
    </div>
);
}
```

Add Custom CSS to `styles/Home.module.css`

```
/* Home.module.css */

/* Global styles for the body and container */
.container {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: #f4f7fa;
    font-family: Arial, sans-serif;
    margin: 0;
}

.main {
    text-align: center;
    padding: 20px;
}

/* Styling for the button */
.button {
    background-color: #007bff; /* Blue background */
    color: white; /* White text */
    font-size: 16px; /* Font size */
    padding: 12px 24px; /* Padding around text */
    border: none; /* Remove border */
    border-radius: 5px; /* Rounded corners */
    cursor: pointer; /* Pointer cursor on hover */
    transition: background-color 0.3s, transform 0.2s; /* Smooth transitions */
}

/* Hover effect for the button */
.button:hover {
    background-color: #0056b3; /* Darker blue on hover */
    transform: scale(1.05); /* Slightly enlarge the button */
}

/* Active state for the button (when clicked) */
.button:active {
    background-color: #004085; /* Even darker blue when clicked */
    transform: scale(1); /* Reset button size */
}

/* Styling for the message text */
.message {
    margin-top: 20px;
    font-size: 18px;
    color: #333;
}
```
 
[Back](../Readme.md)