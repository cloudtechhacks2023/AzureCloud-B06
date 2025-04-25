

### 🔵 **AD DS (Active Directory Domain Services) – On-Premises**

- **AD DS** ek directory service hai jo Microsoft Windows Server pe chalti hai.
- Ye users, computers, printers, groups wagaira ka data store karti hai.
- AD DS ke zariye hi user **authentication & authorization** hoti hai.

---

### 🖥️ **Domain Controller (DC) Server – Explained**

- **Domain Controller (DC)** ek Windows Server hota hai jisme **AD DS role installed** hota hai.
- DC ka kaam hota hai:  
  - User login request accept karna  
  - Authentication karna (Kerberos/LDAP)  
  - Group Policy apply karna  
  - Directory database (NTDS.dit) ko manage karna

#### 🧠 Important Concepts:
- Aapke network mein ek ya ek se zyada **DCs** ho sakte hain.
- Ek DC failure hone par dusra DC kaam continue karta hai (**High Availability**).
- DC har waqt AD database ko replicate karta hai agar multiple DCs hon.
- DC ko domain ke andar hi rakhte hain aur ye **always-on** server hota hai.

#### ⚙️ How to Promote a Server as DC:
1. **Windows Server install karein.**
2. Server Manager → Add roles and features → Select **Active Directory Domain Services**.
3. Installation ke baad server ko **Promote to Domain Controller** karein.
4. Naya domain create karein ya existing mein add karein.

---

### 🟢 **Migration of On-Prem Users to Azure Entra ID**

> [Same steps as before – Using Azure AD Connect]

#### 🔁 Updated Steps:
1️⃣ **Install & Promote Domain Controller**  
2️⃣ **Install Azure AD Connect on DC or member server**  
3️⃣ **Sync On-Prem AD Users to Azure Entra ID**

---

### 🔍 Verification:
- DC par `dsa.msc` se AD users check kar sakte hain.
- Azure Portal → Entra ID → Users → Source should show as “Windows Server AD”.

-