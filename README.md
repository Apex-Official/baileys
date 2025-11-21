<div align='center'>

<h1>APEX Baileys</h1>

<img src="https://files.catbox.moe/3g1ep9.jpg" width="600"/>

<br><br>

<!-- JS & Node Logos -->
<img src="https://upload.wikimedia.org/wikipedia/commons/6/6a/JavaScript-logo.png" width="90"/>
<img src="https://upload.wikimedia.org/wikipedia/commons/d/d9/Node.js_logo.svg" width="120"/>

<br><br>

A modern, stable and enhanced WhatsApp Web API library  
Built for developers who want **speed, stability and full control**  
Developed by **RADIO DEMON** — APEX / Dark Team  

</div>

---

## 🔧 What is APEX Baileys?

APEX Baileys is an improved and modified version of the WhatsApp Web API.  
It focuses on **performance**, **clean handling**, and **support for all modern WhatsApp login methods**.

The goal is to give developers a **production-ready** library that works smoothly without patching or editing core files.

---

## 🚀 Features Overview

### ✔ Core Fixes
- LID linking completely fixed  
- Session stabilization  
- Restart-safe authentication  
- Compatible with every WhatsApp update

### ✔ Authentication Support
- QR Code Login  
- Pairing (8-digit) Login  
- Multi-device support  

### ✔ Extra Enhancements
- Faster group operations  
- Full media support (images, videos, audio, docs, stickers)  
- Auto reconnect system  
- Clean & readable error outputs  
- Developer-friendly structure  
- Supports TypeScript and JavaScript projects  

---

## 📁 Example Usage (JavaScript)

```js
import makeWASocket from "apex-baileys";
import { useMultiFileAuthState } from "apex-baileys";

async function start() {
  const { state, saveCreds } = await useMultiFileAuthState("./session");

  const sock = makeWASocket({
    printQRInTerminal: true,
    auth: state
  });

  sock.ev.on("creds.update", saveCreds);

  sock.ev.on("messages.upsert", ({ messages }) => {
    const m = messages[0];

    if (!m.message) return;

    console.log("New Message:", m.message);

    if (m.message.conversation === "ping") {
      sock.sendMessage(m.key.remoteJid, { text: "pong!" });
    }
  });
}

start();
