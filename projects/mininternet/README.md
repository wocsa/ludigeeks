# Activity Sheet: The Minimal Internet (MiniInternet)

## 🎯 Objectives
- Understand **network threats**, including:
  - **Denial of Service (DoS) attacks**
  - **Loss of control over transmitted information** (once shared, data cannot be easily deleted)
  - **Man-in-the-Middle Attacks** _(not included in this session)_

---

## ⏳ Activity Duration
**2 hour 30 minutes**

## 👥 Number of Participants
- **Minimum**: 3 participants with 3 computers.  
- **Depends on available computers** (participants can work in pairs on a single computer).  

## 🏫 Recommended Age
- Participants must be able to **read, write and count** (approximately **13 years old and older**).

## 🖥️ Required Materials
- **One long and wide cardboard tube**
- **One sheet of paper per service** (bakery, butcher, greengrocer, restaurant, post office, town hall)
- **Web server setup**:
  - Apache web server with PHP module installed on each computer
- **Local network**:
  - router with wifi for example
- **Computers with text editor**:
  - If possible html text editor

---

## 🏗️ Activity Flow

### **1️⃣ Explanation: How Servers and Clients Work**
- The **server** responds to requests from the **client**.
- The **client** sends a request through the **cardboard tube** by **speaking into it**.
- The **server listens through the tube** and then **displays the requested page at the other end**.
- The **client looks through the tube** to see the displayed page.

#### **🔍 Key Takeaways**
- This **mimics how computer networks function**.
- **Wi-Fi transmits communications between clients and servers using inaudible waves**.
- **A computer can be both a client and a server simultaneously**.
- **Optical fiber transmits data using light**.
- **Ethernet cables transmit data using electrical signals**.
- A **network** is a group of computers communicating using a shared connection (Wi-Fi, fiber, or cable).
- **The Internet** is a massive network that connects smaller networks worldwide.
- In this workshop, **we create a local network** simulating the Internet, with different **online stores**.

#### **💡 Web Browsers and Servers**
- **Web browsers** are like a client’s "eye," interpreting and displaying web pages.
- **Web servers** are like the "ears" of the system, listening to requests and responding with web pages.
- A **server does not display anything** on the screen; it simply communicates via the network.

---

### **2️⃣ Hands-on Activity: Creating a Mini Internet**
- Each participant creates their **own online store**.
- The **Wi-Fi router acts as a relay**, forwarding requests between devices.
- Participants **write the web page using HTML**.

#### **Basic HTML Code for a Store Page**
```html
<html>
  <body>
    <h1>Bakery</h1>
    <img src="bakery.jpg" width="200" height="150"><br/>
    <p>
      Welcome to my online store!  
      Place your orders below, and I'll deliver them via mail.
    </p>
    <hr>
    <form>
      Name: <input type="text" name="name"><br>
      Message: <br/>
      <textarea name="message" rows="5" cols="40"></textarea>
      <input type="submit" value="Send"/>
    </form>
  </body>
</html>
