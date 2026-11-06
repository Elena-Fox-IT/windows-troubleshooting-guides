# Title of the problem
**No internet connection**

## Symptoms
The user cannot access websites.


## Environment
Windows 11, laptop.

## Diagnosis
1. **Confirmed the problem by reproducing it.**
  Tried to open a website in the browser.
<img width="1365" height="662" alt="1" src="https://github.com/user-attachments/assets/97253b68-b634-46ed-8fbe-9977556b485e" />

  - Result: The page didn't load. 
  - Conclusion: the problem reported by the user is real and reproducible.

2. **Checked the network configuration.**
  Ran 'ipconfig /all' and reviewed the Wi-Fi adapter section.
 <img width="1026" height="448" alt="2" src="https://github.com/user-attachments/assets/57fb4fbc-0ad4-4a98-9da5-88431c4ab876" />

  - IPv4 address: valid (assigned by the router).
  - Default gateway: present.
  - DNS servers: 192.0.2.1, which looks unusual for this network.
  - Conclusion: the device is connected to the local network. The DNS address is suspicious and needs to be confirmed by testing.

3. **Tested connectivity by IP address.**
  Ran 'ping 8.8.8.8'.
<img width="777" height="295" alt="3" src="https://github.com/user-attachments/assets/feeec2b8-d3cf-4682-b261-b8ad9aa8057d" />

- Result: replies received.
- Conclusion: the device can reach the internet, so the problem is not the connection itself.

4. **Tested name resolution.**
  Ran 'ping google.com'.
  - Result: "Ping request could not find host google.com."
  - Conclusion: IP address works, but the name does not, so the issue is DNS. Root cause: incorrect manual DNS setting.

## Solution
1. Opened the Wi-Fi adapter properties, then IPv4 settings, and set "Obtain DNS server address automatically".
<img width="806" height="432" alt="4" src="https://github.com/user-attachments/assets/0b572d20-8257-45b5-a47c-d8485a46955d" />

<img width="770" height="392" alt="5" src="https://github.com/user-attachments/assets/887e1102-05b4-4be2-890c-81be7e52670d" />


2. Opened Command Prompt **as administrator** and ran 'ipconfig /flushdns' to clear the DNS cache.
<img width="601" height="267" alt="6" src="https://github.com/user-attachments/assets/35ba7c67-60d1-49c4-a701-2f86a682b3e7" />

3. **Verified the fix:** 'ping google.com' returned replies and websites opened normally.
<img width="592" height="257" alt="image" src="https://github.com/user-attachments/assets/2f440d22-03a0-4e62-9089-6f74170ac7ed" />

<img width="1427" height="676" alt="7" src="https://github.com/user-attachments/assets/6bac542a-ec3c-40bc-87bf-c0b0e8fcc769" />

## Prevention
- Avoid manual DNS settings unless required.


## Notes
- If a user reports "Wi-Fi connected but no websites open", check DNS first.
