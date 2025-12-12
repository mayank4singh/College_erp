# 📘 LEARN.md — Understanding and Working With the College ERP Project

Welcome to **College ERP – Integrated Student Management System**!  
This guide is designed to help new contributors quickly understand the project architecture, tools, workflow, and development environment.

Whether you’re a beginner or an experienced developer, this file will give you everything you need to **learn, explore, and contribute confidently**.

---

# 🎯 What You Will Learn

- How the College ERP system works  
- Project structure overview  
- Understanding the technology stack  
- How data flows between frontend → backend → storage → payment  
- How roles and permissions work  
- How to run and develop the project locally  
- How to extend or modify modules  
- Key concepts you must understand before contributing  

---

# 🧠 1. High-Level Architecture

The project uses a **modern full-stack architecture**:

- **React 18 + TypeScript + Vite** → Frontend  
- **Tailwind CSS** → Styling  
- **Supabase Postgres** → Database  
- **Supabase Auth** → Authentication (JWT-based)  
- **RLS (Row Level Security)** → Role-based access   
- **Razorpay (Demo)** → Fee payment integration  
- **Recharts** → Charts & analytics  
- **jsPDF** → PDF receipts & reports  
- **Context API** → State management  

All data flows from the UI to Supabase via secure API routes, and documents are uploaded to Backblaze B2.


---

# 🛠️ 2. Understanding Each Technology

### **React + TypeScript**
Used to build modular, reusable UI components with type safety.

### **Vite**
Super-fast bundler and dev server.

### **Tailwind CSS**
Utility-first CSS for rapid styling.

### **Supabase (Postgres + Auth + APIs)**
- Stores all student, admission, fee, exam, and hostel data  
- Handles login, JWT sessions, and role-based permissions  
- Enforces **RLS (Row Level Security)** to ensure users see only their data  

### **Razorpay Demo Integration**
Allows digital fee payment and auto-updates transaction records.

### **Recharts**
Used for dashboards:
- Admissions trends  
- Fee collection charts  
- Hostel occupancy  
- Exam result analytics  

### **jsPDF**
Exports:
- Receipts  
- Reports  
- Student profiles  
- Summaries  

---

# 🔁 3. How Data Flows in the System

Below is a simplified version of the internal workflow:

1. **Student/Clerk/Admin performs an action** (submit form, allocate room, pay fees).  
2. **Frontend validates the data** using React + TypeScript.  
3. Data is sent to **Supabase Postgres**, which serves as the main database.  
4. Uploaded documents are stored in **Backblaze B2**, and their URLs are saved in Supabase.  
5. For payments:
   - Razorpay handles the payment demo  
   - Returns transaction response  
   - Supabase updates status  
   - jsPDF generates the digital receipt  
6. Dashboards pull real-time data using **Recharts**.  

---

# 👤 4. Role-Based Learning Guide

The system includes multiple roles:

| Role | Access |
|------|--------|
| Student | Own records, fee payment, hostel status, results |
| Clerk | Admissions, fee management, hostel applications |
| Faculty | Exams, marks upload |
| Hostel Officer | Room allocation, hostel records |
| Admin | Full system access |
| Principal | Dashboards, reports |

Each role interacts differently with the database and UI.

---

# ▶️ 5. Running the Project Locally

### 1. Clone Repository
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```
### 2. Install Dependencies
```bash
npm install
```
### 3. Setup Environment Variables
Create .env file containing:
```bash
VITE_SUPABASE_URL=your_url
VITE_SUPABASE_ANON_KEY=your_key
VITE_B2_BUCKET_URL=your_bucket_url
VITE_RAZORPAY_KEY=test_key_here
```
### 4. Start Development Server
```bash
npm run dev
```
# 🧩 6. How to Add or Modify Features
### Adding a Page
- Create a folder in src/pages/
- Add route in React Router
- Use Tailwind for UI
- Use Supabase methods for CRUD operations

### Extending Database
- Add table/columns in Supabase
- Update TypeScript interfaces in /types
- Update forms + validation

### Adding Dashboard Cards
- Fetch data from Supabase
- Use Recharts for graph visualizations

# 🧪 7. Things You Should Understand Before Contributing
- Basics of React Hooks
- TypeScript interfaces
- Supabase CRUD operations
- How RLS rules affect role-based access
- Tailwind component styling
- How payment callbacks work
- How PDF generation works with jsPDF

# 📚 8. Recommended Resources to Learn Faster
### React:
- https://react.dev/learn
### TypeScript:
- https://www.typescriptlang.org/docs/
### Supabase:
- https://supabase.com/docs
### Tailwind:
- https://tailwindcss.com/docs
### Recharts:
- https://recharts.org/en-US
### jsPDF:
- https://github.com/parallax/jsPDF

# ⭐ Conclusion

You now understand everything necessary to learn, extend, and contribute to the College ERP project.
This system is modular, scalable, and community-driven — your contributions help shape its future.

If you have questions or need help, feel free to open a Discussion or Issue in the repository.

Happy Coding! 🚀
