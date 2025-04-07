<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Personal Finance Management Tool</title>
  <!-- Include Chart.js -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <!-- Include Font Awesome for icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Montserrat:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    /* =========================
       PREMIUM MODERN THEME 2025
       ========================= */
    :root {
      --primary-gradient: linear-gradient(135deg, #4361ee 0%, #3a0ca3 100%);
      --secondary-gradient: linear-gradient(135deg, #7209b7 0%, #4361ee 100%);
      --accent-gradient: linear-gradient(135deg, #f72585 0%, #b5179e 100%);
      --success-gradient: linear-gradient(135deg, #4cc9f0 0%, #4895ef 100%);
      --warning-gradient: linear-gradient(135deg, #f8961e 0%, #f3722c 100%);
      --danger-gradient: linear-gradient(135deg, #ef233c 0%, #d90429 100%);
      
      /* Dark mode variables */
      --dark-primary: #3a0ca3;
      --dark-secondary: #7209b7;
      --dark-accent: #f72585;
      --dark-nav-color: #0a0a1a;
      --dark-sidebar-bg: #12122e;
      --dark-card-bg: #1e1e2e;
      --dark-text-color: #e2e2e2;
      --dark-text-light: #f8f9fa;
      --dark-shadow-color: rgba(0, 0, 0, 0.5);
      --dark-border-color: rgba(255, 255, 255, 0.1);
      --dark-input-bg: rgba(30, 30, 46, 0.8);
      --dark-error-color: #ff6b6b;
      --dark-success-color: #6bff6b;
      
      /* Light mode variables */
      --nav-color: #0c0d2e;
      --sidebar-bg: #1a1a2e;
      --card-bg: rgba(255, 255, 255, 0.97);
      --text-color: #2b2d42;
      --text-light: #f8f9fa;
      --accent-color: #f72585;
      --success-color: #4cc9f0;
      --warning-color: #f8961e;
      --danger-color: #ef233c;
      --border-color: rgba(0, 0, 0, 0.1);
      --input-bg: rgba(255, 255, 255, 0.9);
      --error-color: #ef233c;
      
      --shadow-sm: 0 1px 3px rgba(0,0,0,0.12);
      --shadow-md: 0 4px 6px rgba(0,0,0,0.1);
      --shadow-lg: 0 10px 15px rgba(0,0,0,0.1);
      --shadow-xl: 0 20px 25px rgba(0,0,0,0.1);
      --shadow-xxl: 0 25px 50px rgba(0,0,0,0.25);
      
      --border-radius-sm: 8px;
      --border-radius-md: 12px;
      --border-radius-lg: 16px;
      --border-radius-xl: 24px;
      --border-radius-xxl: 32px;
    }

    @keyframes float {
      0% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
      100% { transform: translateY(0px); }
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes pulse {
      0% { box-shadow: 0 0 0 0 rgba(72, 149, 239, 0.7); }
      70% { box-shadow: 0 0 0 15px rgba(72, 149, 239, 0); }
      100% { box-shadow: 0 0 0 0 rgba(72, 149, 239, 0); }
    }

    @keyframes gradientFlow {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Poppins', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f8f9fa;
      color: var(--text-color);
      line-height: 1.6;
      overflow-x: hidden;
      min-height: 100vh;
      transition: background-color 0.3s ease, color 0.3s ease;
    }

    body.dark-mode {
      background-color: #121212;
      color: var(--dark-text-color);
    }

    h1, h2, h3, h4, h5, h6 {
      font-family: 'Montserrat', sans-serif;
      font-weight: 600;
      color: var(--text-color);
    }

    body.dark-mode h1,
    body.dark-mode h2,
    body.dark-mode h3,
    body.dark-mode h4,
    body.dark-mode h5,
    body.dark-mode h6 {
      color: var(--dark-text-light);
    }

    /* Premium header with modern abstract background */
    header {
      background: 
        linear-gradient(rgba(12, 13, 46, 0.9), rgba(12, 13, 46, 0.9)),
        url('https://images.unsplash.com/photo-1635070041078-e363dbe005cb?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80') no-repeat center center;
      background-size: cover;
      color: white;
      text-align: center;
      padding: 40px 20px;
      position: relative;
      overflow: hidden;
      box-shadow: var(--shadow-xl);
    }

    body.dark-mode header {
      background: linear-gradient(rgba(10, 10, 26, 0.9), rgba(10, 10, 26, 0.9));
      color: var(--dark-text-light);
    }

    header::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle, rgba(67, 97, 238, 0.1) 0%, rgba(12, 13, 46, 0.8) 70%);
      animation: float 15s infinite linear;
    }

    header h1 {
      margin: 0;
      font-size: 2.8rem;
      font-weight: 700;
      text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
      position: relative;
      animation: fadeIn 0.8s ease-out;
      background: linear-gradient(to right, #fff, #c1c8ff);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      letter-spacing: -0.5px;
    }

    header p {
      margin: 15px 0 0;
      font-size: 1.3rem;
      opacity: 0.9;
      position: relative;
      animation: fadeIn 1s ease-out;
      max-width: 700px;
      margin-left: auto;
      margin-right: auto;
    }

    /* Premium navigation */
    nav {
      background: var(--nav-color);
      padding: 15px 0;
      text-align: center;
      box-shadow: var(--shadow-lg);
      position: relative;
      z-index: 10;
    }

    body.dark-mode nav {
      background: var(--dark-nav-color);
    }

    nav a {
      color: white;
      text-decoration: none;
      margin: 0 20px;
      font-size: 1.1rem;
      font-weight: 500;
      padding: 10px 20px;
      border-radius: var(--border-radius-xl);
      transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
      position: relative;
      letter-spacing: 0.5px;
    }

    nav a:hover {
      background: rgba(255, 255, 255, 0.15);
      transform: translateY(-2px);
    }

    nav a::after {
      content: '';
      position: absolute;
      bottom: -5px;
      left: 50%;
      transform: translateX(-50%);
      width: 0;
      height: 3px;
      background: white;
      transition: width 0.3s ease;
    }

    nav a:hover::after {
      width: 60%;
    }

    /* Premium card sections */
    section {
      max-width: 1100px;
      margin: 40px auto;
      background: var(--card-bg);
      padding: 40px;
      border-radius: var(--border-radius-lg);
      box-shadow: var(--shadow-lg);
      backdrop-filter: blur(5px);
      border: 1px solid var(--border-color);
      animation: fadeIn 0.6s ease-out;
      transition: all 0.3s ease;
      position: relative;
      overflow: hidden;
    }

    body.dark-mode section {
      background: var(--dark-card-bg);
      color: var(--dark-text-color);
      border-color: var(--dark-border-color);
    }

    section::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 5px;
      background: var(--primary-gradient);
    }

    section:hover {
      transform: translateY(-5px);
      box-shadow: var(--shadow-xl);
    }

    h2 {
      text-align: center;
      color: #4361ee;
      margin-bottom: 30px;
      font-size: 2rem;
      position: relative;
      display: inline-block;
      left: 50%;
      transform: translateX(-50%);
      padding-bottom: 10px;
    }

    body.dark-mode h2 {
      color: var(--dark-accent);
    }

    h2::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 4px;
      background: var(--primary-gradient);
      border-radius: 2px;
    }

    /* Premium form elements */
    .form-group {
      margin-bottom: 30px;
      position: relative;
    }

    .form-group label {
      display: block;
      font-weight: 500;
      margin-bottom: 12px;
      color: var(--text-color);
      font-size: 1.1rem;
    }

    body.dark-mode .form-group label {
      color: var(--dark-text-color);
    }

    .form-group input,
    .form-group textarea,
    .form-group select {
      width: 100%;
      padding: 15px 20px;
      border: 2px solid var(--border-color);
      border-radius: var(--border-radius-md);
      font-size: 1rem;
      transition: all 0.3s ease;
      background: var(--input-bg);
      font-family: 'Poppins', sans-serif;
      color: var(--text-color);
    }

    body.dark-mode .form-group input,
    body.dark-mode .form-group textarea,
    body.dark-mode .form-group select {
      background: var(--dark-input-bg);
      color: var(--dark-text-color);
      border-color: var(--dark-border-color);
    }

    .form-group input:focus,
    .form-group textarea:focus,
    .form-group select:focus {
      border-color: #4361ee;
      box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.2);
      outline: none;
    }

    body.dark-mode .form-group input:focus,
    body.dark-mode .form-group textarea:focus,
    body.dark-mode .form-group select:focus {
      border-color: var(--dark-accent);
      box-shadow: 0 0 0 3px rgba(247, 37, 133, 0.2);
    }

    button {
      background: var(--primary-gradient);
      color: white;
      border: none;
      padding: 15px 35px;
      border-radius: var(--border-radius-xl);
      font-size: 1.1rem;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto;
      transition: all 0.3s ease;
      font-weight: 600;
      letter-spacing: 0.5px;
      box-shadow: var(--shadow-md);
      position: relative;
      overflow: hidden;
    }

    button i {
      margin-right: 10px;
    }

    button:hover {
      transform: translateY(-3px);
      box-shadow: var(--shadow-lg);
    }

    button:active {
      transform: translateY(1px);
    }

    button::after {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
      transition: all 0.6s ease;
    }

    button:hover::after {
      left: 100%;
    }

    /* Secondary button style */
    button.secondary {
      background: white;
      color: #4361ee;
      border: 2px solid #4361ee;
    }

    body.dark-mode button.secondary {
      background: var(--dark-card-bg);
      color: var(--dark-text-color);
      border-color: var(--dark-accent);
    }

    button.danger {
      background: var(--danger-gradient);
    }

    button.success {
      background: var(--success-gradient);
    }

    /* Premium results section */
    .results {
      background: rgba(241, 249, 245, 0.9);
      padding: 30px;
      margin-top: 30px;
      border-radius: var(--border-radius-md);
      border: 1px solid var(--border-color);
      backdrop-filter: blur(5px);
      animation: fadeIn 0.8s ease-out;
    }

    body.dark-mode .results {
      background: var(--dark-card-bg);
      border-color: var(--dark-border-color);
    }

    .results p {
      font-size: 1.1rem;
      margin: 15px 0;
      line-height: 1.6;
      color: var(--text-color);
    }

    body.dark-mode .results p {
      color: var(--dark-text-color);
    }

    .results .red {
      color: var(--danger-color);
      font-weight: bold;
    }

    .results .green {
      color: var(--success-color);
      font-weight: bold;
    }

    body.dark-mode .results .red {
      color: var(--dark-error-color);
    }

    body.dark-mode .results .green {
      color: var(--dark-success-color);
    }

    canvas {
      max-width: 100%;
      margin: 40px auto;
      animation: fadeIn 1s ease-out;
      display: block;
      background-color: var(--card-bg);
      border-radius: var(--border-radius-md);
      padding: 20px;
    }

    body.dark-mode canvas {
      background-color: var(--dark-card-bg);
    }

    /* Premium AI insights */
    #ai-insights {
      margin-top: 40px;
      background: rgba(249, 249, 249, 0.9);
      padding: 30px;
      border-radius: var(--border-radius-md);
      border: 1px solid var(--border-color);
      backdrop-filter: blur(5px);
      animation: fadeIn 1s ease-out;
    }

    body.dark-mode #ai-insights {
      background: var(--dark-card-bg);
      border-color: var(--dark-border-color);
    }

    #ai-insights h3 {
      color: var(--nav-color);
      margin-bottom: 20px;
      font-size: 1.3rem;
      border-bottom: 2px solid #eee;
      padding-bottom: 10px;
      display: flex;
      align-items: center;
    }

    body.dark-mode #ai-insights h3 {
      color: var(--dark-text-light);
      border-bottom-color: var(--dark-border-color);
    }

    #ai-insights h3 i {
      margin-right: 10px;
      color: #4361ee;
    }

    body.dark-mode #ai-insights h3 i {
      color: var(--dark-accent);
    }

    .ai-tips {
      background-color: rgba(255, 241, 0, 0.15);
      padding: 20px;
      border-radius: var(--border-radius-md);
      margin-bottom: 20px;
      border-left: 4px solid #ffd700;
      animation: pulse 2s infinite;
    }

    body.dark-mode .ai-tips {
      background-color: rgba(255, 241, 0, 0.1);
    }

    .ai-tips h3 {
      color: #b8860b;
      border-bottom: none;
      padding-bottom: 0;
    }

    footer {
      background: var(--nav-color);
      color: white;
      text-align: center;
      padding: 30px 0;
      margin-top: 60px;
      font-size: 0.9rem;
      position: relative;
    }

    body.dark-mode footer {
      background: var(--dark-nav-color);
    }

    footer::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 3px;
      background: var(--primary-gradient);
    }

    footer p {
      margin: 0;
      opacity: 0.8;
    }

    /* =========================
       PREMIUM SIDEBAR STYLES
       ========================= */
    .sidebar {
      position: fixed;
      top: 0;
      left: -320px;
      width: 300px;
      height: 100vh;
      background: var(--sidebar-bg);
      color: white;
      transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
      z-index: 1000;
      box-shadow: 10px 0 30px rgba(0, 0, 0, 0.2);
      overflow-y: auto;
    }
    
    body.dark-mode .sidebar {
      background: var(--dark-sidebar-bg);
    }
    
    .sidebar.open {
      left: 0;
    }
    
    .sidebar-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 25px;
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
      background: rgba(0, 0, 0, 0.2);
      position: relative;
      overflow: hidden;
    }
    
    .sidebar-header::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, rgba(67, 97, 238, 0.2), rgba(58, 12, 163, 0.2));
    }
    
    .sidebar-close {
      color: white;
      font-size: 1.5rem;
      cursor: pointer;
      transition: all 0.3s ease;
      z-index: 1;
    }
    
    .sidebar-close:hover {
      transform: rotate(90deg);
      color: var(--accent-color);
    }
    
    .sidebar-menu {
      padding: 20px 0;
      height: calc(100vh - 60px);
      overflow-y: auto;
    }
    
    .sidebar-title {
      padding: 15px 25px;
      font-size: 0.8rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      color: rgba(255, 255, 255, 0.5);
      margin-top: 15px;
    }
    
    .sidebar-item {
      display: flex;
      align-items: center;
      padding: 15px 25px;
      color: white;
      text-decoration: none;
      transition: all 0.3s ease;
      position: relative;
      overflow: hidden;
      margin: 5px 10px;
      border-radius: var(--border-radius-md);
    }
    
    .sidebar-item::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
      transition: all 0.6s ease;
    }
    
    .sidebar-item:hover {
      background: rgba(255, 255, 255, 0.1);
      color: #ffffff;
      transform: translateX(5px);
    }
    
    .sidebar-item:hover::before {
      left: 100%;
    }
    
    .sidebar-item i {
      font-size: 1.2rem;
      margin-right: 15px;
      width: 24px;
      text-align: center;
    }
    
    /* Hamburger menu */
    .menu-toggle {
      position: fixed;
      top: 20px;
      left: 20px;
      width: 50px;
      height: 50px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      z-index: 999;
      background: rgba(255, 255, 255, 0.95);
      border-radius: 50%;
      box-shadow: var(--shadow-md);
      transition: all 0.3s ease;
    }
    
    body.dark-mode .menu-toggle {
      background: rgba(30, 30, 46, 0.95);
    }
    
    .menu-toggle:hover {
      transform: scale(1.1);
      box-shadow: var(--shadow-lg);
    }
    
    .menu-toggle span {
      display: block;
      width: 25px;
      height: 3px;
      background: #333;
      margin: 4px 0;
      transition: all 0.3s ease;
      border-radius: 3px;
    }
    
    body.dark-mode .menu-toggle span {
      background: var(--dark-text-color);
    }
    
    /* Overlay */
    .overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.5);
      z-index: 999;
      opacity: 0;
      visibility: hidden;
      transition: all 0.3s ease;
      backdrop-filter: blur(5px);
    }
    
    .overlay.active {
      opacity: 1;
      visibility: visible;
    }
    
    /* Premium Modal */
    .modal {
      display: none;
      position: fixed;
      z-index: 1001;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.5);
      animation: fadeIn 0.3s ease-out;
    }
    
    .modal-content {
      background-color: #fefefe;
      margin: 15% auto;
      padding: 30px;
      border-radius: var(--border-radius-lg);
      width: 90%;
      max-width: 500px;
      box-shadow: var(--shadow-xxl);
      transform: scale(0.9);
      opacity: 0;
      transition: all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
      border-top: 5px solid var(--accent-color);
      position: relative;
      overflow: hidden;
    }
    
    body.dark-mode .modal-content {
      background-color: var(--dark-card-bg);
      color: var(--dark-text-color);
    }
    
    .modal-content::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 5px;
      background: var(--accent-gradient);
    }
    
    .modal.show .modal-content {
      transform: scale(1);
      opacity: 1;
    }
    
    .modal-header h3 {
      color: var(--accent-color);
      font-size: 1.5rem;
      margin-top: 0;
      border-bottom: 2px solid #eee;
      padding-bottom: 10px;
      display: flex;
      align-items: center;
    }
    
    body.dark-mode .modal-header h3 {
      color: var(--dark-accent);
      border-bottom-color: var(--dark-border-color);
    }
    
    .modal-header h3 i {
      margin-right: 10px;
    }
    
    .modal-body {
      padding: 20px 0;
      line-height: 1.6;
      color: var(--text-color);
    }
    
    body.dark-mode .modal-body {
      color: var(--dark-text-color);
    }
    
    .modal-buttons {
      margin-top: 25px;
      display: flex;
      justify-content: flex-end;
      gap: 15px;
    }
    
    .modal-btn {
      padding: 12px 25px;
      border-radius: var(--border-radius-xl);
      cursor: pointer;
      font-weight: 600;
      transition: all 0.3s ease;
      display: inline-flex;
      align-items: center;
    }
    
    .modal-btn i {
      margin-right: 8px;
    }
    
    .modal-btn.confirm {
      background: var(--danger-gradient);
      color: white;
      border: none;
      box-shadow: var(--shadow-md);
    }
    
    .modal-btn.confirm:hover {
      transform: translateY(-2px);
      box-shadow: var(--shadow-lg);
    }
    
    .modal-btn.cancel {
      background: linear-gradient(135deg, #9c27b0 0%, #673ab7 100%); /* Light gray gradient */
      color: white; 
      border: none;
      padding: 12px 30px;
      border-radius: 50px;
      font-weight: 600;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
    }

    .modal-btn.cancel::before {
      content: ' ';
      position: absolute;
      top: -2px;
      left: -2px;
      right: -2px;
      bottom: -2px;
      background: linear-gradient(135deg, #9c27b0 0%, #673ab7 100%);
      border-radius: 50px;
      z-index: -1;
      opacity: 5;
      transition: all 0.3s ease;
    }

    .modal-btn.cancel:hover {
      background: linear-gradient(135deg, #e4e8eb 0%, #d1d5d8 100%); /* Darker gray gradient */
      color: white;
      transform: translateY(-2px);
      box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
    }

    .modal-btn.cancel:active {
      transform: translateY(0);
    }

    /* =========================
       PREMIUM AUTH PAGES - MODERN ABSTRACT STYLE
       ========================= */
    .auth-page {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: 
        linear-gradient(rgba(12, 13, 46, 0.9), rgba(12, 13, 46, 0.9)),
        url('https://images.unsplash.com/photo-1639762681057-408e52192e55?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2232&q=80') no-repeat center center;
      background-size: cover;
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 9999;
      overflow: hidden;
    }
    
    .auth-container {
      position: relative;
      width: 100%;
      max-width: 450px;
      padding: 50px 40px;
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(15px);
      border-radius: var(--border-radius-xl);
      box-shadow: var(--shadow-xxl);
      border: 1px solid rgba(255, 255, 255, 0.2);
      border-right: 1px solid rgba(255, 255, 255, 0.1);
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
      overflow: hidden;
      animation: fadeIn 0.8s cubic-bezier(0.39, 0.575, 0.565, 1);
    }
    
    .auth-container::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(
        90deg,
        transparent,
        rgba(255, 255, 255, 0.2),
        transparent
      );
      transition: 0.5s;
    }
    
    .auth-container:hover::before {
      left: 100%;
    }
    
    .auth-form {
      position: relative;
      width: 100%;
      display: flex;
      flex-direction: column;
      gap: 25px;
      align-items: center;
      z-index: 10;
    }
    
    .auth-form h2 {
      color: #fff;
      font-size: 2.5rem;
      font-weight: 700;
      letter-spacing: 1px;
      margin-bottom: 20px;
      text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
      position: relative;
      background: linear-gradient(to right, #fff, #c1c8ff);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      text-align: right;
      width: 100%;
      padding-bottom: 0;
    }
    
    /* Remove the ::after pseudo-element that created the gradient line */
    .auth-form h2::after {
      display: none;
    }
    
    .inputBx {
      position: relative;
      width: 100%;
      max-width: 350px;
    }
    
    .inputBx input {
      width: 100%;
      padding: 15px 25px;
      background: rgba(255, 255, 255, 0.2);
      border: none;
      border-radius: var(--border-radius-xl);
      font-size: 1.1rem;
      color: #fff;
      outline: none;
      transition: all 0.5s ease;
      box-shadow: var(--shadow-md);
      backdrop-filter: blur(5px);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }
    
    .inputBx input:focus {
      border-color: #fff;
      box-shadow: 0 0 15px rgba(255, 255, 255, 0.3);
      transform: translateY(-2px);
    }
    
    .inputBx input[type="submit"] {
      background: linear-gradient(45deg, #4cc9f0, #4895ef);
      border: none;
      cursor: pointer;
      font-weight: 600;
      letter-spacing: 1px;
      transition: all 0.5s ease;
      box-shadow: 0 5px 20px rgba(76, 201, 240, 0.4);
      margin-top: 10px;
      width: 100%;
      max-width: 350px;
    }
    
    .inputBx input[type="submit"]:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 25px rgba(76, 201, 240, 0.5);
      background: linear-gradient(45deg, #4895ef, #4cc9f0);
    }
    
    .inputBx input::placeholder {
      color: rgba(255, 255, 255, 0.8);
    }
    
    .links {
      width: 100%;
      max-width: 350px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 10px;
    }
    
    .links a {
      color: #fff;
      text-decoration: none;
      font-size: 0.9rem;
      transition: all 0.3s ease;
      opacity: 0.8;
      position: relative;
      padding: 5px 0;
    }
    
    .links a:hover {
      opacity: 1;
      text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
    }
    
    .links a::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 0;
      height: 2px;
      background: #fff;
      transition: width 0.3s ease;
    }
    
    .links a:hover::after {
      width: 100%;
    }
    
    /* Error messages */
    .error-message {
      color: #ff4444;
      font-size: 0.9rem;
      margin-top: 8px;
      display: none;
      padding-left: 15px;
      animation: fadeIn 0.3s ease-out;
      text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
      text-align: left;
      width: 100%;
    }
    
    body.dark-mode .error-message {
      color: var(--dark-error-color);
    }
    
    /* Password reset page */
    .reset-form {
      display: flex;
      flex-direction: column;
      gap: 50px;
      width: 100%;
      align-items: right;
    }
    
    .reset-form h3 {
      color: #fff;
      text-align: center;
      margin-bottom: 15px;
      font-weight: 300;
      letter-spacing: 1px;
      font-size: 1.1rem;
      width: 100%;
    }
    
    .reset-steps {
      display: flex;
      flex-direction: column;
      gap: 20px;
      width: 100%;
      align-items: center;
    }
    
    .reset-step {
      display: none;
      animation: fadeIn 0.5s ease-out;
      width: 100%;
    }
    
    .reset-step.active {
      display: flex;
      flex-direction: column;
      gap: 20px;
      width: 100%;
      align-items: center;
    }
    
    /* Abstract floating shapes */
    .floating-shapes {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      z-index: 1;
      overflow: hidden;
    }
    
    .shape {
      position: absolute;
      border-radius: 50%;
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(5px);
      animation: float 15s infinite linear;
      opacity: 0.6;
    }
    
    .shape:nth-child(1) {
      width: 100px;
      height: 100px;
      top: 20%;
      left: 10%;
      animation-duration: 20s;
      animation-delay: 0s;
      background: linear-gradient(45deg, rgba(255,0,150,0.1), rgba(0,200,255,0.1));
    }
    
    .shape:nth-child(2) {
      width: 150px;
      height: 150px;
      top: 60%;
      left: 70%;
      animation-duration: 25s;
      animation-delay: 2s;
      background: linear-gradient(45deg, rgba(0,200,255,0.1), rgba(255,255,0,0.1));
    }
    
    .shape:nth-child(3) {
      width: 80px;
      height: 80px;
      top: 80%;
      left: 20%;
      animation-duration: 15s;
      animation-delay: 1s;
      background: linear-gradient(45deg, rgba(255,255,0,0.1), rgba(255,0,150,0.1));
    }
    
    .shape:nth-child(4) {
      width: 120px;
      height: 120px;
      top: 30%;
      left: 80%;
      animation-duration: 30s;
      animation-delay: 3s;
      background: linear-gradient(45deg, rgba(0,255,200,0.1), rgba(0,200,255,0.1));
    }
    
    /* Hidden class */
    .hidden {
      display: none;
    }
    
    /* =========================
       DRAFTS PAGE STYLES
       ========================= */
    .drafts-container {
      max-width: 800px;
      margin: 40px auto;
      background: var(--card-bg);
      padding: 40px;
      border-radius: var(--border-radius-lg);
      box-shadow: var(--shadow-lg);
      backdrop-filter: blur(5px);
      border: 1px solid var(--border-color);
      animation: fadeIn 0.6s ease-out;
    }
    
    body.dark-mode .drafts-container {
      background: var(--dark-card-bg);
      border-color: var(--dark-border-color);
    }
    
    .drafts-container button.secondary {
      margin-top: 15px;
    }
    
    .draft-item {
      background: rgba(241, 249, 245, 0.9);
      padding: 20px;
      margin-bottom: 20px;
      border-radius: var(--border-radius-md);
      border: 1px solid var(--border-color);
      transition: all 0.3s ease;
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }
    
    body.dark-mode .draft-item {
      background: var(--dark-card-bg);
      border-color: var(--dark-border-color);
    }
    
    .draft-item::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 5px;
      height: 100%;
      background: var(--primary-gradient);
    }
    
    .draft-item:hover {
      transform: translateY(-3px);
      box-shadow: var(--shadow-md);
    }
    
    .draft-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 15px;
      border-bottom: 1px solid var(--border-color);
      padding-bottom: 10px;
    }
    
    body.dark-mode .draft-header {
      border-bottom-color: var(--dark-border-color);
    }
    
    .draft-title {
      font-size: 1.2rem;
      font-weight: 600;
      color: var(--nav-color);
    }
    
    body.dark-mode .draft-title {
      color: var(--dark-text-light);
    }
    
    .draft-date {
      font-size: 0.9rem;
      color: #777;
    }
    
    body.dark-mode .draft-date {
      color: rgba(255, 255, 255, 0.6);
    }
    
    .draft-preview {
      display: flex;
      gap: 20px;
    }
    
    .draft-income, .draft-expenses {
      flex: 1;
    }
    
    .draft-label {
      font-size: 0.9rem;
      color: #555;
      margin-bottom: 5px;
    }
    
    body.dark-mode .draft-label {
      color: rgba(255, 255, 255, 0.7);
    }
    
    .draft-value {
      font-size: 1.1rem;
      font-weight: 600;
      color: var(--text-color);
    }
    
    body.dark-mode .draft-value {
      color: var(--dark-text-color);
    }
    
    .draft-actions {
      display: flex;
      justify-content: flex-end;
      margin-top: 15px;
    }
    
    .delete-draft-btn {
      background: var(--danger-gradient);
      color: white;
      border: none;
      padding: 8px 15px;
      border-radius: var(--border-radius-md);
      font-size: 0.9rem;
      cursor: pointer;
      transition: all 0.3s ease;
      display: inline-flex;
      align-items: center;
      gap: 5px;
    }
    
    .delete-draft-btn:hover {
      transform: translateY(-2px);
      box-shadow: var(--shadow-sm);
    }
    
    .no-drafts {
      text-align: center;
      padding: 40px 20px;
      color: #777;
      font-size: 1.1rem;
    }
    
    body.dark-mode .no-drafts {
      color: rgba(255, 255, 255, 0.6);
    }
    
    /* =========================
       SETTINGS PAGE STYLES
       ========================= */
    .settings-container {
      max-width: 800px;
      margin: 40px auto;
      background: var(--card-bg);
      padding: 40px;
      border-radius: var(--border-radius-lg);
      box-shadow: var(--shadow-lg);
      backdrop-filter: blur(5px);
      border: 1px solid var(--border-color);
      animation: fadeIn 0.6s ease-out;
    }
    
    body.dark-mode .settings-container {
      background: var(--dark-card-bg);
      border-color: var(--dark-border-color);
    }
    
    .settings-section {
      margin-bottom: 30px;
      padding-bottom: 20px;
      border-bottom: 1px solid var(--border-color);
    }
    
    body.dark-mode .settings-section {
      border-bottom-color: var(--dark-border-color);
    }
    
    .settings-section:last-child {
      border-bottom: none;
      margin-bottom: 0;
      padding-bottom: 0;
    }
    
    .settings-section h3 {
      color: var(--nav-color);
      margin-bottom: 20px;
      font-size: 1.3rem;
      display: flex;
      align-items: center;
    }
    
    body.dark-mode .settings-section h3 {
      color: var(--dark-text-light);
    }
    
    .settings-section h3 i {
      margin-right: 10px;
      color: var(--success-color);
    }
    
    body.dark-mode .settings-section h3 i {
      color: var(--dark-success-color);
    }
    
    .settings-option {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 15px;
      padding: 15px;
      background: rgba(241, 249, 245, 0.9);
      border-radius: var(--border-radius-md);
      transition: all 0.3s ease;
    }
    
    body.dark-mode .settings-option {
      background: var(--dark-card-bg);
    }
    
    .settings-option:hover {
      background: rgba(241, 249, 245, 1);
      transform: translateY(-2px);
      box-shadow: var(--shadow-sm);
    }
    
    body.dark-mode .settings-option:hover {
      background: rgba(30, 30, 46, 0.8);
    }
    
    .option-info {
      flex: 1;
    }
    
    .option-title {
      font-weight: 600;
      margin-bottom: 5px;
      color: var(--text-color);
    }
    
    body.dark-mode .option-title {
      color: var(--dark-text-light);
    }
    
    .option-description {
      font-size: 0.9rem;
      color: #777;
    }
    
    body.dark-mode .option-description {
      color: rgba(255, 255, 255, 0.7);
    }
    
    .option-control select {
      padding: 10px 15px;
      border: 2px solid var(--border-color);
      border-radius: var(--border-radius-md);
      font-size: 1rem;
      transition: all 0.3s ease;
      background: var(--input-bg);
      min-width: 150px;
      font-family: 'Poppins', sans-serif;
      color: var(--text-color);
    }
    
    body.dark-mode .option-control select {
      background: var(--dark-input-bg);
      color: var(--dark-text-color);
      border-color: var(--dark-border-color);
    }
    
    .option-control select:focus {
      border-color: #4361ee;
      box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.2);
      outline: none;
    }
    
    body.dark-mode .option-control select:focus {
      border-color: var(--dark-accent);
      box-shadow: 0 0 0 3px rgba(247, 37, 133, 0.2);
    }
    
    /* =========================
       USER PROFILE PAGE STYLES
       ========================= */
    .profile-container {
      max-width: 600px;
      margin: 40px auto;
      background: var(--card-bg);
      padding: 40px;
      border-radius: var(--border-radius-lg);
      box-shadow: var(--shadow-lg);
      backdrop-filter: blur(5px);
      border: 1px solid var(--border-color);
      animation: fadeIn 0.6s ease-out;
      position: relative;
      overflow: hidden;
    }
    
    body.dark-mode .profile-container {
      background: var(--dark-card-bg);
      border-color: var(--dark-border-color);
    }
    
    .profile-container::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 5px;
      background: var(--primary-gradient);
    }
    
    .profile-header {
      display: flex;
      align-items: center;
      gap: 20px;
      margin-bottom: 30px;
    }
    
    .profile-header img {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      border: 3px solid var(--primary-gradient);
      object-fit: cover;
      box-shadow: var(--shadow-md);
    }
    
    .profile-header-text {
      display: flex;
      flex-direction: column;
    }
    
    .profile-header-text h2 {
      color: var(--nav-color);
      margin: 0 0 5px 0;
      font-size: 1.5rem;
      left: 0;
      transform: none;
      padding-bottom: 0;
    }
    
    body.dark-mode .profile-header-text h2 {
      color: var(--dark-text-light);
    }
    
    .profile-header-text h2::after {
      display: none;
    }
    
    .profile-details {
      margin-bottom: 30px;
    }
    
    .profile-detail {
      display: flex;
      margin-bottom: 15px;
      padding-bottom: 15px;
      border-bottom: 1px solid var(--border-color);
      align-items: center;
    }

    body.dark-mode .profile-detail {
      border-bottom-color: var(--dark-border-color);
    }

    .detail-label {
      width: 120px;
      font-weight: 600;
      color: #555;
      margin-right: 20px;
    }

    body.dark-mode .detail-label {
      color: rgba(255, 255, 255, 0.7);
    }

    .detail-value {
      flex: 1;
      color: var(--text-color);
      word-break: break-word;
    }
    
    body.dark-mode .detail-value {
      color: var(--dark-text-light);
    }
    
    /* Gmail/Email specific styling */
    .profile-detail.email .detail-value {
      color: #d44638;
      font-weight: 500;
    }
    
    body.dark-mode .profile-detail.email .detail-value {
      color: #ff6b6b;
    }
    
    /* Member since styling */
    .profile-detail.member-since .detail-value {
      color: #666;
      font-style: italic;
    }
    
    body.dark-mode .profile-detail.member-since .detail-value {
      color: rgba(255, 255, 255, 0.6);
    }
    
    /* Responsive adjustments */
    @media (max-width: 768px) {
      header h1 {
        font-size: 2rem;
      }
      
      header p {
        font-size: 1rem;
      }
      
      nav a {
        font-size: 0.9rem;
        margin: 0 10px;
        padding: 8px 15px;
      }
      
      section {
        margin: 20px;
        padding: 25px;
      }
      
      .form-group input,
      .form-group textarea {
        font-size: 0.9rem;
        padding: 12px 18px;
      }
      
      button {
        font-size: 1rem;
        padding: 12px 25px;
      }
      
      canvas {
        width: 100%;
        height: 250px;
      }
      
      #ai-insights {
        padding: 20px;
      }
      
      /* Auth page responsive adjustments */
      .auth-container {
        width: 90%;
        padding: 40px 20px;
      }
      
      .auth-form h2 {
        font-size: 2rem;
      }
      
      .inputBx input {
        padding: 12px 20px;
      }
      
      .links {
        flex-direction: column;
        gap: 10px;
        align-items: center;
      }
      
      .sidebar {
        width: 280px;
      }
      
      .drafts-container,
      .settings-container,
      .profile-container {
        margin: 20px;
        padding: 25px;
      }
      
      .draft-preview {
        flex-direction: column;
        gap: 10px;
      }
      
      .profile-detail {
        flex-direction: column;
        align-items: flex-start;
      }
      
      .detail-label {
        width: 100%;
        margin-bottom: 5px;
      }
      
      .profile-header img {
        width: 60px;
        height: 60px;
      }
      
      .profile-header h2 {
        font-size: 1.3rem;
      }
    }
    
    @media (min-width: 769px) {
      section {
        padding: 40px;
      }
      
      canvas {
        width: 80%;
        height: 400px;
      }
    }
  </style>
</head>
<body>
  <!-- SIDEBAR -->
  <div class="sidebar" id="sidebar">
    <div class="sidebar-header">
      <h3 style="color: white; margin: 0; z-index: 1;">Dashboard</h3>
      <div class="sidebar-close" onclick="toggleSidebar()">
        <i class="fas fa-times"></i>
      </div>
    </div>
    
    <div class="sidebar-menu">
      <div class="sidebar-title">Main</div>
      <a href="#" class="sidebar-item" onclick="showAppPage(); toggleSidebar()">
        <i class="fas fa-home"></i>
        <span>Home</span>
      </a>
      <a href="#" class="sidebar-item" onclick="showUserProfile(); toggleSidebar()">
        <i class="fas fa-user"></i>
        <span>Profile</span>
      </a>
      
      <div class="sidebar-title">Tools</div>
      <a href="#" class="sidebar-item" onclick="exportData(); toggleSidebar()">
        <i class="fas fa-file-export"></i>
        <span>Export Data</span>
      </a>
      <a href="#" class="sidebar-item" onclick="importData(); toggleSidebar()">
        <i class="fas fa-file-import"></i>
        <span>Import Data</span>
      </a>
      <a href="#" class="sidebar-item" onclick="downloadActivityLog(); toggleSidebar()">
        <i class="fas fa-history"></i>
        <span>Activity Log</span>
      </a>
      <a href="#" class="sidebar-item" onclick="showDrafts(); toggleSidebar()">
        <i class="fas fa-file-alt"></i>
        <span>Drafts</span>
      </a>
      
      <div class="sidebar-title">Account</div>
      <a href="#" class="sidebar-item" onclick="showSettings(); toggleSidebar()">
        <i class="fas fa-cog"></i>
        <span>Settings</span>
      </a>
      <a href="#" class="sidebar-item" onclick="showDeleteAccountModal(); toggleSidebar()">
        <i class="fas fa-trash-alt"></i>
        <span>Delete Account</span>
      </a>
    </div>
  </div>
  
  <!-- OVERLAY -->
  <div class="overlay" id="overlay" onclick="toggleSidebar()"></div>
  
  <!-- HAMBURGER MENU -->
  <div class="menu-toggle" id="menuToggle" onclick="toggleSidebar()">
    <span></span>
    <span></span>
    <span></span>
  </div>

  <!-- LOGIN PAGE -->
  <div id="loginPage" class="auth-page">
    <div class="auth-container">
      <!-- Floating abstract shapes -->
      <div class="floating-shapes">
        <div class="shape"></div>
        <div class="shape"></div>
        <div class="shape"></div>
        <div class="shape"></div>
      </div>
      
      <div class="auth-form">
        <h2>Welcome</h2>
        <div class="inputBx">
          <input type="text" placeholder="Username" id="loginUsername" />
          <div id="loginUsernameError" class="error-message">Username is required</div>
        </div>
        <div class="inputBx">
          <input type="password" placeholder="Password" id="loginPassword" />
          <div id="loginPasswordError" class="error-message">Password is required</div>
        </div>
        <div class="inputBx">
          <input type="submit" value="Sign in" onclick="login()" />
        </div>
        <div class="links">
          <a href="#" onclick="showRegisterPage()">Create Account</a>
          <a href="#" onclick="showForgotPasswordPage()">Forgot Password?</a>
        </div>
      </div>
    </div>
  </div>

  <!-- REGISTER PAGE -->
  <div id="registerPage" class="auth-page hidden">
    <div class="auth-container">
      <!-- Floating abstract shapes -->
      <div class="floating-shapes">
        <div class="shape"></div>
        <div class="shape"></div>
        <div class="shape"></div>
        <div class="shape"></div>
      </div>
      
      <div class="auth-form">
        <h2>Create Account</h2>
        <div class="inputBx">
          <input type="text" placeholder="Username" id="regUsername" />
          <div id="regUsernameError" class="error-message">Username is required</div>
        </div>
        <div class="inputBx">
          <input type="email" placeholder="Email" id="regEmail" />
          <div id="regEmailError" class="error-message">Valid email is required</div>
        </div>
        <div class="inputBx">
          <input type="password" placeholder="Password" id="regPassword" />
          <div id="regPasswordError" class="error-message">Password must be at least 8 characters</div>
        </div>
        <div class="inputBx">
          <input type="password" placeholder="Confirm Password" id="regConfirmPassword" />
          <div id="regConfirmPasswordError" class="error-message">Passwords must match</div>
        </div>
        <div class="inputBx">
          <input type="submit" value="Register" onclick="register()" />
        </div>
        <div class="links">
          <a href="#" onclick="showLoginPage()">Already have an account? Login</a>
        </div>
      </div>
    </div>
  </div>

  <!-- FORGOT PASSWORD PAGE -->
  <div id="forgotPasswordPage" class="auth-page hidden">
    <div class="auth-container">
      <!-- Floating abstract shapes -->
      <div class="floating-shapes">
        <div class="shape"></div>
        <div class="shape"></div>
        <div class="shape"></div>
        <div class="shape"></div>
      </div>
      
      <div class="auth-form">
        <div class="reset-form">
          <h2>Reset Password</h2>
          
          <!-- Step 1: Enter Email -->
          <div id="resetStep1" class="reset-step active">
            <h3>Enter your registered email address</h3>
            <div class="inputBx">
              <input type="email" placeholder="Email" id="resetEmail" />
              <div id="resetEmailError" class="error-message">Valid email is required</div>
            </div>
            <div class="inputBx">
              <input type="submit" value="Send Reset Link" onclick="verifyResetEmail()" />
            </div>
            <div class="links">
              <a href="#" onclick="showLoginPage()">Back to Login</a>
            </div>
          </div>
          
          <!-- Step 2: Enter New Password -->
          <div id="resetStep2" class="reset-step">
            <h3>Create New Password</h3>
            <div class="inputBx">
              <input type="password" placeholder="New Password" id="newPassword" />
              <div id="newPasswordError" class="error-message">Password must be at least 8 characters</div>
            </div>
            <div class="inputBx">
              <input type="password" placeholder="Confirm New Password" id="confirmNewPassword" />
              <div id="confirmNewPasswordError" class="error-message">Passwords must match</div>
            </div>
            <div class="inputBx">
              <input type="submit" value="Update Password" onclick="resetPassword()" />
            </div>
            <div class="links">
              <a href="#" onclick="showLoginPage()">Back to Login</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- USER PROFILE PAGE -->
  <div id="userProfilePage" class="hidden">
    <div class="profile-container">
      <div class="profile-header">
        <img src="https://cdn-icons-png.flaticon.com/512/149/149071.png" alt="Profile Picture">
        <div class="profile-header-text">
          <h2 id="profileUsernameDisplay">Username</h2>
        </div>
      </div>
      
      <div class="profile-details">
        <div class="profile-detail">
          <div class="detail-label">Username:</div>
          <div class="detail-value" id="profileUsername">username</div>
        </div>
        <div class="profile-detail email">
          <div class="detail-label">Email:</div>
          <div class="detail-value" id="profileEmail">user@example.com</div>
        </div>
        <div class="profile-detail member-since">
          <div class="detail-label">Member since:</div>
          <div class="detail-value" id="profileCreatedAt">January 1, 2023</div>
        </div>
      </div>
      
      <button onclick="logout()" class="danger" style="margin-top: 20px;">
        <i class="fas fa-sign-out-alt"></i> Logout
      </button>
      <button onclick="showAppPage()" class="secondary" style="margin-top: 15px;">
        <i class="fas fa-arrow-left"></i> Back to Home
      </button>
    </div>
  </div>

  <!-- SETTINGS PAGE -->
  <div id="settingsPage" class="hidden">
    <div class="settings-container">
      <h2><i class="fas fa-cog"></i> Settings</h2>
      
      <div class="settings-section">
        <h3><i class="fas fa-palette"></i> Appearance</h3>
        
        <div class="settings-option">
          <div class="option-info">
            <div class="option-title">Theme</div>
            <div class="option-description">Choose between light, dark or system default</div>
          </div>
          <div class="option-control">
            <select id="themeSelect">
              <option value="system">System Default</option>
              <option value="light">Light Mode</option>
              <option value="dark">Dark Mode</option>
            </select>
          </div>
        </div>
      </div>
      
      <div class="settings-section">
        <h3><i class="fas fa-bell"></i> Notifications</h3>
        
        <div class="settings-option">
          <div class="option-info">
            <div class="option-title">Email Notifications</div>
            <div class="option-description">Receive email alerts for important updates</div>
          </div>
          <div class="option-control">
            <select id="emailNotifications">
              <option value="enabled">Enabled</option>
              <option value="disabled">Disabled</option>
            </select>
          </div>
        </div>
        
        <div class="settings-option">
          <div class="option-info">
            <div class="option-title">Budget Alerts</div>
            <div class="option-description">Get notified when approaching budget limits</div>
          </div>
          <div class="option-control">
            <select id="budgetAlerts">
              <option value="enabled">Enabled</option>
              <option value="disabled">Disabled</option>
            </select>
          </div>
        </div>
      </div>
      
      <div class="settings-section">
        <h3><i class="fas fa-shield-alt"></i> Security</h3>
        
        <div class="settings-option">
          <div class="option-info">
            <div class="option-title">Two-Factor Authentication</div>
            <div class="option-description">Add an extra layer of security to your account</div>
          </div>
          <div class="option-control">
            <select id="twoFactorAuth">
              <option value="disabled">Disabled</option>
              <option value="enabled">Enabled</option>
            </select>
          </div>
        </div>
        
        <div class="settings-option">
          <div class="option-info">
            <div class="option-title">Auto Logout</div>
            <div class="option-description">Automatically logout after period of inactivity</div>
          </div>
          <div class="option-control">
            <select id="autoLogout">
              <option value="15">15 minutes</option>
              <option value="30">30 minutes</option>
              <option value="60">1 hour</option>
              <option value="0">Never</option>
            </select>
          </div>
        </div>
      </div>
      
      <button onclick="saveSettings()"><i class="fas fa-save"></i> Save Settings</button>
      <button onclick="showAppPage()" class="secondary" style="margin-top: 15px;">
        <i class="fas fa-arrow-left"></i> Back to Home
      </button>
    </div>
  </div>

  <!-- DRAFTS PAGE -->
  <div id="draftsPage" class="hidden">
    <div class="drafts-container">
      <h2><i class="fas fa-file-alt"></i> Your Drafts</h2>
      
      <div id="draftsList">
        <!-- Draft items will be added here dynamically -->
      </div>
      
      <button onclick="showAppPage()" class="secondary">
        <i class="fas fa-arrow-left"></i> Back to Home
      </button>
    </div>
  </div>

  <!-- PERSONAL FINANCE MANAGEMENT TOOL CONTENT (hidden until login) -->
  <div id="app" class="hidden">
    <header>
      <h1>Personal Finance Management Tool</h1>
      <p>AI-Powered Budget Tracking &amp; Expense Guidance</p>
      <p>Welcome, <span id="usernameDisplay" style="cursor: pointer;" onclick="showUserProfile()"></span>!</p>
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
      <button onclick="setIncome()"><i class="fas fa-paper-plane"></i> Submit Income</button>
    </section>
    <section id="expense-section">
      <h2>Track Your Expenses</h2>
      <div class="form-group">
        <label for="expenses">List Your Expenses (separated by commas):</label>
        <textarea id="expenses" rows="4" placeholder="e.g., Rent:5000, Groceries:3000, Utilities:2000"></textarea>
      </div>
      <button onclick="trackExpenses()"><i class="fas fa-paper-plane"></i> Submit Expenses</button>
    </section>
    <section id="results-section">
      <h2>AI-Powered Guidance</h2>
      <div class="results" id="results">
        <p>No data entered yet. Submit your income and expenses to see results!</p>
      </div>
      <canvas id="expenseChart"></canvas>
      <div id="ai-insights">
        <h3><i class="fas fa-lightbulb"></i> Suggestions</h3>
        <p id="suggestion-text"></p>
        <div class="ai-tips">
          <h3><i class="fas fa-magic"></i> AI-Powered Tips</h3>
          <p id="tips-text"></p>
        </div>
        <h3><i class="fas fa-exclamation-triangle"></i> Problem</h3>
        <p id="problem-text"></p>
        <h3><i class="fas fa-check-circle"></i> Solution</h3>
        <p id="solution-text"></p>
      </div>
    </section>
    <footer>
      <p>&copy; 2025 Personal Finance Management Tool | AI-Powered Budget Guidance</p>
    </footer>
  </div>

  <!-- Delete Account Confirmation Modal -->
  <div id="deleteAccountModal" class="modal">
    <div class="modal-content">
      <div class="modal-header">
        <h3><i class="fas fa-exclamation-triangle"></i> Delete Account</h3>
      </div>
      <div class="modal-body">
        <p>Are you sure you want to delete your account? This action cannot be undone and all your data will be permanently lost.</p>
      </div>
      <div class="modal-buttons">
        <button class="modal-btn cancel" onclick="closeModal()"><i class="fas fa-times"></i> Cancel</button>
        <button class="modal-btn confirm" onclick="deleteAccount()"><i class="fas fa-trash-alt"></i> Delete Account</button>
      </div>
    </div>
  </div>

  <!-- Hidden elements for file operations -->
  <textarea id="fileExport" class="hidden"></textarea>
  <input type="file" id="fileImport" class="hidden" accept=".txt" />

  <script>
    // -------------------------------------------------------
    // SIDEBAR TOGGLE FUNCTIONALITY
    // -------------------------------------------------------
    function toggleSidebar() {
      const sidebar = document.getElementById('sidebar');
      const overlay = document.getElementById('overlay');
      const menuToggle = document.getElementById('menuToggle');
      
      sidebar.classList.toggle('open');
      overlay.classList.toggle('active');
      
      // Show modal animation
      if (sidebar.classList.contains('open')) {
        document.querySelectorAll('.sidebar-item').forEach((item, index) => {
          item.style.transitionDelay = `${index * 0.1}s`;
          item.style.opacity = '0';
          item.style.transform = 'translateX(-20px)';
          setTimeout(() => {
            item.style.opacity = '1';
            item.style.transform = 'translateX(0)';
          }, 100);
        });
      }
    }
    
    // Close sidebar when clicking outside
    document.addEventListener('click', function(event) {
      const sidebar = document.getElementById('sidebar');
      const menuToggle = document.getElementById('menuToggle');
      const overlay = document.getElementById('overlay');
      
      if (!sidebar.contains(event.target) && !menuToggle.contains(event.target) && overlay.classList.contains('active')) {
        toggleSidebar();
      }
    });
    
    // -------------------------------------------------------
    // MODAL FUNCTIONS
    // -------------------------------------------------------
    function showDeleteAccountModal() {
      const modal = document.getElementById('deleteAccountModal');
      modal.style.display = 'block';
      setTimeout(() => {
        modal.classList.add('show');
      }, 10);
    }
    
    function closeModal() {
      const modal = document.getElementById('deleteAccountModal');
      modal.classList.remove('show');
      setTimeout(() => {
        modal.style.display = 'none';
      }, 300);
    }
    
    // -------------------------------------------------------
    // USER PROFILE & SETTINGS
    // -------------------------------------------------------
    function showUserProfile() {
      const username = localStorage.getItem('currentUser');
      const users = JSON.parse(localStorage.getItem('financeUsers')) || {};
      const user = users[username];
      
      if (user) {
        document.getElementById('profileUsername').textContent = username;
        document.getElementById('profileUsernameDisplay').textContent = username;
        document.getElementById('profileEmail').textContent = user.email || 'Not provided';
        document.getElementById('profileCreatedAt').textContent = new Date(user.createdAt).toLocaleDateString();
        
        // Hide all pages
        document.getElementById('loginPage').classList.add('hidden');
        document.getElementById('registerPage').classList.add('hidden');
        document.getElementById('forgotPasswordPage').classList.add('hidden');
        document.getElementById('app').classList.add('hidden');
        document.getElementById('settingsPage').classList.add('hidden');
        document.getElementById('draftsPage').classList.add('hidden');
        
        // Show profile page
        document.getElementById('userProfilePage').classList.remove('hidden');
        logActivity('VIEWED_PROFILE');
      }
    }
    
    function showSettings() {
      // Hide all pages
      document.getElementById('loginPage').classList.add('hidden');
      document.getElementById('registerPage').classList.add('hidden');
      document.getElementById('forgotPasswordPage').classList.add('hidden');
      document.getElementById('app').classList.add('hidden');
      document.getElementById('userProfilePage').classList.add('hidden');
      document.getElementById('draftsPage').classList.add('hidden');
      
      // Show settings page
      document.getElementById('settingsPage').classList.remove('hidden');
      logActivity('VIEWED_SETTINGS');
      
      // Load current settings
      const username = localStorage.getItem('currentUser');
      const users = JSON.parse(localStorage.getItem('financeUsers')) || {};
      const user = users[username];
      
      if (user && user.settings) {
        document.getElementById('themeSelect').value = user.settings.theme || 'system';
        document.getElementById('emailNotifications').value = user.settings.emailNotifications || 'enabled';
        document.getElementById('budgetAlerts').value = user.settings.budgetAlerts || 'enabled';
        document.getElementById('twoFactorAuth').value = user.settings.twoFactorAuth || 'disabled';
        document.getElementById('autoLogout').value = user.settings.autoLogout || '30';
      }
    }
    
    function saveSettings() {
      const username = localStorage.getItem('currentUser');
      const users = JSON.parse(localStorage.getItem('financeUsers'));
      
      if (users && users[username]) {
          const selectedTheme = document.getElementById('themeSelect').value;
          
          users[username].settings = {
              theme: selectedTheme,
              emailNotifications: document.getElementById('emailNotifications').value,
              budgetAlerts: document.getElementById('budgetAlerts').value,
              twoFactorAuth: document.getElementById('twoFactorAuth').value,
              autoLogout: document.getElementById('autoLogout').value
          };
          
          localStorage.setItem('financeUsers', JSON.stringify(users));
          applyTheme(selectedTheme);
          alert('Settings saved successfully!');
          logActivity('SAVED_SETTINGS', users[username].settings);
        }
    }
    
    function applyTheme(theme) {
      // Remove all theme classes first
      document.body.classList.remove('dark-mode', 'light-mode');
      
      if (theme === 'system') {
          // Use system preference
          const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
          if (prefersDark) {
              document.body.classList.add('dark-mode');
          } else {
              document.body.classList.add('light-mode');
          }
      } else if (theme === 'dark') {
          document.body.classList.add('dark-mode');
      } else {
          document.body.classList.add('light-mode');
      }
      
      // Force redraw of chart if it exists
      if (expenseChart) {
        expenseChart.update();
      }
    }

    function setupThemeListener() {
      const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)');
      
      mediaQuery.addEventListener('change', (e) => {
          const username = localStorage.getItem('currentUser');
          if (username) {
              const users = JSON.parse(localStorage.getItem('financeUsers')) || {};
              const user = users[username];
              if (user && user.settings && user.settings.theme === 'system') {
                  applyTheme('system');
              }
          }
      });
    }
    
    function showDrafts() {
      // Hide all pages
      document.getElementById('loginPage').classList.add('hidden');
      document.getElementById('registerPage').classList.add('hidden');
      document.getElementById('forgotPasswordPage').classList.add('hidden');
      document.getElementById('app').classList.add('hidden');
      document.getElementById('userProfilePage').classList.add('hidden');
      document.getElementById('settingsPage').classList.add('hidden');
      
      // Show drafts page
      document.getElementById('draftsPage').classList.remove('hidden');
      logActivity('VIEWED_DRAFTS');
      
      const username = localStorage.getItem('currentUser');
      const users = JSON.parse(localStorage.getItem('financeUsers')) || {};
      const user = users[username];
      const draftsList = document.getElementById('draftsList');
      draftsList.innerHTML = '';
      
      if (user && user.drafts && user.drafts.length > 0) {
        user.drafts.forEach((draft, index) => {
          const draftItem = document.createElement('div');
          draftItem.className = 'draft-item';
          draftItem.innerHTML = `
            <div class="draft-header">
              <div class="draft-title">Draft ${index + 1}</div>
              <div class="draft-date">${new Date(draft.timestamp).toLocaleString()}</div>
            </div>
            <div class="draft-preview">
              <div class="draft-income">
                <div class="draft-label">Income</div>
                <div class="draft-value">₹${draft.income || 'Not set'}</div>
              </div>
              <div class="draft-expenses">
                <div class="draft-label">Expenses</div>
                <div class="draft-value">${draft.expenses ? draft.expenses.split(',').length + ' items' : 'Not set'}</div>
              </div>
            </div>
            <div class="draft-actions">
              <button class="delete-draft-btn" onclick="deleteDraft(event, ${index})">
                <i class="fas fa-trash-alt"></i> Delete Draft
              </button>
            </div>
          `;
          draftItem.addEventListener('click', (e) => {
            // Only load draft if the click wasn't on the delete button
            if (!e.target.closest('.delete-draft-btn')) {
              loadDraft(draft);
            }
          });
          draftsList.appendChild(draftItem);
        });
      } else {
        draftsList.innerHTML = '<div class="no-drafts">No drafts available. Your saved drafts will appear here.</div>';
      }
    }
    
    function deleteDraft(event, index) {
      event.stopPropagation();
      
      if (confirm('Are you sure you want to delete this draft?')) {
        const username = localStorage.getItem('currentUser');
        const users = JSON.parse(localStorage.getItem('financeUsers'));
        
        if (users && users[username] && users[username].drafts) {
          users[username].drafts.splice(index, 1);
          localStorage.setItem('financeUsers', JSON.stringify(users));
          showDrafts();
          logActivity('DELETED_DRAFT', { index });
        }
      }
    }
    
    function loadDraft(draft) {
      document.getElementById('monthly-income').value = draft.income || '';
      document.getElementById('expenses').value = draft.expenses || '';
      
      if (draft.income && draft.expenses) {
        monthlyIncome = parseFloat(draft.income);
        const expenseData = parseExpenseData(draft.expenses);
        totalExpenses = Object.values(expenseData).reduce((a, b) => a + b, 0);
        const remaining = monthlyIncome - totalExpenses;
        updateResults(remaining, expenseData);
        renderChart(expenseData, remaining);
      }
      
      showAppPage();
      logActivity('LOADED_DRAFT', { timestamp: draft.timestamp });
    }
    
    function saveDraft() {
      const username = localStorage.getItem('currentUser');
      const users = JSON.parse(localStorage.getItem('financeUsers'));
      
      if (users && users[username]) {
        const income = document.getElementById("monthly-income").value;
        const expenses = document.getElementById("expenses").value;
        
        if (!income && !expenses) return;
        
        if (!users[username].drafts) {
          users[username].drafts = [];
        }
        
        users[username].drafts.push({
          income: income,
          expenses: expenses,
          timestamp: getCurrentTimestamp()
        });
        
        // Keep only the last 5 drafts
        if (users[username].drafts.length > 5) {
          users[username].drafts = users[username].drafts.slice(-5);
        }
        
        localStorage.setItem('financeUsers', JSON.stringify(users));
        logActivity('SAVED_DRAFT');
      }
    }
    
    // Auto-save draft every 2 minutes
    setInterval(saveDraft, 120000);
    
    // -------------------------------------------------------
    // UTILITY FUNCTIONS
    // -------------------------------------------------------
    function showError(elementId, message) {
      const element = document.getElementById(elementId);
      element.textContent = message;
      element.style.display = 'block';
      return false;
    }
    
    function hideError(elementId) {
      const element = document.getElementById(elementId);
      element.style.display = 'none';
      return true;
    }
    
    function validateEmail(email) {
      const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return re.test(email);
    }
    
    function getCurrentTimestamp() {
      return new Date().toISOString();
    }
    
    // Simple hash function for password obfuscation (not cryptographically secure)
    function simpleHash(str) {
      let hash = 0;
      for (let i = 0; i < str.length; i++) {
        const char = str.charCodeAt(i);
        hash = (hash << 5) - hash + char;
        hash = hash & hash; // Convert to 32bit integer
      }
      return hash.toString();
    }
    
    // -------------------------------------------------------
    // LOGGING SYSTEM
    // -------------------------------------------------------
    function logActivity(action, details = {}) {
      const username = localStorage.getItem('currentUser');
      if (!username) return;
      
      const timestamp = getCurrentTimestamp();
      const logEntry = {
        timestamp,
        username,
        action,
        details
      };
      
      // Get existing logs or create new array
      const logs = JSON.parse(localStorage.getItem('financeLogs')) || {};
      
      // Initialize user's log if it doesn't exist
      if (!logs[username]) {
        logs[username] = [];
      }
      
      // Add new log entry
      logs[username].push(logEntry);
      
      // Save back to localStorage
      localStorage.setItem('financeLogs', JSON.stringify(logs));
      
      // Also save to a downloadable log file
      saveToUserLogFile(logEntry);
    }
    
    function saveToUserLogFile(logEntry) {
      // This is a simulation - in a real app, this would save to an actual file
      const username = logEntry.username;
      const userLogs = JSON.parse(localStorage.getItem(`userLogs_${username}`)) || [];
      userLogs.push(logEntry);
      localStorage.setItem(`userLogs_${username}`, JSON.stringify(userLogs));
    }
    
    function downloadActivityLog() {
      const username = localStorage.getItem('currentUser');
      if (!username) return;
      
      const userLogs = JSON.parse(localStorage.getItem(`userLogs_${username}`)) || [];
      if (userLogs.length === 0) {
        alert('No activity logs found for your account.');
        return;
      }
      
      // Format logs as text
      let logText = `Activity Log for ${username}\n`;
      logText += '================================\n\n';
      
      userLogs.forEach((log, index) => {
        logText += `${index + 1}. ${log.timestamp} - ${log.action}\n`;
        if (Object.keys(log.details).length > 0) {
          logText += `   Details: ${JSON.stringify(log.details, null, 2)}\n`;
        }
        logText += '\n';
      });
      
      // Create download link
      const blob = new Blob([logText], { type: 'text/plain' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = `${username}_activity_log_${new Date().toISOString().split('T')[0]}.txt`;
      a.click();
      
      logActivity('DOWNLOADED_ACTIVITY_LOG', { logEntries: userLogs.length });
    }
    
    // -------------------------------------------------------
    // PAGE NAVIGATION FUNCTIONS
    // -------------------------------------------------------
    function showRegisterPage() {
      document.getElementById('loginPage').classList.add('hidden');
      document.getElementById('registerPage').classList.remove('hidden');
      document.getElementById('forgotPasswordPage').classList.add('hidden');
    }
    
    function showLoginPage() {
      document.getElementById('registerPage').classList.add('hidden');
      document.getElementById('loginPage').classList.remove('hidden');
      document.getElementById('forgotPasswordPage').classList.add('hidden');
      document.getElementById('userProfilePage').classList.add('hidden');
      document.getElementById('settingsPage').classList.add('hidden');
      document.getElementById('draftsPage').classList.add('hidden');
      document.getElementById('app').classList.add('hidden');
    }
    
    function showForgotPasswordPage() {
      document.getElementById('loginPage').classList.add('hidden');
      document.getElementById('registerPage').classList.add('hidden');
      document.getElementById('forgotPasswordPage').classList.remove('hidden');
      // Reset to step 1 when showing the page
      document.getElementById('resetStep1').classList.add('active');
      document.getElementById('resetStep2').classList.remove('active');
    }
    
    function showAppPage() {
      // Hide all pages
      document.getElementById('loginPage').classList.add('hidden');
      document.getElementById('registerPage').classList.add('hidden');
      document.getElementById('forgotPasswordPage').classList.add('hidden');
      document.getElementById('userProfilePage').classList.add('hidden');
      document.getElementById('settingsPage').classList.add('hidden');
      document.getElementById('draftsPage').classList.add('hidden');
      
      // Show main app page
      document.getElementById('app').classList.remove('hidden');
      
      // Update sidebar username
      const username = localStorage.getItem('currentUser');
      if (username) {
        document.getElementById('usernameDisplay').textContent = username;
      }
    }
    
    // -------------------------------------------------------
    // PASSWORD RESET FUNCTIONS
    // -------------------------------------------------------
    let resetEmail = ''; // Store the email being reset globally
    
    function verifyResetEmail() {
      const email = document.getElementById('resetEmail').value.trim();
      
      if (!email) {
        showError('resetEmailError', 'Email is required');
        return;
      }
      
      if (!validateEmail(email)) {
        showError('resetEmailError', 'Please enter a valid email');
        return;
      }
      
      // Check if email exists in users
      const users = JSON.parse(localStorage.getItem('financeUsers')) || {};
      const user = Object.values(users).find(u => u.email === email);
      
      if (!user) {
        showError('resetEmailError', 'No account found with this email');
        return;
      }
      
      // Store the email for the next step
      resetEmail = email;
      
      // Move to step 2
      document.getElementById('resetStep1').classList.remove('active');
      document.getElementById('resetStep2').classList.add('active');
      
      logActivity('PASSWORD_RESET_EMAIL_VERIFIED', { email });
    }
    
    function resetPassword() {
      const newPassword = document.getElementById('newPassword').value;
      const confirmPassword = document.getElementById('confirmNewPassword').value;
      
      // Reset error messages
      hideError('newPasswordError');
      hideError('confirmNewPasswordError');
      
      // Validate inputs
      let isValid = true;
      
      if (!newPassword) {
        showError('newPasswordError', 'Password is required');
        isValid = false;
      } else if (newPassword.length < 8) {
        showError('newPasswordError', 'Password must be at least 8 characters');
        isValid = false;
      }
      
      if (newPassword !== confirmPassword) {
        showError('confirmNewPasswordError', 'Passwords do not match');
        isValid = false;
      }
      
      if (!isValid) return;
      
      // Update password in users
      const users = JSON.parse(localStorage.getItem('financeUsers'));
      const username = Object.keys(users).find(u => users[u].email === resetEmail);
      
      if (username) {
        users[username].password = simpleHash(newPassword);
        localStorage.setItem('financeUsers', JSON.stringify(users));
        
        alert('Password reset successfully! Please login with your new password.');
        logActivity('PASSWORD_RESET_SUCCESS', { email: resetEmail });
        showLoginPage();
      } else {
        alert('Error resetting password. Please try again.');
        logActivity('PASSWORD_RESET_FAILED', { email: resetEmail, error: 'User not found' });
      }
    }
    
    // -------------------------------------------------------
    // USER MANAGEMENT SYSTEM
    // -------------------------------------------------------
    function register() {
      // Reset error messages
      hideError('regUsernameError');
      hideError('regEmailError');
      hideError('regPasswordError');
      hideError('regConfirmPasswordError');
      
      const username = document.getElementById('regUsername').value.trim();
      const email = document.getElementById('regEmail').value.trim();
      const password = document.getElementById('regPassword').value;
      const confirmPassword = document.getElementById('regConfirmPassword').value;
      
      // Validate inputs
      let isValid = true;
      
      if (!username) {
        showError('regUsernameError', 'Username is required');
        isValid = false;
      }
      
      if (!email) {
        showError('regEmailError', 'Email is required');
        isValid = false;
      } else if (!validateEmail(email)) {
        showError('regEmailError', 'Please enter a valid email');
        isValid = false;
      }
      
      if (!password) {
        showError('regPasswordError', 'Password is required');
        isValid = false;
      } else if (password.length < 8) {
        showError('regPasswordError', 'Password must be at least 8 characters');
        isValid = false;
      }
      
      if (password !== confirmPassword) {
        showError('regConfirmPasswordError', 'Passwords do not match');
        isValid = false;
      }
      
      if (!isValid) return;
      
      // Get existing users or create new list
      const users = JSON.parse(localStorage.getItem('financeUsers')) || {};
      
      if (users[username]) {
        showError('regUsernameError', 'Username already exists');
        return;
      }
      
      // Check if email is already registered
      const emailExists = Object.values(users).some(user => user.email === email);
      if (emailExists) {
        showError('regEmailError', 'Email already registered');
        return;
      }
      
      // Store new user with hashed password
      users[username] = { 
        email: email,
        password: simpleHash(password), // Note: In a real app, use proper password hashing
        data: {
          income: 0,
          expenses: "",
          expenseData: {}
        },
        settings: {
          theme: "system",
          emailNotifications: "enabled",
          budgetAlerts: "enabled",
          twoFactorAuth: "disabled",
          autoLogout: "30"
        },
        drafts: [],
        createdAt: getCurrentTimestamp()
      };
      
      localStorage.setItem('financeUsers', JSON.stringify(users));
      
      // Create a secure log file for the user
      localStorage.setItem(`userLogs_${username}`, JSON.stringify([]));
      
      alert("Registration successful! Please login.");
      logActivity('USER_REGISTERED', { username, email });
      showLoginPage();
    }
    
    function login() {
      // Reset error messages
      hideError('loginUsernameError');
      hideError('loginPasswordError');
      
      const username = document.getElementById('loginUsername').value.trim();
      const password = document.getElementById('loginPassword').value;
      
      // Validate inputs
      let isValid = true;
      
      if (!username) {
        showError('loginUsernameError', 'Username is required');
        isValid = false;
      }
      
      if (!password) {
        showError('loginPasswordError', 'Password is required');
        isValid = false;
      }
      
      if (!isValid) return;
      
      const users = JSON.parse(localStorage.getItem('financeUsers')) || {};
      const user = users[username];
      
      // Check if user exists and password matches (using simple hash)
      if (user && user.password === simpleHash(password)) {
        // Login successful
        localStorage.setItem('currentUser', username);
        
        // Show app and hide auth pages
        showAppPage();
        
        // Load user data
        if (user.data) {
          if (user.data.income) {
            document.getElementById("monthly-income").value = user.data.income;
            monthlyIncome = parseFloat(user.data.income);
          }
          if (user.data.expenses) {
            document.getElementById("expenses").value = user.data.expenses;
          }
          if (user.data.expenseData && Object.keys(user.data.expenseData).length > 0) {
            // If there's expense data, render the chart and results
            totalExpenses = Object.values(user.data.expenseData).reduce((a, b) => a + b, 0);
            const remaining = monthlyIncome - totalExpenses;
            updateResults(remaining, user.data.expenseData);
            renderChart(user.data.expenseData, remaining);
          }
        }
        
        // Apply saved theme
        if (user.settings && user.settings.theme) {
          applyTheme(user.settings.theme);
        }
        
        // Log successful login
        logActivity('USER_LOGGED_IN', { username });
      } else {
        showError('loginPasswordError', 'Invalid username or password');
        logActivity('LOGIN_FAILED', { username, reason: 'Invalid credentials' });
      }
    }
    
    function deleteAccount() {
      const username = localStorage.getItem('currentUser');
      if (!username) return;
      
      // Get users from localStorage
      const users = JSON.parse(localStorage.getItem('financeUsers'));
      
      if (users && users[username]) {
        // Delete user data
        delete users[username];
        localStorage.setItem('financeUsers', JSON.stringify(users));
        
        // Delete activity logs
        localStorage.removeItem(`userLogs_${username}`);
        
        // Remove from financeLogs
        const financeLogs = JSON.parse(localStorage.getItem('financeLogs')) || {};
        delete financeLogs[username];
        localStorage.setItem('financeLogs', JSON.stringify(financeLogs));
        
        // Logout user
        logout();
        
        alert('Your account has been permanently deleted.');
        logActivity('ACCOUNT_DELETED', { username });
      }
      
      closeModal();
    }
    
    function saveData() {
      const username = localStorage.getItem('currentUser');
      if (!username) return;
      
      const users = JSON.parse(localStorage.getItem('financeUsers'));
      const income = document.getElementById("monthly-income").value;
      const expenses = document.getElementById("expenses").value;
      
      // Update user data
      users[username].data = {
        income: income,
        expenses: expenses,
        expenseData: parseExpenseData(expenses)
      };
      
      localStorage.setItem('financeUsers', JSON.stringify(users));
      
      // Log the data update
      logActivity('DATA_UPDATED', {
        income: income,
        expenses: expenses
      });
    }
    
    function parseExpenseData(expensesInput) {
      const expensesArray = expensesInput.split(",");
      let expenseData = {};
      
      expensesArray.forEach(expense => {
        const [item, cost] = expense.split(":").map(e => e.trim());
        if (item && cost && !isNaN(cost)) {
          expenseData[item] = parseFloat(cost);
        }
      });
      
      return expenseData;
    }
    
    function logout(e) {
      if (e) e.stopPropagation();
      
      const username = localStorage.getItem('currentUser');
      if (username) {
        logActivity('USER_LOGGED_OUT', { username });
      }
      localStorage.removeItem('currentUser');
      location.reload();
    }
    
    // File export/import functions
    function exportData() {
      const username = localStorage.getItem('currentUser');
      const users = JSON.parse(localStorage.getItem('financeUsers'));
      const userData = users[username];
      
      // Remove sensitive information before export
      const exportData = {
        ...userData,
        password: undefined, // Don't export password
        email: undefined     // Don't export email
      };
      
      const exportText = JSON.stringify(exportData, null, 2);
      document.getElementById('fileExport').value = exportText;
      
      // Create download link
      const blob = new Blob([exportText], { type: 'text/plain' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = `${username}_finance_data_${new Date().toISOString().split('T')[0]}.txt`;
      a.click();
      
      logActivity('DATA_EXPORTED', { filename: a.download });
    }
    
    function importData() {
      const fileInput = document.getElementById('fileImport');
      fileInput.onchange = e => {
        const file = e.target.files[0];
        if (!file) return;
        
        const reader = new FileReader();
        
        reader.onload = event => {
          try {
            const data = JSON.parse(event.target.result);
            const username = localStorage.getItem('currentUser');
            const users = JSON.parse(localStorage.getItem('financeUsers'));
            
            // Only import the data portion, not credentials
            if (data.data) {
              users[username].data = data.data;
              localStorage.setItem('financeUsers', JSON.stringify(users));
              
              // Update UI
              if (data.data.income) {
                document.getElementById("monthly-income").value = data.data.income;
                monthlyIncome = parseFloat(data.data.income);
              }
              if (data.data.expenses) {
                document.getElementById("expenses").value = data.data.expenses;
              }
              if (data.data.expenseData) {
                totalExpenses = Object.values(data.data.expenseData).reduce((a, b) => a + b, 0);
                const remaining = monthlyIncome - totalExpenses;
                updateResults(remaining, data.data.expenseData);
                renderChart(data.data.expenseData, remaining);
              }
              
              alert('Data imported successfully!');
              logActivity('DATA_IMPORTED', { filename: file.name });
            } else {
              alert('No valid data found in the file');
            }
          } catch (err) {
            alert('Error importing file: ' + err.message);
            logActivity('DATA_IMPORT_FAILED', { error: err.message });
          }
        };
        
        reader.readAsText(file);
      };
      
      fileInput.value = ''; // Reset so same file can be imported again
      fileInput.click();
    }
    
    // Check if user is already logged in
    window.onload = function() {
      const currentUser = localStorage.getItem('currentUser');
      if (currentUser) {
          showAppPage();
          
          // Load user data
          const users = JSON.parse(localStorage.getItem('financeUsers'));
          const user = users[currentUser];

          // Apply saved theme (Dark Mode Addition)
          if (user.settings && user.settings.theme) {
              applyTheme(user.settings.theme);
              document.getElementById('themeSelect').value = user.settings.theme;
          }

          // Load financial data (Existing Functionality)
          if (user.data) {
              if (user.data.income) {
                  document.getElementById("monthly-income").value = user.data.income;
                  monthlyIncome = parseFloat(user.data.income);
              }
              if (user.data.expenses) {
                  document.getElementById("expenses").value = user.data.expenses;
              }
              if (user.data.expenseData && Object.keys(user.data.expenseData).length > 0) {
                  totalExpenses = Object.values(user.data.expenseData).reduce((a, b) => a + b, 0);
                  const remaining = monthlyIncome - totalExpenses;
                  updateResults(remaining, user.data.expenseData);
                  renderChart(user.data.expenseData, remaining);
              }
          }
          
          logActivity('PAGE_LOADED', { autoLogin: true });
      } else {
          showLoginPage();
          logActivity('PAGE_LOADED', { autoLogin: false });
      }

      // Initialize theme listener (Dark Mode Addition)
      setupThemeListener();
    };
    
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
        saveData();
        logActivity('INCOME_SET', { amount: monthlyIncome });
      } else {
        alert("Please enter a valid income.");
        logActivity('INCOME_SET_FAILED', { reason: 'Invalid input' });
      }
    }
    
    function trackExpenses() {
      const expensesInput = document.getElementById("expenses").value;
      const expenseData = parseExpenseData(expensesInput);
      totalExpenses = Object.values(expenseData).reduce((a, b) => a + b, 0);
      const remaining = monthlyIncome - totalExpenses;
      
      updateResults(remaining, expenseData);
      renderChart(expenseData, remaining);
      saveData();
      
      logActivity('EXPENSES_TRACKED', {
        expenseCount: Object.keys(expenseData).length,
        totalExpenses: totalExpenses,
        remaining: remaining
      });
    }
    
    function updateResults(remaining, expenseData) {
      let breakdown = '<p><strong>Expense Breakdown:</strong></p><ul>';
      
      for (const [item, cost] of Object.entries(expenseData)) {
        breakdown += `<li>${item}: ₹${cost}</li>`;
      }
      
      breakdown += "</ul>";
      
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
              "#9C27B0",
              "#00bcd4",
              "#e91e63",
              "#8bc34a"
            ],
            borderWidth: 0,
            hoverOffset: 15
          }]
        },
        options: {
          responsive: true,
          plugins: {
            legend: { 
              position: "top",
              labels: {
                font: {
                  size: 12,
                  weight: 'bold'
                },
                padding: 20
              }
            },
            tooltip: {
              callbacks: {
                label: function (tooltipItem) {
                  return tooltipItem.label + ": ₹" + tooltipItem.raw;
                }
              },
              bodyFont: {
                size: 14,
                weight: 'bold'
              },
              padding: 12,
              displayColors: true,
              usePointStyle: true
            }
          },
          animation: {
            animateScale: true,
            animateRotate: true
          }
        }
      });
      
      logActivity('CHART_RENDERED', {
        expenseCategories: Object.keys(expenseData).length,
        hasRemaining: remaining > 0
      });
    }
  </script>
</body>
</html>
