# Ex06 BMI Calculator
## Date: 29-05-2026
## NAME:MADHUPRIYA R
## REG NO:212224040177

## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM
## app.jsx
```
import React, { useState } from "react";
import "./App.css";

function App() {

  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [bmi, setBmi] = useState("");
  const [message, setMessage] = useState("");

  const calculateBMI = (e) => {
    e.preventDefault();

    if (weight === "" || height === "") {
      alert("Please enter weight and height");
      return;
    }

    const bmiValue = (
      weight / ((height / 100) * (height / 100))
    ).toFixed(2);

    setBmi(bmiValue);

    if (bmiValue < 18.5) {
      setMessage("Underweight");
    } 
    else if (bmiValue < 24.9) {
      setMessage("Normal Weight");
    } 
    else if (bmiValue < 29.9) {
      setMessage("Overweight");
    } 
    else {
      setMessage("Obese");
    }
  };

  return (
    <div className="container">

      <div className="card">

        <h1>BMI Calculator</h1>

        <form onSubmit={calculateBMI}>

          <input
            type="number"
            placeholder="Enter Weight in Kg"
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
          />

          <input
            type="number"
            placeholder="Enter Height in cm"
            value={height}
            onChange={(e) => setHeight(e.target.value)}
          />

          <button type="submit">
            Calculate BMI
          </button>

        </form>

        {bmi && (
          <div className="result">

            <h2 style={{ color: "black" }}>
              Your BMI: {bmi}
            </h2>

            <h3 style={{ color: "green" }}>
              {message}
            </h3>

          </div>
        )}

      </div>

    </div>
  );
}

export default App;
```
## app.css
```
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(to right, #4facfe, #00f2fe);
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.card {
  background: white;
  padding: 35px;
  width: 350px;
  border-radius: 15px;
  text-align: center;
  box-shadow: 0px 4px 20px rgba(0,0,0,0.3);
}

h1 {
  color: #333;
}

input {
  width: 90%;
  padding: 12px;
  margin: 12px 0;
  border-radius: 8px;
  border: 1px solid #ccc;
  font-size: 16px;
}

button {
  width: 100%;
  padding: 12px;
  background-color: #0077ff;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 17px;
  cursor: pointer;
}

button:hover {
  background-color: #005fcc;
}

.result {
  margin-top: 20px;
  background: #f1f5f9;
  padding: 15px;
  border-radius: 10px;
}
```



## OUTPUT

<img width="1347" height="861" alt="image" src="https://github.com/user-attachments/assets/0cf62460-b195-4ef4-870f-baef81634b41" />



## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
