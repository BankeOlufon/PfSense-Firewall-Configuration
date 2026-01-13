# PfSense-Firewall-Configuration
Firewall Configuration with PfSense in a Virtual Environment

<img width="738" height="589" alt="image" src="https://github.com/user-attachments/assets/37336ea5-1075-4036-a2c1-453b51fe9ef9" />


Step 1: Install PfSense

Step 2: 
Allocate Memory
<img width="1914" height="173" alt="image" src="https://github.com/user-attachments/assets/5e1d99a4-f961-4d72-9ab5-a810e3c593be" />


Step 3:
Adjust Boot Order
<img width="1918" height="347" alt="image" src="https://github.com/user-attachments/assets/88242b98-edbc-42a5-b18c-2c922245cf7b" />

Step 4:
Allocate Adapters.
####
SIMPLE ADAPTER EXPLANATION: So basically, LAN0 is internal, LAN1 is guest. Guest networks cannot talk to Internal networks. Like in a bank, you have two networks. BANK-STAFF-WIFI and BANK-GUEST-WIFI BANK-GUEST-WIFI is not allowed to speak to BANK-STAFF-WIFI regardless of if it is KALI or windows and vice versa. SO LAN1 can either be kali or windows and LAN0 can either be KALI or Windows. pfsense just decides who can speak to who.

pfSense is basically asking one question for every packet:

“You came from where, and you want to go where — is that allowed?”

Examples:

🔴 LAN1 → 🟢 LAN0 ❌ (blocked)

🟢 LAN0 → 🌍 Internet ✅ (allowed)

🔴 LAN1 → 🌍 Internet ✅ (usually allowed)

🟢 LAN0 → 🔴 LAN1 ❌ (often blocked too)

**Internal networks never reach the internet directly — pfSense routes them out through its WAN.**
####

Adapter 1: (Bridged - WAN) 
Purpose: Connects pfSense to the host’s real network / internet
Traffic: pfSense WAN interface uses this to send/receive traffic from the outside world

<img width="817" height="380" alt="image" src="https://github.com/user-attachments/assets/8f096f7c-05c2-4e2b-9126-7e6d64801bc3" />


Adapter 2:
Purpose: Internal Network (LAN) This is a safe, isolated LAN for lab VMs that aren’t “attacking” anything
Traffic: VMs on this network can talk to each other and route through pfSense to the WAN (internet) if allowed

<img width="808" height="320" alt="image" src="https://github.com/user-attachments/assets/de29668c-4a1d-4402-8455-8e68f6c50fc2" />


Adapter 3: Internal Network (LAN) Purpose: Isolated network for penetration testing
Traffic: Only attacker + target VMs exist here

<img width="822" height="326" alt="image" src="https://github.com/user-attachments/assets/5799e7ff-5bd9-4e82-a92a-613a17cf13ad" />



