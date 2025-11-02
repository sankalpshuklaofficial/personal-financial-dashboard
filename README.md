# Personal Financial Dashboard

## 1. Introduction

In today’s fast-paced digital era, managing personal finances has become increasingly complex. People often struggle to keep track of their expenses, savings, investments, and income sources across multiple platforms such as bank apps, UPI transactions, and digital wallets. To address this problem, the **Personal Financial Dashboard** was developed — a full-stack web application that provides users with a centralized platform to track, analyze, and manage their financial activities efficiently.

This project leverages **Next.js**, **Node.js**, **Express**, and **Supabase** to deliver a secure, scalable, and user-friendly solution. It also integrates **JWT authentication** for data privacy and can optionally use a **Python microservice** for machine-learning-based transaction categorization and expense prediction.

The system not only helps users monitor their financial health but also encourages disciplined spending, better budgeting, and informed decision-making through visual insights and reports.

---

## 2. Problem Statement

Despite the availability of several finance management tools, most people still depend on manual tracking using spreadsheets or fragmented mobile apps. These methods are:

* **Time-consuming** and prone to errors
* **Unintegrated**, requiring users to switch between multiple apps
* **Lacking analytics**, making it hard to visualize spending habits
* **Difficult to personalize**, since most tools don’t adapt to individual behavior

Hence, there’s a need for an **integrated web platform** that can:

1. Aggregate income and expenses from different sources,
2. Categorize transactions intelligently,
3. Visualize financial data for better understanding, and
4. Ensure privacy and security of user data.

The **Personal Financial Dashboard** fulfills these needs through a clean interface, robust backend, and insightful visualizations.

---

## 3. Project Objectives

The main objectives of this project are:

* To design and build a **modern, full-stack web dashboard** that enables users to manage their personal finances efficiently.
* To implement **secure user authentication** and data management using JWT and Supabase.
* To develop **data visualization modules** for tracking income, expenses, and category-wise spending.
* To integrate a **machine learning model** (optional Python microservice) that predicts upcoming expenses and automatically categorizes transactions.
* To ensure scalability and maintainability through modular design and reusable components.

---

## 4. Technology Stack

| Layer                           | Technology Used                 | Description                                                                                |
| ------------------------------- | ------------------------------- | ------------------------------------------------------------------------------------------ |
| **Frontend**                    | **Next.js (React framework)**   | Provides a responsive, server-rendered UI with optimized performance.                      |
| **Styling**                     | **Material UI / Chakra UI**     | Used for designing elegant, accessible, and consistent UI components.                      |
| **Backend**                     | **Node.js + Express.js**        | Handles API routes, authentication, and server logic.                                      |
| **Database**                    | **Supabase (PostgreSQL)**       | A hosted backend-as-a-service platform that simplifies CRUD operations and authentication. |
| **Authentication**              | **JWT + bcrypt**                | Ensures secure login and authorization.                                                    |
| **Charts**                      | **Recharts / Chart.js**         | For data visualization of spending patterns.                                               |
| **Machine Learning (optional)** | **Python + Flask microservice** | For intelligent categorization and expense prediction.                                     |
| **Version Control**             | **Git + GitHub**                | Used for version tracking and collaboration.                                               |

---

## 5. System Architecture

The **Personal Financial Dashboard** follows a **client-server architecture** with the following components:

1. **Frontend (Next.js):**

   * Interacts with backend APIs to fetch and display data.
   * Handles routing, state management, and visualization.
   * Implements user authentication and form validation.

2. **Backend (Node.js + Express):**

   * Exposes RESTful APIs for CRUD operations on transactions, budgets, and user profiles.
   * Handles JWT-based authentication and authorization.
   * Communicates securely with the Supabase database.

3. **Database (Supabase/PostgreSQL):**

   * Stores users, transactions, categories, and budget data.
   * Ensures relational integrity and data security.

4. **Optional ML Microservice (Python):**

   * Predicts future expenses using regression models.
   * Categorizes transactions automatically using text embeddings or trained models.

5. **Integration Layer:**

   * Manages API communication between the frontend and backend.
   * Uses Axios or Fetch API for seamless data exchange.

---

## 6. Key Features

### 🧾 1. User Authentication

* JWT-based login and signup.
* Passwords encrypted using bcrypt.
* Secure session handling with refresh tokens.

### 💸 2. Expense & Income Management

* Add, edit, or delete transactions manually.
* Automatically categorize transactions (optional ML model).
* Separate views for income, expenses, and savings.

### 📊 3. Data Visualization

* Dynamic charts showing monthly trends.
* Category-wise breakdown of spending.
* Real-time dashboards summarizing total income and expenses.

### 🎯 4. Budget Planning

* Set monthly or category-based budgets.
* Track budget utilization and alerts when limits are exceeded.

### 🧠 5. Predictive Analytics (Optional)

* Machine learning models trained on user data predict next-month expenses.
* Insights help users anticipate future financial needs.

### ⚙️ 6. Responsive UI/UX

* Built with Material UI/Chakra for smooth interaction.
* Fully responsive layout for mobile and desktop users.

### 🔐 7. Security

* HTTPS communication (recommended in deployment).
* JWT token verification middleware.
* Environment variables hidden using `.env`.

---

## 7. Implementation Details

### 7.1 Frontend

Developed in **Next.js**, the frontend offers a multi-page experience optimized with server-side rendering for faster load times. The pages include:

* **Dashboard Page:** Displays summary metrics (total income, expense, savings).
* **Transactions Page:** Allows CRUD operations on user entries.
* **Analytics Page:** Shows charts and reports for trends and spending behavior.
* **Profile Page:** User info and settings.

Reusable components such as cards, modals, forms, and charts improve maintainability.

### 7.2 Backend

The backend API is powered by **Node.js and Express**. Routes are structured modularly:

```
/auth        -> handles signup/login
/transactions -> CRUD for transactions
/budget      -> handles budget setup
/analytics   -> provides aggregated data
```

Each route connects with the Supabase database through REST calls or the Supabase JS SDK.

### 7.3 Database Schema (Supabase/PostgreSQL)

**Tables:**

1. **Users:** `id`, `name`, `email`, `password`
2. **Transactions:** `id`, `user_id`, `amount`, `type (income/expense)`, `category`, `date`
3. **Budgets:** `id`, `user_id`, `category`, `limit_amount`, `spent`
4. **Predictions (optional):** `user_id`, `predicted_expense`, `month`, `confidence_score`

### 7.4 Authentication Workflow

1. User signs up → password hashed using `bcrypt`.
2. Upon login, JWT token generated with a secret key.
3. Token stored in client (usually localStorage or cookies).
4. Backend middleware verifies token for each request.

### 7.5 Machine Learning Integration (Optional)

A lightweight Python Flask service processes transaction data and predicts future spending using regression or LSTM models. The backend calls this API asynchronously and stores results in Supabase.

---

## 8. Challenges Faced & Solutions

### Challenge 1: Data Consistency

* **Problem:** Keeping frontend, backend, and Supabase in sync.
* **Solution:** Implemented async/await in all API calls and used React Query for caching.

### Challenge 2: Authentication Errors

* **Problem:** Handling token expiry and invalid sessions.
* **Solution:** Added middleware for token verification and refresh mechanism.

### Challenge 3: Chart Rendering Performance

* **Problem:** Slow rendering with large datasets.
* **Solution:** Implemented lazy loading and optimized chart re-renders.

### Challenge 4: Deployment Environment

* **Problem:** Environment variable leakage during deployment.
* **Solution:** Used `.env.local` and `.env.production` files with `.gitignore` to secure keys.

---

## 9. Future Enhancements

* 🔗 **Bank API Integration:** Automatically fetch transactions from user bank accounts.
* 🤖 **AI Expense Advisor:** Suggest savings plans and investment recommendations.
* 📱 **Mobile App:** Build a React Native version for mobile users.
* 🧾 **Receipt Scanner:** Extract transaction data using OCR and NLP.
* ☁️ **Cloud Deployment:** Deploy fully on Vercel (frontend) + Render or Supabase (backend).
* 📧 **Email Reports:** Send monthly spending summaries.

---

## 10. Testing and Quality Assurance

* **Unit Testing:** Jest for frontend and Mocha/Chai for backend APIs.
* **Integration Testing:** Validated data flow between components.
* **Manual UI Testing:** Checked responsiveness across screen sizes.
* **Error Logging:** Implemented middleware for error handling and logging.

---

## 11. Deployment

### Recommended Setup

* **Frontend:** Deploy on **Vercel** (built for Next.js).
* **Backend:** Deploy on **Render / Railway.app**.
* **Database:** Hosted by **Supabase Cloud**.
* **ML Service:** Hosted on **Streamlit Cloud / Flask API on Render**.

### Environment Variables

```
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
JWT_SECRET=
SUPABASE_SERVICE_KEY=
```

---

## 12. Conclusion

The **Personal Financial Dashboard** project is a comprehensive, modern solution for personal finance management. It integrates a robust backend, secure authentication, intuitive frontend, and optional machine learning features to give users a seamless experience.

This project not only showcases full-stack development skills but also highlights the use of **real-world technologies** such as Supabase, JWT, and React-based visualization. It demonstrates how software can empower individuals to take control of their financial lives through automation and insight.

The modular architecture ensures easy scalability, allowing integration of future features like AI-based advisors, mobile apps, and external financial APIs.

Ultimately, this project reflects the vision of simplifying financial management using technology — making it smart, secure, and accessible to everyone.
