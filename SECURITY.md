# 🔒 SECURITY.md — Security Policy for College ERP

This document outlines the **security practices**, **policies**, and **guidelines** for ensuring the safety of data and users within the **College ERP – Integrated Student Management System**.  
The system handles sensitive student, academic, and financial information, so maintaining strict security standards is essential.

---

# 📌 Supported Versions

Only the **latest main branch** and the most recent **released build** are actively supported for security updates.

| Version | Supported |
|---------|-----------|
| Latest release | ✅ Yes |
| Development branch | ⚠️ Partially |
| Older versions | ❌ No |

---

# 🔑 1. Authentication & Authorization

### **Supabase Auth (JWT-based)**
- All users authenticate through Supabase Auth.  
- Sessions are secured using **JWT tokens**.  
- Tokens must never be stored in plain localStorage without expiration logic.

### **Role-Based Access Control (RBAC)**
The ERP includes multiple roles:
- **Student**
- **Clerk**
- **Faculty**
- **Hostel Officer**
- **Admin**

Each role only has access to modules relevant to its responsibilities.

### **Row Level Security (RLS)**
Supabase RLS ensures:
- Users only access data that belongs to their role and permissions.  
- Students cannot see other students' data.  
- Clerks cannot modify admin-only data.  
- Faculty can only upload marks for assigned exams.

All tables have strict RLS policies in place.

---

# 🔐 2. Data Protection

### **Supabase (Postgres)**
- All sensitive data (student personal details, transactions) stays in the encrypted Postgres database.  
- RLS prevents unauthorized access.  
- Token-based security ensures only authenticated users can query.

### **Client-Side Storage**
- No sensitive data (Aadhaar, marks, receipts) is stored in browser localStorage.  
- Only minimal items like theme settings or UI preferences may be stored.

---

# 💳 3. Payment Security

### **Razorpay Demo Integration**
Even though the project uses demo integration:
- API keys must remain in `.env` files.  
- Keys must never be committed to GitHub.  
- Payment response data is validated before updating records in Supabase.

Never log payment responses in production mode.

---

# 🛡️ 4. Secure Coding Guidelines

### **Do Not Expose Secrets**
- Environment variables must be stored only in `.env` (client + server).  
- Never commit Supabase keys, B2 bucket keys, or Razorpay keys.

### **Input Validation**
- All form inputs must be validated in React + TypeScript.  
- Prevent invalid or malicious user input from reaching Supabase.

### **Avoid SQL Injection**
Supabase prevents SQL injection, but:
- Always use Supabase client libraries.  
- Never use raw SQL strings with user input.

### **Avoid XSS**
- Use React’s default escaping of HTML.  
- Do not insert raw HTML via `dangerouslySetInnerHTML`.

### **File Upload Safety**
- Only allow PDF/JPG/PNG file types.  
- Enforce file size limits.  
- Validate MIME type before upload.

---

# 📝 5. Reporting a Security Vulnerability

If you discover a security issue, please report it responsibly.

### 📧 Email:
**hemantfsu@gmail.com**

### 🕒 Response Time:
- Critical vulnerabilities: **24–48 hours**  
- High severity: **3–5 days**  
- Medium/Low: **1–2 weeks**

### Your report should include:
- Description of the vulnerability  
- Steps to reproduce  
- Potential impact  
- Suggested fix (optional)

---

# 🛑 6. Prohibited Actions

Contributors must **never**:

- Commit `.env` files or secrets  
- Disable Supabase RLS  
- Create public Backblaze B2 buckets  
- Log sensitive personal or financial data  
- Store Aadhaar numbers unmasked  
- Expose API keys in frontend code  
- Modify authorization rules without review  

Any PR violating these rules will be rejected.

---

# 🧯 7. Incident Response Policy

In case of a security breach:

1. Immediately revoke exposed Supabase, B2, or Razorpay keys  
2. Disable affected modules temporarily  
3. Investigate database and auth logs  
4. Notify stakeholders and admins  
5. Patch and deploy a fix  
6. Document the incident for future prevention  

---

# ✅ 8. Best Practices for Contributors

- Test changes under limited permissions to avoid bypassing RLS  
- Keep dependencies updated  
- Avoid unnecessary third-party libraries  
- Follow commit message guidelines  
- Review PRs carefully for hidden security issues  

---

# 🙏 Final Notes

Security is a shared responsibility.  
Your diligence helps protect sensitive educational and financial data in this ERP system.

Thank you for contributing securely to **College ERP** ❤️

