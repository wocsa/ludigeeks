# Activity Sheet: Secret Codes

## 🎯 Objectives
- Understand how to create a **strong password** that is hard to steal.
- Learn how **encryption** works to protect information.
- Discover how encryption can be **broken (decryption)**.

---

## ⏳ Activity Duration
**1 hour 30 minutes**

## 👥 Number of Participants
- **Minimum**: 2 participants with 2 computers.  
- **Depends on available computers** (participants can work in pairs on a single computer).  

## 🏫 Recommended Age
- Participants must be able to **read, write and count** (approximately **7 years and older**).

## 🖥️ Required Materials
- One **computer per participant**.
- The **explanatory sheet** for the Scratch program **under redevelopment in opensource format***.
- The **scratch** softwar (available online [scratch MIT live editor](https://scratch.mit.edu/projects/editor/))


---

## 🏗️ Activity Flow

### **1️⃣ Game: Secret Message Exchange**
- **Scenario**: Participants exchange **secret messages on paper** without letting the facilitator understand them.
- **Example**: Passing notes in class without the teacher being able to read them.
- Each participant receives a **Caesar cipher wheel**.
- Pairs are formed, and each duo **chooses a shift** for their alphabet.
- The pairs **separate**, and one participant writes an **encrypted message** for their partner.
  - ✅ *Success criteria:* The message must be a **full sentence**, correctly written in French.
- The recipient **decrypts the message** and verifies its accuracy with the sender.
- Groups then **exchange their messages with other pairs** and try to **decrypt** a message from another team.

#### **🔍 Decryption Trick**
- Identify the **most frequently used letter** in the message.
- The most common letter in French is **"E" (17.26% occurrence)**.
- By comparing **E with the most frequent letter in the encrypted message**, participants can determine the **shift value**.

#### **📊 Letter Frequency in French**
| **Letter** | **Frequency (%)** | **Letter** | **Frequency (%)** |
|-----------|----------------|-----------|----------------|
| A | 8.40% | N | 7.13% |
| B | 1.06% | O | 5.26% |
| C | 3.03% | P | 3.01% |
| D | 4.18% | Q | 0.99% |
| E | 17.26% | R | 6.55% |
| F | 1.12% | S | 8.08% |
| G | 1.27% | T | 7.07% |
| H | 0.92% | U | 5.74% |
| I | 7.34% | V | 1.32% |
| J | 0.31% | W | 0.04% |
| K | 0.05% | X | 0.45% |
| L | 6.01% | Y | 0.30% |
| M | 2.96% | Z | 0.12% |

**🔹 Key Insight:**  
- The longer the sentence, the **easier it is to analyze letter frequency**.
- Short words **don't provide enough data** for frequency-based decryption.

---

### **2️⃣ Construction: Hiding a Secret Code in Math**
- Each participant **chooses a secret number** (e.g., **8345**).
- They create **math operations** that, when solved, result in **zero** (hiding the secret inside the calculations).
- Participants **swap computers** and attempt to **guess another participant’s secret number**.
- They then brainstorm ways to **better protect their secret code**.

---

### **3️⃣ Debriefing: Understanding Security Risks**
After the activity, the facilitator leads a discussion on **security weaknesses**:

#### **🔴 Identified Problems**
1. **Reverse Engineering**  
   - If an attacker can **reverse the math operations**, they can discover the secret number.
  
2. **Frequency Analysis Attack**  
   - The **most common letter** in the encrypted text can reveal the **cipher shift**.

3. **Collision Risk**  
   - A **wrong answer might still be validated** by the program due to **weak encryption**.

#### **🔹 What Are the Solutions?**
| **Category** | **Ref** | **Best Practice** |
|-------------|--------|----------------------|
| **Passwords** | MDP-02 | Use a **long and complex password**. |
| **Passwords** | MDP-03 | Use a **password that is impossible to guess**. |
| **Passwords** | MDP-06 | **Never share your password** with anyone. |
| **Mobile Security** | SM-02 | **Encrypt** the device's data. |
| **Mobile Security** | SM-10 | **Do not store confidential information** without protection. |
| **Ransomware Protection** | RAN-08 | Use **complex passwords** and **change them regularly**. |

---

## 📌 Additional Resources
- 🔗 [How to Remember Your Password](https://fr.wikihow.com/se-souvenir-de-son-mot-de-passe)
- 🔗 [WOCSA Security Awareness Check](https://www.wocsa.org/qcheck.php)

---

## 🔎 Summary
1. **Encrypt and exchange secret messages** using the Caesar cipher.  
2. **Decrypt other messages** using letter frequency analysis.  
3. **Create a hidden secret code** with math operations.  
4. **Understand cybersecurity threats** such as frequency analysis and reverse engineering.  
5. **Discuss security best practices** to protect passwords and encrypted data.  

This activity teaches **the importance of encryption, strong passwords, and data security! 🔐**  

---

## 🎯 Get Involved!

🔗 **GitHub Repository** → [github.com/wocsa/ludigeeks](https://github.com/wocsa/ludigeeks/tree/master/projects/secret_code/)  
📩 **Contact us** → [WOCSA Contact Form](https://www.wocsa.org/pages/contact.php)

🚀 **Join Ludigeeks and help spread cybersecurity awareness!**
[WOCSA Contact Form](https://www.wocsa.org/pages/contact.php)
