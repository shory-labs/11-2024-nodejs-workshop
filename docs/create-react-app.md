# Create Your First React App

## Step 1: Create a React Project
1. Open your terminal or command prompt.
2. Run the following command to create a new React project using create-react-app:
    `npx create-react-app react-demo`
This will create a new folder called react-demo with all the necessary files and dependencies to start working with React.

## Step 2: Navigate to the Project Directory
After the project is created, move into the newly created directory:
    `cd react-demo`

## Step 3: Start the Development Server
Run the following command to start the development server and open your app in the browser:
    `npm start`
This will start the app and you should see the default React page in your browser at `http://localhost:3000`

## Project Structure Overview
    ```
        react-demo/
        ├── node_modules/        # Dependencies installed via npm
        ├── public/              # Public assets and HTML template
        │   ├── index.html       # The HTML file that gets served
        │   ├── favicon.ico      # The favicon for your app
        │   └── manifest.json    # Web app manifest file
        ├── src/                 # Source code for your React app
        │   ├── App.css          # CSS for the App component
        │   ├── App.js           # Main component of the app
        │   ├── App.test.js      # Tests for the App component
        │   ├── index.css        # Global CSS styles
        │   ├── index.js         # The JavaScript entry point of the app
        │   └── logo.svg         # React logo used in the default template
        ├── .gitignore           # Specifies which files to ignore in git
        ├── package.json         # Project metadata, dependencies, and scripts
        ├── package-lock.json    # Locked versions of dependencies for reproducibility
        └── README.md            # Project documentation (auto-generated)
    ```

## Step 4. Create a Button to Make API Call
Open the `src/App.js` file in your code editor (VS Code, Atom, etc.).
Replace the existing code in App.js with the following code:
    ```
    import React, { useState } from 'react';
    import './App.css';

    function App() {
    const [message, setMessage] = useState('');

    // Function to simulate an API call
    const handleClick = async () => {
        try {
        // Simulating a API call with setTimeout
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
        <div className="App">
        <h1>React API Call Example</h1>
        <button className="button" onClick={handleClick}>Call API</button>
        <p>{message}</p>
        </div>
    );
    }

    export default App;

    ```

Let's apply some CSS styling to the button in the App.css file.

    ```
        /* Button Styling */
        .button {
        padding: 12px 24px;
        font-size: 16px;
        font-weight: 600;
        text-transform: uppercase;
        background-color: #4CAF50; /* Green background */
        color: white;
        border: none;
        border-radius: 8px;
        cursor: pointer;
        transition: all 0.3s ease;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        .button:hover {
        background-color: #45a049; /* Darker green on hover */
        transform: translateY(-2px); /* Slightly lift the button */
        box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15); /* Deepen shadow on hover */
        }

        .button:focus {
        outline: none;
        box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.6); /* Green focus ring */
        }

        .button:active {
        background-color: #3e8e41; /* Even darker green on click */
        transform: translateY(2px); /* Button pressed effect */
        }
    ```
 
[Back](../Readme.md)