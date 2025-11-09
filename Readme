# Ex-06: BMI Calculator
## Date: 27-10-2025

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
#### main.jsx
```
import React from "react";
import { createRoot } from "react-dom/client";
import { BrowserRouter } from "react-router-dom";
import App from "./App";
import "./styles.css";

createRoot(document.getElementById("root")).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```
#### App.jsx
```
import React from "react";
import { Routes, Route, Link } from "react-router-dom";
import Home from "./pages/Home";
import BMICalculator from "./components/BMICalculator";

export default function App() {
  return (
    <div className="app-root">
      <header className="header">
        <Link to="/" className="logo">BMI Calculator</Link>
        <nav>
          <Link to="/" className="nav-link">Home</Link>
          <Link to="/calculator" className="nav-link">Calculator</Link>
        </nav>
      </header>

      <main className="main">
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/calculator" element={<BMICalculator />} />
        </Routes>
      </main>

      <footer className="footer">
        <p>© 2025 BMI Calculator | MWAD Experiment 06</p>
      </footer>
    </div>
  );
}
```
#### Home.jsx
```
import React from "react";
import { Link } from "react-router-dom";

export default function Home() {
  return (
    <section className="home">
      <h1 className="home-title">Welcome to BMI Calculator</h1>
      <p className="home-desc">
        Easily calculate your Body Mass Index (BMI) and find out your health range.
      </p>
      <Link to="/calculator" className="btn-start">Go to Calculator</Link>
    </section>
  );
}
```
#### BMICalculator.jsx
```
import React, { useState, useMemo } from "react";

export default function BMICalculator() {
  const [units, setUnits] = useState("metric");
  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [error, setError] = useState("");

  const parse = (v) => Number(String(v).replace(/,/g, "").trim());

  const { bmi, category } = useMemo(() => {
    const w = parse(weight);
    const h = parse(height);
    if (!w || !h) return { bmi: null, category: "" };
    let kg = w;
    let m = h;
    if (units === "metric") m = h / 100;
    else {
      kg = w * 0.453592;
      m = h * 0.0254;
    }
    const result = kg / (m * m);
    const rounded = Math.round(result * 10) / 10;
    let cat = "";
    if (rounded < 18.5) cat = "Underweight";
    else if (rounded < 25) cat = "Normal";
    else if (rounded < 30) cat = "Overweight";
    else cat = "Obese";
    return { bmi: rounded, category: cat };
  }, [weight, height, units]);

  const handleSubmit = (e) => {
    e.preventDefault();
    const w = parse(weight);
    const h = parse(height);
    if (!w || !h) {
      setError("Please enter valid positive numbers");
      return;
    }
    setError("");
  };

  const reset = () => {
    setWeight("");
    setHeight("");
    setError("");
  };

  return (
    <section className="bmi-section">
      <div className="bmi-card">
        <h2 className="bmi-title">BMI Calculator</h2>

        <div className="unit-toggle">
          <label className={`unit ${units === "metric" ? "selected" : ""}`}>
            <input type="radio" checked={units === "metric"} onChange={() => setUnits("metric")} />
            Metric (kg, cm)
          </label>
          <label className={`unit ${units === "imperial" ? "selected" : ""}`}>
            <input type="radio" checked={units === "imperial"} onChange={() => setUnits("imperial")} />
            Imperial (lb, in)
          </label>
        </div>

        <form onSubmit={handleSubmit} className="bmi-form">
          <input
            type="text"
            placeholder={units === "metric" ? "Weight (kg)" : "Weight (lb)"}
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
          />
          <input
            type="text"
            placeholder={units === "metric" ? "Height (cm)" : "Height (in)"}
            value={height}
            onChange={(e) => setHeight(e.target.value)}
          />
          {error && <p className="error">{error}</p>}

          <div className="buttons">
            <button type="submit" className="btn-calc">Calculate</button>
            <button type="button" className="btn-reset" onClick={reset}>Reset</button>
          </div>
        </form>

        {bmi && (
          <div className="bmi-result">
            <h3>Your BMI: {bmi}</h3>
            <p className={`category ${category.toLowerCase()}`}>{category}</p>
          </div>
        )}
      </div>
    </section>
  );
}
```
#### styles.css
```
* { box-sizing: border-box; }

body, html, #root {
  height: 100%;
  margin: 0;
  font-family: "Poppins", sans-serif;
  background: linear-gradient(120deg, #dbeafe 0%, #f0fdf4 100%);
  color: #1e293b;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #2563eb;
  padding: 14px 28px;
}

.logo {
  color: white;
  font-size: 1.4rem;
  font-weight: 700;
  text-decoration: none;
}

.nav-link {
  color: white;
  text-decoration: none;
  margin-left: 18px;
  font-weight: 500;
}

.footer {
  text-align: center;
  padding: 10px;
  background: #2563eb;
  color: white;
  font-size: 0.9rem;
}

.home {
  text-align: center;
  padding: 60px 20px;
}

.home-title {
  font-size: 2.4rem;
  color: #1d4ed8;
}

.home-desc {
  font-size: 1.1rem;
  color: #334155;
  margin-bottom: 24px;
}

.btn-start {
  background: #10b981;
  color: white;
  padding: 10px 20px;
  border-radius: 10px;
  text-decoration: none;
  font-weight: 600;
}

.bmi-section {
  display: flex;
  justify-content: center;
  padding: 50px 20px;
}

.bmi-card {
  background: white;
  padding: 30px;
  border-radius: 16px;
  max-width: 500px;
  width: 100%;
  box-shadow: 0 8px 25px rgba(37, 99, 235, 0.15);
  text-align: center;
}

.bmi-title {
  color: #1d4ed8;
  font-size: 1.8rem;
}

.unit-toggle {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin: 20px 0;
}

.unit {
  padding: 8px 14px;
  border-radius: 20px;
  background: #e0f2fe;
  cursor: pointer;
}

.unit.selected {
  background: #1d4ed8;
  color: white;
}

.bmi-form {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.bmi-form input {
  padding: 12px;
  border-radius: 10px;
  border: 1px solid #cbd5e1;
  font-size: 1rem;
  text-align: center;
}

.error {
  color: #b91c1c;
  font-size: 0.9rem;
}

.buttons {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 10px;
}

.btn-calc {
  background: #2563eb;
  color: white;
  border: none;
  padding: 10px 18px;
  border-radius: 10px;
  font-weight: 600;
}

.btn-reset {
  background: #f59e0b;
  color: white;
  border: none;
  padding: 10px 18px;
  border-radius: 10px;
  font-weight: 600;
}

.bmi-result {
  margin-top: 20px;
  background: #f0f9ff;
  border-radius: 10px;
  padding: 14px;
}

.category {
  font-size: 1.2rem;
  font-weight: 700;
  margin: 6px 0;
}

.category.underweight { color: #f59e0b; }
.category.normal { color: #10b981; }
.category.overweight { color: #f97316; }
.category.obese { color: #dc2626; }
```

## OUTPUT
<img width="1915" height="884" alt="image" src="https://github.com/user-attachments/assets/39a9c8cf-5fb5-4bac-ba99-37aedc2b0b68" />
<img width="1908" height="877" alt="image" src="https://github.com/user-attachments/assets/3af80615-09e8-4867-b594-679d4c41ebed" />


## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
