# Ex06 BMI Calculator

```
NAME: AMIRTHAVARSHINI V
REG. NO: 212223040014

```

## Date:

## AIM:
To create a BMI calculator using React Router 

## ALGORITHM:
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

## PROGRAM:
### App.js
```
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from './components/Home';
import BmiForm from './components/BmiForm';
import Result from './components/Result';
import Footer from './components/Footer';
import './App.css'; // We'll add styles here

function App() {
  return (
    <Router>
      <div className="app-container">
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/bmi" element={<BmiForm />} />
          <Route path="/result" element={<Result />} />
        </Routes>
        <Footer />
      </div>
    </Router>
  );
}

export default App;
```
### Home.js
```
import React from 'react';
import { Link } from 'react-router-dom';

function Home() {
  return (
    <div style={{ textAlign: 'center' }}>
      <h1>Welcome to BMI Calculator</h1>
      <p>A simple tool to check your health status.</p>
      <Link to="/bmi"><button>Get Started</button></Link>
    </div>
  );
}

export default Home;
```
### BmiForm.js
```
import React, { useState } from 'react';
import { useNavigate } from 'react-router-dom';

function BmiForm() {
  const [height, setHeight] = useState('');
  const [weight, setWeight] = useState('');
  const [error, setError] = useState('');
  const navigate = useNavigate();

  const handleSubmit = (e) => {
    e.preventDefault();
    if (!height || !weight) {
      setError('Please enter both height and weight.');
      return;
    }
    if (isNaN(height) || isNaN(weight) || height <= 0 || weight <= 0) {
      setError('Please enter valid positive numbers.');
      return;
    }
    setError('');
    navigate('/result', { state: { height: parseFloat(height), weight: parseFloat(weight) } });
  };

  return (
    <div className="form-container" style={{ textAlign: 'center', maxWidth: '400px', margin: 'auto' }}>
      <h1>BMI Calculator</h1>
      <form onSubmit={handleSubmit}>
        <label>Height (cm):</label>
        <input type="number" value={height} onChange={(e) => setHeight(e.target.value)} />
        <br />
        <label>Weight (kg):</label>
        <input type="number" value={weight} onChange={(e) => setWeight(e.target.value)} />
        <br />
        {error && <p className="error">{error}</p>}
        <button type="submit">Calculate BMI</button>
      </form>
      <button onClick={() => navigate('/')} style={{ marginTop: '10px' }}>Back to Home</button>
    </div>
  );
}

export default BmiForm;
```

## OUTPUT:

<img width="1916" height="1020" alt="Screenshot 2025-11-04 105305" src="https://github.com/user-attachments/assets/b6f406e1-36c1-402a-8752-5e08912c47e7" />
<img width="1919" height="1021" alt="Screenshot 2025-11-04 105323" src="https://github.com/user-attachments/assets/abe939e8-20e8-4060-8f5e-0b83de38ab30" />
<img width="1919" height="1020" alt="image" src="https://github.com/user-attachments/assets/11ff0486-42c1-4922-a65e-259acb0ba428" />


## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
