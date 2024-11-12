# Set Up a New React Native Project

## Step 1: Install React Native CLI
You will need to install React Native CLI globally on your system. Open a terminal and run:
    `npm install -g react-native-cli`
This will create a new folder called next-demo with the required files and dependencies for a Next.js app.

## Step 2: Create a New React Native Project
Once the CLI is installed, create a new React Native project by running:
    `react-native init reactNativeDemo`
This will create a new directory called reactNativeApiDemo with all the necessary files and dependencies to get started with React Native.

## Step 3: Install Dependencies
Navigate into your project directory:
    `cd reactNativeApiDemo`
Then, to ensure all dependencies are installed (including any Android/iOS dependencies), run:
    `npm install`

## Step 4: Run the App on an Emulator or Device
To run the app, you need either an Android emulator or iOS simulator running, or you can use a physical device.
    * For iOS (macOS only), run: 
        `npx react-native run-ios`

    * For Android, ensure you have an Android emulator running or a physical Android device connected, and run:
        `npx react-native run-android`

## Project Structure Overview
    ```
        reactNativeApiDemo/               # Root directory of the project
        ├── android/                       # Android-specific code and resources
        ├── ios/                           # iOS-specific code and resources
        ├── node_modules/                  # Folder containing all project dependencies
        ├── app.json                       # Configuration file for React Native app
        ├── index.js                       # Entry point for React Native app (renders App component)
        ├── package.json                   # Project metadata, dependencies, and scripts
        ├── package-lock.json              # Dependency version lock file
        └── App.js                         # Main React component (contains button and API logic)
    ```

## Step 4. Create a Button to Make API Call
Now, let’s modify the App.js file to create the button and handle a simulated API call.

Open the `App.js` file in the project and replace its contents with the following code:

    ```
        import React, { useState } from 'react';
        import { View, Text, Button, StyleSheet } from 'react-native';

        const App = () => {
        const [message, setMessage] = useState('');

        // Function to simulate an API call
        const handleClick = async () => {
            try {
            setMessage('Loading...');  // Show loading state
            const data = await new Promise((resolve) => {
                setTimeout(() => {
                resolve({ message: 'API call was successful!' });
                }, 2000); // Simulating a 2-second API delay
            });

            setMessage(data.message);  // Update the state with the response
            } catch (error) {
            setMessage('Error occurred while making the API call.');
            }
        };

        return (
            <View style={styles.container}>
            <Text style={styles.title}>Welcome to React Native!</Text>

            {/* Button to trigger the API call */}
            <Button title="Call Dummy API" onPress={handleClick} />

            {/* Display the message after the API call */}
            <Text style={styles.message}>{message}</Text>
            </View>
        );
        };

        const styles = StyleSheet.create({
        container: {
            flex: 1,
            justifyContent: 'center',
            alignItems: 'center',
            backgroundColor: '#f4f7fa',
            padding: 20,
        },
        title: {
            fontSize: 24,
            marginBottom: 20,
        },
        message: {
            marginTop: 20,
            fontSize: 18,
            color: '#333',
        },
        });

        export default App;

    ```
 
[Back](../Readme.md)