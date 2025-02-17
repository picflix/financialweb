<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Personal Finance Management Tool</title>
  <!-- Include Chart.js -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    /* =========================
       PERSONAL FINANCE TOOL CSS
       ========================= */
    body {
      font-family: 'Arial', sans-serif;
      margin: 0;
      padding: 0;
      background: #f5f7fa;
      color: #333;
    }
    header {
      background: linear-gradient(to right, #11998e, #38ef7d);
      color: white;
      text-align: center;
      padding: 20px 10px;
    }
    header h1 {
      margin: 0;
      font-size: 2.5rem;
    }
    header p {
      margin: 5px 0;
      font-size: 1.2rem;
    }
    nav {
      background: #071a52;
      padding: 10px 0;
      text-align: center;
    }
    nav a {
      color: white;
      text-decoration: none;
      margin: 0 15px;
      font-size: 1.1rem;
      font-weight: bold;
    }
    nav a:hover {
      text-decoration: underline;
    }
    section {
      max-width: 1100px;
      margin: 20px auto;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    }
    h2 {
      text-align: center;
      color: #11998e;
      margin-bottom: 20px;
    }
    .form-group {
      margin-bottom: 20px;
    }
    .form-group label {
      display: block;
      font-weight: bold;
      margin-bottom: 5px;
    }
    .form-group input,
    .form-group textarea {
      width: 100%;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 5px;
      font-size: 1rem;
    }
    button {
      background: #11998e;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 5px;
      font-size: 1rem;
      cursor: pointer;
      display: block;
      margin: 0 auto;
    }
    button:hover {
      background: #0a785a;
    }
    .results {
      background: #f1f9f5;
      padding: 20px;
      margin-top: 20px;
      border-radius: 10px;
      border: 1px solid #ddd;
    }
    .results p {
      font-size: 1.1rem;
      margin: 10px 0;
    }
    .results .red {
      color: red;
      font-weight: bold;
    }
    .results .green {
      color: green;
      font-weight: bold;
    }
    canvas {
      max-width: 100%;
      margin: 20px auto;
    }
    #ai-insights {
      margin-top: 20px;
      background: #f9f9f9;
      padding: 15px;
      border-radius: 10px;
      border: 1px solid #ddd;
    }
    #ai-insights h3 {
      color: #071a52;
      margin-bottom: 10px;
    }
    footer {
      background: #071a52;
      color: white;
      text-align: center;
      padding: 15px 0;
    }
    footer p {
      margin: 0;
    }
    .ai-tips {
      background-color: yellow;
      padding: 10px;
      border-radius: 5px;
      margin-bottom: 10px;
    }
    /* Responsive Styles */
    @media (max-width: 768px) {
      header h1 {
        font-size: 2rem;
      }
      header p {
        font-size: 1rem;
      }
      nav a {
        font-size: 1rem;
        margin: 0 10px;
      }
      section {
        margin: 10px;
        padding: 15px;
      }
      .form-group input,
      .form-group textarea {
        font-size: 0.9rem;
      }
      button {
        font-size: 0.9rem;
        padding: 8px 16px;
      }
      canvas {
        width: 100%;
        height: 250px;
      }
      #ai-insights {
        padding: 10px;
      }
      footer p {
        font-size: 0.9rem;
      }
    }
    @media (min-width: 769px) {
      section {
        padding: 25px;
      }
      canvas {
        width: 75%;
        height: 400px;
      }
    }

    /* =========================
       LOGIN OVERLAY CSS
       ========================= */
    /* The overlay covers the whole page */
    #loginOverlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: #111;
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 9999;
      overflow: hidden;
    }
    /* Animated ring container */
    #loginOverlay .ring {
      position: relative;
      width: 500px;
      height: 500px;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    #loginOverlay .ring i {
      position: absolute;
      inset: 0;
      border: 2px solid #fff;
      transition: 0.5s;
    }
    #loginOverlay .ring i:nth-child(1) {
      border-radius: 38% 62% 63% 37% / 41% 44% 56% 59%;
      animation: animate 6s linear infinite;
    }
    #loginOverlay .ring i:nth-child(2) {
      border-radius: 41% 44% 56% 59%/38% 62% 63% 37%;
      animation: animate 4s linear infinite;
    }
    #loginOverlay .ring i:nth-child(3) {
      border-radius: 41% 44% 56% 59%/38% 62% 63% 37%;
      animation: animate2 10s linear infinite;
    }
    #loginOverlay .ring:hover i {
      border: 6px solid var(--clr);
    }
    @keyframes animate {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
    @keyframes animate2 {
      0% { transform: rotate(360deg); }
      100% { transform: rotate(0deg); }
    }
    /* Login form container */
    #loginOverlay .login {
      position: absolute;
      width: 300px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      align-items: center;
    }
    #loginOverlay .login h2 {
      color: #fff;
      font-size: 2em;
      text-transform: uppercase;
    }
    #loginOverlay .inputBx {
      position: relative;
      width: 100%;
    }
    #loginOverlay .inputBx input {
      width: 100%;
      padding: 12px 20px;
      background: transparent;
      border: 2px solid #fff;
      border-radius: 40px;
      font-size: 1.2em;
      color: #fff;
      outline: none;
    }
    #loginOverlay .inputBx input[type="submit"] {
      background: linear-gradient(45deg, #00ff0a, #ff0057);
      border: none;
      cursor: pointer;
      font-weight: 600;
    }
    #loginOverlay .inputBx input::placeholder {
      color: rgba(255, 255, 255, 0.75);
    }
    #loginOverlay .links {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    #loginOverlay .links a {
      color: #fff;
      text-decoration: none;
    }
    #loginOverlay .links a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>
  <!-- LOGIN OVERLAY (This covers the page until login is completed) -->
  <div id="loginOverlay">
    <div class="ring">
      <i style="--clr:#00ff0a;"></i>
      <i style="--clr:#ff0057;"></i>
      <i style="--clr:#fffd44;"></i>
      <div class="login">
        <h2>Login</h2>
        <div class="inputBx">
          <input type="text" placeholder="Username" id="username" />
        </div>
        <div class="inputBx">
          <input type="password" placeholder="Password" id="password" />
        </div>
        <div class="inputBx">
          <!-- When clicking Sign in, the loginComplete() function fires -->
          <input type="submit" value="Sign in" onclick="loginComplete()" />
        </div>
        <div class="links">
          <a href="#">Forget Password</a>
          <a href="#">Signup</a>
        </div>
      </div>
    </div>
  </div>

  <!-- PERSONAL FINANCE MANAGEMENT TOOL CONTENT -->
  <header>
    <h1>Personal Finance Management Tool</h1>
    <p>AI-Powered Budget Tracking &amp; Expense Guidance</p>
  </header>
  <nav>
    <a href="#income-section">Income</a>
    <a href="#expense-section">Expenses</a>
    <a href="#results-section">Results</a>
  </nav>
  <section id="income-section">
    <h2>Enter Your Monthly Income</h2>
    <div class="form-group">
      <label for="monthly-income">Monthly Income:</label>
      <input type="number" id="monthly-income" placeholder="Enter your income" />
    </div>
    <button onclick="setIncome()">Submit Income</button>
  </section>
  <section id="expense-section">
    <h2>Track Your Expenses</h2>
    <div class="form-group">
      <label for="expenses">List Your Expenses (separated by commas):</label>
      <textarea id="expenses" rows="4" placeholder="e.g., Rent:5000, Groceries:3000, Utilities:2000"></textarea>
    </div>
    <button onclick="trackExpenses()">Submit Expenses</button>
  </section>
  <section id="results-section">
    <h2>AI-Powered Guidance</h2>
    <div class="results" id="results">
      <p>No data entered yet. Submit your income and expenses to see results!</p>
    </div>
    <canvas id="expenseChart"></canvas>
    <div id="ai-insights">
      <h3>Suggestions</h3>
      <p id="suggestion-text"></p>
      <div class="ai-tips">
        <h3>AI-Powered Tips</h3>
        <p id="tips-text"></p>
      </div>
      <h3>Problem</h3>
      <p id="problem-text"></p>
      <h3>Solution</h3>
      <p id="solution-text"></p>
    </div>
  </section>
  <footer>
    <p>&copy; 2024 Personal Finance Management Tool | AI-Powered Budget Guidance</p>
  </footer>

  <script>
    // -------------------------------------------------------
    // LOGIN FUNCTION: Hide overlay on login completion
    // -------------------------------------------------------
    function loginComplete() {
      // Optionally validate credentials here
      document.getElementById("loginOverlay").style.display = "none";
    }

    // -------------------------------------------------------
    // PERSONAL FINANCE MANAGEMENT TOOL SCRIPT
    // -------------------------------------------------------
    let monthlyIncome = 0;
    let totalExpenses = 0;
    let expenseChart; // Global variable to hold the chart instance

    function setIncome() {
      const incomeInput = document.getElementById("monthly-income").value;
      if (incomeInput > 0) {
        monthlyIncome = parseFloat(incomeInput);
        document.getElementById("results").innerHTML = `<p>Income Submitted: <strong>₹${monthlyIncome}</strong></p>`;
      } else {
        alert("Please enter a valid income.");
      }
    }

    function trackExpenses() {
      const expensesInput = document.getElementById("expenses").value;
      const expensesArray = expensesInput.split(",");
      totalExpenses = 0;
      let expenseData = {};
      let breakdown = '<p><strong>Expense Breakdown:</strong></p><ul>';

      expensesArray.forEach(expense => {
        const [item, cost] = expense.split(":").map(e => e.trim());
        if (item && cost && !isNaN(cost)) {
          totalExpenses += parseFloat(cost);
          expenseData[item] = parseFloat(cost);
          breakdown += `<li>${item}: ₹${cost}</li>`;
        }
      });

      breakdown += "</ul>";
      const remaining = monthlyIncome - totalExpenses;

      let suggestion, problem, solution, tips;

      if (remaining > 0) {
        suggestion = `You're on track! Keep saving!`;
        problem = "None. Your finances are well-managed.";
        solution = "Continue monitoring your expenses and saving consistently.";
        tips = "Invest your savings in mutual funds or fixed deposits for better returns.";
      } else if (remaining === 0) {
        suggestion = `Budget balanced! Consider saving more!`;
        problem = "You aren't saving money.";
        solution = "Find areas to reduce spending and allocate for savings.";
        tips = "Review your expenses to identify potential savings.";
      } else {
        suggestion = `You're overspending! Cut unnecessary expenses.`;
        problem = "You are spending more than your income.";
        solution = "Prioritize essential expenses and reduce luxury spending.";
        tips = "Avoid unnecessary purchases and plan your budget carefully.";
      }

      document.getElementById("results").innerHTML = `
        ${breakdown}
        <p><strong>Total Expenses:</strong> ₹${totalExpenses}</p>
        <p><strong>Remaining Budget:</strong> <span id="remaining-budget" style="color: ${
          remaining > 0 ? "green" : "red"
        };">₹${remaining}</span></p>
      `;

      // Populate AI insights
      document.getElementById("suggestion-text").innerText = suggestion;
      document.getElementById("solution-text").innerText = solution;
      document.getElementById("tips-text").innerText = tips;
      document.getElementById("suggestion-text").style.color = remaining > 0 ? "green" : "red";
      document.getElementById("problem-text").innerText = problem;

      renderChart(expenseData, remaining);
    }

    function renderChart(expenseData, remaining) {
      const ctx = document.getElementById("expenseChart").getContext("2d");
      const labels = [...Object.keys(expenseData), "Remaining"];
      const data = [...Object.values(expenseData), remaining > 0 ? remaining : 0];

      // Destroy previous chart instance if it exists
      if (expenseChart) {
        expenseChart.destroy();
      }
      
      expenseChart = new Chart(ctx, {
        type: "pie",
        data: {
          labels: labels,
          datasets: [{
            data: data,
            backgroundColor: [
              "#FF6384",
              "#36A2EB",
              "#FFCE56",
              "#4CAF50",
              "#FF5722",
              "#9C27B0"
            ]
          }]
        },
        options: {
          responsive: true,
          plugins: {
            legend: { position: "top" },
            tooltip: {
              callbacks: {
                label: function (tooltipItem) {
                  return tooltipItem.label + ": ₹" + tooltipItem.raw;
                }
              }
            }
          }
        }
      });
    }
  </script>
</body>
</html>
