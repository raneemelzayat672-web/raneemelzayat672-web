
// Example token verification & RBAC middleware snippet
const jwt = require('jsonwebtoken');

function verifyRole(requiredRole) {
  return (req, res, next) => {
    const token = req.headers.authorization?.split(' ')[1];
    if (!token) return res.status(401).json({ error: 'Access token missing' });

    try {
      const decoded = jwt.verify(token, process.en# AI-Powered Threat Intelligence & Automated Incident Response Platform

## 🛡️ Raneem's Cybersecurity & Backend Contributions

A secure backend and threat-response architecture built with Node.js, Express, and MongoDB.

---

### 1. Project Organization & Git Workflow
* **Overview:** Unified file structures across the repository, cleaned up redundant code, and established a clean branching strategy.
* **Implementation & Workflow:**
```bash
# Initialize and manage repository structure
git status
git add .
git commit -m "Refactor repository structure and cleanup redundant files"
git push origin main
```

---

### 2. Authentication & Role-Based Access Control (RBAC)
* **Overview:** Developed secure user registration, login/logout mechanisms with JWT, password hashing, and strict role segregation.
* **Roles Implemented:** `Admin`, `Analyst`, `Viewer`.
* **Sample Authentication Route Integration:**
```javascriptv.JWT_SECRET);
      if (decoded.role !== requiredRole && decoded.role !== 'admin') {
        return res.status(403).json({ error: 'Unauthorized access' });
      }
      req.user = decoded;
      next();
    } catch (err) {
      return res.status(403).json({ error: 'Invalid or expired token' });
    }
  };
}
```

---

### 3. API Security & Hardening
* **Overview:** Secured sensitive endpoints, implemented input validation, centralized JSON error handling with request IDs, and CORS configuration.
* **Sample Error Handling Middleware:**
```javascript
// Centralized Error Handling with Request IDs
app.use((err, req, res, next) => {
  const requestId = req.headers['x-request-id'] || Date.now().toString();
  console.error(`[Error ID: ${requestId}] ${err.message}`);
  
  res.status(err.status || 500).json({
    error: {
      message: err.message || 'Internal Server Error',
      requestId: requestId
    }
  });
});
```

---

### 4. Concurrency & Duplicate Prevention
* **Overview:** Engineered database constraints, unique indexes, and logic to prevent duplicate open alerts and race conditions during simultaneous incoming requests.
* **Sample Unique Index Constraint (MongoDB):**
```javascript
// Ensuring no duplicate open alerts for the same threat signature
alertSchema.index({ threatId: 1, status: 1 }, { 
  unique: true, 
  partialFilterExpression: { status: 'open' } 
});
```

---

### 🛠️ Tech Stack & Security Tools:
* **Backend:** Node.js, Express.js
* **Database & Indexing:** MongoDB, Mongoose Unique Constraints
* **Security & Core Domains:** RBAC, JWT Authentication, API Hardening, Concurrency Control
* **Tools:** Git, GitHub, VS Code, Linux
