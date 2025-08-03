# 🛡️ Project Name: ShadowMesh
> A decentralized, end-to-end encrypted, privacy-first communication platform that runs without centralized servers, user data collection, or app store distribution.

## 🚨 DISCLAIMER
This project is **NOT** for profit, commercial use, or public distribution via Google Play or App Store. This is a **community-driven, open-source privacy contribution**, encouraging users to build and host the app themselves. Use it responsibly and understand that **once access is lost, there is no recovery.**

---

## 🧠 Philosophy

ShadowMesh is built with the following **privacy-first principles**:

1. **Zero Trust Model** — not even the developer can access user data.
2. **No Data Recovery** — user anonymity is preserved through irreversible identity design.
3. **No Central Hosting** — users host their own backend servers at home.
4. **No App Store** — users must build and install the app themselves.
5. **No Logs / No IP Trace** — complete anonymity, even if a node is compromised.
6. **Self-Destruct Option** — emergency kill-switch erases all traces locally.

---

## 📦 Features

- ✅ End-to-End Encrypted Messaging (E2EE)
- ✅ Self-hosted Home Server (Linux/Raspberry Pi recommended)
- ✅ Anonymous Identity via Random UUIDs
- ✅ Temporary Identity Sessions (No recovery option)
- ✅ Tor-based Traffic Routing (Onion Routing)
- ✅ Kill-Switch to Wipe All Data
- ✅ No IP Storage / Metadata-Free
- ✅ Peer-to-Peer Connectivity via Tor Hidden Services
- ✅ Enforced app-side proxy/VPN validation
- ❌ No Email / Phone / Contact Access
- ❌ No Advertising, No Analytics

---

## ⚙️ Architecture

### 1. **Client-Side (Mobile App - React Native or Flutter)**
- Contains UI, messaging logic, encryption engine.
- Connects to user’s own backend relay (via `.onion` or LAN IP).
- Does **not** know public IP or location of any other user.
- Stores identity in **volatile memory** unless persistent mode is enabled.

### 2. **Home Relay Server**
- Open-source Node.js or Rust-based relay software.
- Runs behind a Tor Hidden Service.
- Passes messages only, no storage or logs.
- Accessible via `.onion` address only.

### 3. **Communication Flow**
- User A App --> Tor --> User B’s Home Server (via Onion) --> User B App
- Entire traffic is onion-routed.
- Messages are encrypted with recipient’s public key.
- No IPs are ever exposed.

---

## 🔐 Security Design

### **Feature	Description**
- Identity	Random UUID or Ed25519 keypair (no username/email)
- Session Storage	Local secure storage (no sync or backup)
- Transport	Encrypted via TLS + Tor Layer
- Message Security	NaCl box (Curve25519 + XSalsa20 + Poly1305)
- Metadata Removal	No IPs, no timestamps, no user agent, no headers
- Compromise Plan	Kill-switch wipes RAM + local secure store

---

## 🔥 Kill Switch

### **The app includes an emergency kill-switch that:**

- Immediately erases:
- - Identity keys
- - Local storage (chats, tokens)
- - Session info
- Secure deletes using platform tools (shred, rm -P, wipe, etc.)
- Overwrites in-memory values with zeroes before shutdown
- Activation Options:
- - Manual button (long press)
- - Codeword or signal received in message
- - Inactivity timeout (optional)

---

## 🧰 Requirements

### **Client**
- React Native / Flutter
- Tor Proxy (e.g., Orbot)
- NaCl or Libsodium library
- Secure storage (iOS Keychain / Android Keystore)

### **Server**
- Linux (Ubuntu/Debian) or Raspberry Pi
- Tor installed and running hidden service
- Node.js or Rust for relay server
- Firewall blocking everything except Tor

---

## 🔧 Setup Instructions

### **1. Clone the Repo**
```bash
git clone https://github.com/youruser/shadowmesh.git
cd shadowmesh
```

### **2. Configure Tor Hidden Service**
- Edit your torrc:
```swift
HiddenServiceDir /var/lib/tor/shadowmesh/
HiddenServicePort 8080 127.0.0.1:8080
```

- Restart Tor:
```bash
sudo systemctl restart tor
```

- Find your .onion domain:
```bash
cat /var/lib/tor/shadowmesh/hostname
```

### **3. Run the Server**
```bash
cd server
npm install
node index.js
```

### **4. Build the App (Manual Only)**
- No pre-built APKs or IPAs provided.
```bash
cd client
npm install
npx expo run:android
# or
npx react-native run-android
```

---

## 🚫 No IP Trace Policy
- All connections go through Tor .onion addresses.
- No IP is ever stored, even in memory.
- Traffic between clients and servers is fully encrypted and anonymous.
- App refuses to operate if VPN/Tor is not active (configurable).

---

## 🕵️ FAQ

### **Q: What if I lose my device or data?**
- You cannot recover it. That’s the point. No one—not even the developer—can help you.

### **Q: Can governments or hackers track me?**
- Not if you follow proper opsec. Use Tor, avoid revealing your identity, and always run the kill-switch if you're at risk.

### **Q: Can someone build a fake version with backdoors?**
- Yes. That’s why this project must be self-built and audited by the user. No third-party builds are trusted.

---

## ❤️ Contributing
**If you understand secure communications, cryptography, or privacy law and want to help—contribute on GitHub!**

---

## 🛡️ License  
**GNU Affero General Public License v3.0 (AGPL-3.0)** — redistribution allowed only if the full source is made available, with no tracking, monetization, or proprietary modifications permitted.

---

## 👥 Credits
**Created by privacy-focused developers and contributors who believe communication should be truly free and safe.**
