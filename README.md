# Console-DNS-Block

# 🎮 Console DNS Blocklist (2026 Edition)

A curated, DNS blocklist designed for self-hosted DNS (AdGuard Home, Pi-hole). This list targets mandatory updates, aggressive telemetry, and tracking across all major gaming platforms while keeping login services functional.

---

## 🧐 What is it?
This is a centralized collection of domain filters for consoles. Instead of manually adding rules to every device, you can link this repository to your DNS server to keep your consoles "frozen" on their current firmware—perfect for the "waiting room" before a jailbreak.

## 🚀 What does it do?
* **Blocks Mandatory Updates:** Prevents PS4, PS5, Switch, and Xbox from "calling home" to download new system software.
* **Kills Telemetry:** Stops consoles from sending usage data and "annoying" background tracking to corporate servers.
* **Maintains Playability:** Uses "Exception Rules" (Whitelist) to ensure you can still sign in to PSN/Nintendo/Xbox Live and play your existing games online.

## 🛠 How does it do it?
It utilizes **AdGuard/uBlock syntax** (`||domain.com^`). 
* **Blocks:** Intercepts requests to update servers and returns a null IP (0.0.0.0).
* **Exceptions:** Uses the `@@` prefix to ensure vital authentication servers are never accidentally blocked.

## 📂 Structure
The project is divided into specialized files so you can choose exactly what to restrict:
* `full-block-List.txt`: Everything combined.
* `sony-block.txt`: PS4 & PS5 specific.
* `nintendo-block.txt`: Switch & Legacy support.
* `microsoft.txt`: Xbox and PC publisher telemetry. Careful as it might block windows services or not let games play at all. more test needed.
* `sega-ea-block.txt`: Sega & EA publisher telemetry

---

## 📥 How to Install

### **For AdGuard Home (Recommended)**
1.  Go to **Filters** -> **DNS Blocklists**.
2.  Click **Add blocklist** -> **Add a custom list**.
3.  Name it `ZixX3r-DNS-consoles-blocker`.
4.  Paste the **Raw** URL from this GitHub (e.g., `https://raw.githubusercontent.com/ZixX3r/Console-DNS-Block/refs/heads/main/full-block-List.txt`).
5.  Set the update interval to **24 hours**.

### **For Pi-hole**
1.  Go to **Group Management** -> **Adlists**.
2.  Paste the **Raw** URL in the **Address** field.
3.  Click **Add**.
4.  Run `pihole -g` in your terminal or click **Update Gravity**.

---

## 🤝 Credits & Thank You
This project is a compilation of community knowledge. Special thanks to:
* **The PS4/PS5 Scene:** For identifying regional update nodes.
* **MagicStuffCL & amende155:** For the initial domain research.
* **Drakmor (nanoDNS):** For the exception logic inspiration.
* **Gemini (AI Assistant):** For help in the process.

---

## ⚠️ Technical Warning:
The Switch 2 and late-model PS5s are increasingly using DoH (DNS over HTTPS). Even with these blocks, if the console has "hardcoded" DNS settings (like 8.8.8.8), it might bypass AdGuard entirely. On your DNS-blocker, look into creating a NAT Redirect rule that forces all traffic on port 53 to go to your AdGuard/pihole IP, regardless of what the console tries to do.

---

## ⚠️ Disclaimer
* I'm just an entusiast, if there any errors or things not working, just let me know, and I'll try fixing it right away.
* This list is provided for educational and privacy purposes. Blocking updates can sometimes cause errors in some games. Use at your own risk.*
* Keep the scene Alive! 
