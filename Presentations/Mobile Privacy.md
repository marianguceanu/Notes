# Mobile privacy. It is threatened, motive is good but implementation is bad.

Quick dive into politic reasons and then the techy stuff :)

---

## Abbreviations
- **CSAR** → *Regulation to Prevent and Combat Child Sexual Abuse*  
- **CSAM** → *Child Sexual Abuse Material*  

---

# EU Chat Control: Summary 

- EU is debating implementing the **CSAR**, widely referred to as **“Chat Control”**.
- [What is CSAR? The Legislative Proposal](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A52022PC0209)
- If passed, requires messaging services (WhatsApp, Signal, iMessage, etc.) to **scan private communications** (including encrypted ones) for CSAM.
- Scanning would be client side, before encryption.
- You're constantly under surveillance :). (kind of like north koreans, not as drastic though)
- Mass surveillance from the government could turn George Orwell's "1984" into reality.
- **BONUS**: Isn't it bad enough that Meta already has most of the private chats data of the world?

---

# Possible Solutions

# 1. Political / Civic
- Support digital rights groups (e.g., **EFF, EDRi, Privacy International**).  
- Contact local representatives — especially in undecided countries (Germany, Belgium, Ireland, Finland, Luxembourg, Romania).  
- [Here is the current state](https://fightchatcontrol.eu/)
- Raise awareness: public pushback has stopped similar laws before.  

---

# 2. Technical
## Alternative messaging apps + encryption layers 

---

# *Signal* (may exit EU to avoid compliance)  
[Platform](https://signal.org/)
- Encryption: Uses the Signal Protocol (double ratchet, X3DH, and prekeys). 
    - Considered the **gold standard** of end-to-end encryption.
- Metadata: Signal tries to minimize metadata. 
    - Server knows your phone number and when you last connected, not who you messaged/what you sent.
- Identifiers: Relies on a phone number for account creation 
    - Privacy drawback if you want complete anonymity.
- Trust model: Centralized 
    - Must trust Signal’s servers to deliver messages, they cannot decrypt content.

---

# *Session* (decentralized, no phone number required)  
[Platform](https://getsession.org/)
- Encryption: Based on the Signal protocol, adapted for a decentralized network 
    - Uses the Oxen Service Node network.
- Metadata: No central server. 
    - Messages are routed via onion-style routing through multiple nodes, reducing metadata leaks.
- Identifiers: No phone number required. 
        - You get a random Session ID.
- Trust model: Decentralized 
    - Privacy doesn’t depend on one company/server.
- Trade-offs
    - Message delivery can be slower than Signal because of the multi-hop routing.
    - No voice or video calls.

---

# *SimpleX Chat* (no identifiers)  
[Platform](https://simplex.chat/)
- Encryption: e2e encrypted
    - Different philosophy: no static identifiers at all.
- Metadata: No permanent user IDs. 
    - Communication is handled via disposable, one-time addresses (called “SimpleX queues”). This makes metadata correlation nearly impossible.
- Identifiers: You don’t need a phone number, email, or a permanent username.
- Trust model: Decentralized in design 
    - Messages are relayed via servers, but these servers don’t know sender or recipient identities, and you can even run your own relay.
- Trade-offs
    - Still a newer project compared to Signal/Session, less user trust
    - No group video / voice calls

---

## Local encryption:  
- **PGP / GPG** → Encrypt messages/files before sending.  
- **age** → Modern alternative to PGP, simpler to use.  
- **Cryptomator / VeraCrypt** → Encrypt files before uploading to cloud.  
- **OnionShare** → Share files/messages via Tor securely.  

## Network privacy:  
- **VPNs** outside EU jurisdiction (Mullvad, IVPN, ProtonVPN).  
- **Tor** for anonymous routing.  
- **DNS over HTTPS/TLS** to prevent ISP tracking.  

---

# 3. More Privacy (Change OS/ROM + fossify your life)
- Use **privacy-focused OS** (GrapheneOS, iodéOS, CalyxOS, /e/OS) (will come later on).  
- Go more open source with **F-Droid** (open-source app store).  
    - Replace Google apps with FOSS apps such as [Fossify](https://www.fossify.org/) 
    - Start using ProtonMail/Tutanota for your personal mail
    - Use a keyboard that doesn't connect to the internet
        - [FUTO organization](https://wiki.futo.org/) and their [keyboard](https://keyboard.futo.org/)
- Use firewalls like **NetGuard** or **RethinkDNS**.  
- Limit app permissions (location, camera, microphone).  
- Keep a **secondary phone** (Wi-Fi only, no SIM, never eSIM) for private comms. (If you want to go deeper into it) 

---

### 4. Practical Habits
- Don’t store sensitive files in cloud apps unencrypted.  
- Separate “casual” and “sensitive” communications.  
- Practice data minimization: share only what’s strictly necessary.  

---

# GrapheneOS
## Advantages:
    - Best-in-class security hardening.
    - Regular updates (fast, tightly synced with Google).
    - Can run apps in isolated profiles, including Play Services (sandboxed).
    
## Disadvantages:
    - Pixel-only support.
    - No microG → weaker compatibility with Google-dependent apps.
    - More “security first” than “convenience”.

---

# CalyxOS

## Advantages:
    - Easier migration for normal users (Google-dependent apps mostly work).
    - Good balance between privacy & usability.
    - Runs on Pixels + some other devices.

## Disadvantages:
    - Less hardened than GrapheneOS.
    - Updates slightly slower.
    - Still some Google dependence if you enable microG.

---

# iodéOS

## Advantages:
    - Built-in ad/tracker blocking → privacy out of the box.
    - User-friendly setup.
    - Broader device support (not just Pixels), because it is built on LineageOS -> LTS.

## Disadvantages:
    - Security hardening not as strong as GrapheneOS.
    - Smaller dev team → updates not as fast.
    - Some reliance on microG if you need Google apps.

---

# /e/OS (Murena)

## Advantages:
    - Very user-friendly (almost iPhone-like onboarding).
    - Comes with its own app store + Murena cloud.
    - Good for people who want “Google-free but easy.”

## Disadvantages:
    - Security hardening is weaker than GrapheneOS.
    - Heavy reliance on microG.
    - Updates slower than Pixels/GrapheneOS.

---

# Conclusions 
Chat Control aims to combat child abuse but risks **eroding digital privacy for everyone**.  
Once client-side scanning backdoors exist, they can be repurposed for other types of surveillance.  

**Your defense is twofold:**  
1. **Political action now** (before it passes).  
2. **Technical & lifestyle countermeasures** (if it does).  
