<div align="center">

# <span style="color:#FF0000;">APEX Baileys</span> 🔥

<img src="https://files.catbox.moe/3g1ep9.jpg" width="600"/>

<br>

<!-- Logos -->
<img src="https://upload.wikimedia.org/wikipedia/commons/6/6a/JavaScript-logo.png" width="90"/>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Node.js_logo.svg/768px-Node.js_logo.svg.png" width="120"/>

<br><br>

A modern, stable and enhanced WhatsApp Web API library  
Built for developers who want **speed, stability and full control**  
Developed by **RADIO DEMON** — APEX / Dark Team  

</div>

---

[🌐 Visit Official Site](https://apex-official.vercel.app/)  
[💬 WhatsApp Updates Channel](https://whatsapp.com/channel/0029Vb6qkXM8V0tvdYh1fJ2g)

---

## 🔥 Features Overview

### ✔ Core Fixes
- ⚡ LID linking completely fixed  
- ⚡ Session stabilization  
- ⚡ Restart-safe authentication  
- ⚡ Compatible with every WhatsApp update

### ✔ Authentication Support
- 🔑 QR Code Login  
- 🔑 Pairing (8-digit) Login  
- 🔑 Multi-device support  

### ✔ Extra Enhancements
- 🚀 Faster group operations  
- 📦 Full media support (images, videos, audio, docs, stickers)  
- 🔄 Auto reconnect system  
- 🛠 Clean & readable error outputs  
- 💻 Developer-friendly structure  
- 📝 Supports TypeScript and JavaScript projects  

---

## 🧩 Tech Stack
<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" width="70"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" width="70"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="70"/>
</div>

---

## 🎨 Example Usage (JavaScript)

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
