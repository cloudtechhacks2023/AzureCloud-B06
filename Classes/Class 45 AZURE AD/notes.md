

## 🔐 **Azure Active Directory (Azure AD) – Notes**

### 🔸 What is Azure AD?
- Azure Active Directory is **Microsoft’s cloud-based identity and access management (IAM) service**.
- It helps employees sign in and access resources like:
  - Microsoft 365
  - Azure Portal
  - Third-party SaaS apps (e.g., Salesforce)
  - Internal apps (on-prem or cloud)

---

### 🔸 Key Components

**1. Tenants**
- A **dedicated Azure AD instance** for an organization.
- Each tenant is **unique and isolated**.

**2. Directory**
- Stores user identities, groups, devices, applications, and roles.

**3. Identity Types**
- **Cloud-only**: Users created in Azure AD (no on-prem AD).
- **Synced (Hybrid)**: On-prem AD users synced using Azure AD Connect.
- **Guest**: External users (B2B).

**4. Objects**
- **User**: Represents a person.
- **Group**: Collection of users (security or M365).
- **Device**: Registered or joined devices.
- **Application**: Enterprise or registered apps.

---

### 🔸 Authentication Methods
- Password
- **Multi-Factor Authentication (MFA)**
- Certificate-based auth
- Windows Hello for Business
- FIDO2 security keys

---

### 🔸 Azure AD Editions
1. **Free**: Basic identity services.
2. **P1 (Premium 1)**:
   - Conditional Access
   - Self-service password reset
   - Hybrid identity
3. **P2 (Premium 2)**:
   - All P1 features +
   - Identity Protection
   - Privileged Identity Management (PIM)

---

### 🔸 Azure AD Features

**1. Conditional Access**
- Automates access control decisions based on conditions like user location, device state, etc.

**2. MFA (Multi-Factor Authentication)**
- Adds an extra layer of security beyond username and password.

**3. SSO (Single Sign-On)**
- Sign in once to access multiple applications.

**4. Azure AD Connect**
- Tool to sync on-prem Active Directory with Azure AD.

**5. Self-Service Password Reset (SSPR)**
- Users can reset their password securely without IT support.

**6. Identity Protection**
- Detects risky sign-ins and users, applies remediation.

**7. Privileged Identity Management (PIM)**
- Just-in-time role assignments, approval workflows, auditing.

**8. Role-Based Access Control (RBAC)**
- Assign permissions to users based on roles.

**9. Enterprise Applications**
- Enable SSO, provisioning, and monitoring for 3rd-party and custom apps.

**10. B2B (Business-to-Business)**
- Share your apps/services with guest users from other organizations.

**11. B2C (Business-to-Consumer)**
- Manage identity for customers using apps (custom branding, social login).

---

### 🔸 Important Azure AD Roles
- **Global Administrator** – Full access to everything.
- **User Administrator** – Manage users and groups.
- **Application Administrator** – Manage enterprise applications.
- **Security Administrator** – Manage security-related features.
- **Privileged Role Administrator** – Manage role assignments.

---

### 🔸 Monitoring & Logs
- Azure AD Sign-In logs
- Audit logs
- Integration with **Microsoft Sentinel** or **Log Analytics**

