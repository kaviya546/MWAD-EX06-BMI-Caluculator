## Ex06 BMI Calculator
### Date: 
## AIM
To create a BMI calculator using React Router

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM
App.jsx:
```
import React, { useState } from "react";
import "./App.css";

function App() {
  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState("");

  const calculateBMI = () => {
    if (weight && height) {
      const heightInMeters = height / 100;
      const bmiValue = (weight / (heightInMeters * heightInMeters)).toFixed(2);
      setBmi(bmiValue);

      if (bmiValue < 18.5) setCategory("Underweight");
      else if (bmiValue < 25) setCategory("Normal weight");
      else if (bmiValue < 30) setCategory("Overweight");
      else setCategory("Obesity");
    }
  };

  const reset = () => {
    setWeight("");
    setHeight("");
    setBmi(null);
    setCategory("");
  };

  return (
    <div className="container">
      <h1>BMI Calculator</h1>
      <div className="card">
        <div className="input-group">
          <label>Weight (kg):</label>
          <input
            type="number"
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
          />
        </div>
        <div className="input-group">
          <label>Height (cm):</label>
          <input
            type="number"
            value={height}
            onChange={(e) => setHeight(e.target.value)}
          />
        </div>
        <div className="buttons">
          <button className="btn calculate" onClick={calculateBMI}>Calculate</button>
          <button className="btn reset" onClick={reset}>Reset</button>
        </div>
        {bmi && (
          <div className="result">
            <h2>Your BMI: {bmi}</h2>
            <p className={`category ${category.toLowerCase().replace(" ", "-")}`}>
              Category: {category}
            </p>
          </div>
        )}
      </div>
    </div>
  );
}

export default App;
```
App.css:
```
{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Roboto', sans-serif;
  background-color: #e0f7fa;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  color: #444;
}

.container {
  background-color: #ffffff;
  border-radius: 12px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 420px;
  padding: 30px;
  text-align: center;
}

h1 {
  font-size: 28px;
  margin-bottom: 20px;
  color: #00796b;
  font-weight: 700;
}

.input-group {
  margin-bottom: 20px;
}

.input-group label {
  font-size: 18px;
  margin-bottom: 10px;
  color: #00796b;
}

.input-group input {
  width: 100%;
  padding: 12px;
  font-size: 18px;
  border: 2px solid #00796b;
  border-radius: 8px;
  background-color: #e0f7fa;
  color: #00796b;
  outline: none;
}

.input-group input:focus {
  border-color: #004d40;
  background-color: #ffffff;
}

.buttons {
  display: flex;
  justify-content: space-between;
  gap: 15px;
}

.btn {
  width: 48%;
  padding: 12px;
  font-size: 16px;
  font-weight: 600;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.calculate {
  background-color: #00796b;
  color: white;
}

.calculate:hover {
  background-color: #004d40;
}

.reset {
  background-color: #f44336;
  color: white;
}

.reset:hover {
  background-color: #d32f2f;
}

.result {
  margin-top: 25px;
  padding: 15px;
  background-color: #f1f8e9;
  border-radius: 8px;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
}

h2 {
  font-size: 32px;
  color: #00796b;
  margin-bottom: 10px;
}

.category {
  font-size: 20px;
  font-weight: 600;
}

.underweight {
  color: #ffeb3b;
}

.normal-weight {
  color: #388e3c;
}

.overweight {
  color: #ff9800;
}

.obesity {
  color: #e64a19;
}
```
## OUTPUT
![Screenshot 2025-05-20 211940](https://github.com/user-attachments/assets/1105d20c-e096-45f3-b722-b2b567ce9131)


## RESULT
The program for creating BMI Calculator using React Router is executed successfully.

