# Wireshark HTTP Traffic Analysis Project

## 📌 Project Overview

This project demonstrates how **unencrypted HTTP traffic** can expose sensitive information, such as login credentials, using **Wireshark**. The goal is to capture HTTP traffic, filter authentication packets, and highlight the importance of HTTPS encryption.

## 🛠 Tools Used

- **Wireshark** – Packet sniffing and network analysis
- **Test Web Application** – vbsca.ca
- **Operating System** – Windows

## 🔍 Steps to Execute

### 1️⃣ Setup & Capture Traffic

1. Install **Wireshark** and select the active network interface.
2. Start capturing network traffic while navigating to a test login page.
3. Enter dummy credentials on an **HTTP-based login form**.

### 2️⃣ Apply Wireshark Filters

1. Use the following filter to capture HTTP POST requests:
   ```plaintext
   http.request.method == "POST"
   ```
2. Look for packets containing **username** and **password** fields in plaintext.

### 3️⃣ Analyze Findings

- **Captured Data Analysis:**

  - Identified **plaintext login credentials** within an HTTP POST request.
  - Captured packets revealed **username: [exposed\_username]** and **password: [exposed\_password]** in readable text.
  - Observed that HTTP does not encrypt transmitted data, making it vulnerable to interception.

- **Security Implications:**

  - Attackers on the same network can **easily sniff traffic** and steal login credentials.
  - Credentials intercepted this way could be used for unauthorized access, credential stuffing, or identity theft.
  - Demonstrates why websites must use **HTTPS encryption** to secure authentication data.

- **Evidence & Screenshots:**

  - Packet capture screenshot showing **HTTP POST request with login credentials**.
  - Filter applied: `http.request.method == "POST"` to locate authentication requests.
  - Comparison with an HTTPS request to highlight encrypted vs. unencrypted traffic.

- **Next Steps:**

  - Test traffic with an HTTPS-enabled login page and observe the differences.
  - Analyze TLS handshake processes and encryption methods for securing web communications.

## 🔒 Security Risks & Recommendations

### 🚨 Identified Risks

- Credentials are transmitted **in plaintext**, making them easy to intercept.
- Attackers can **eavesdrop** on network traffic and steal sensitive data.

### ✅ Mitigation Strategies

- Enforce **HTTPS encryption** using SSL/TLS.
- Implement **HSTS (HTTP Strict Transport Security)** to prevent protocol downgrades.
- Encourage **password hashing & salting** instead of storing plaintext credentials.

## 📌 Conclusion

This project demonstrates the importance of **securing network traffic** by enforcing HTTPS. Future explorations could include **TLS handshake analysis**, using proxies to inspect encrypted traffic, and identifying misconfigured HTTPS settings.

## 📂 Resources

- [Wireshark Official Documentation](https://www.wireshark.org/docs/)
- OWASP: Transport Layer Protection

---

💡 *If you found this project helpful, feel free to ⭐ the repository!*
