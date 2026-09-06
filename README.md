# Phishing-Awareness-Simulation

(Phishing Awareness Simulation with Gophish)


Overview


This project demonstrates the end-to-end process of planning, deploying, and analyzing a controlled phishing simulation using Gophish, an open-source phishing framework commonly used by security teams for employee awareness training. The goal was to replicate the full workflow a SOC/security awareness analyst would follow, from infrastructure setup to reporting in a safe, self-administered test.


Tools used: Gophish, Kali Linux, Gmail SMTP, Firefox


Step 1: Environment Setup


Deployed a Kali Linux virtual machine as the test environment.


Downloaded the Gophish release binary for Linux (x86_64) from the official GitHub repo.


Extracted the binary and made it executable


Launched Gophish

<img width="1078" height="685" alt="Screenshot 2026-09-06 190537" src="https://github.com/user-attachments/assets/0731597a-71ba-42b3-beba-dfe229e6e68e" />


<img width="1366" height="768" alt="Screenshot 2026-09-05 221115" src="https://github.com/user-attachments/assets/2eed15b9-ea13-41b4-8dcd-ded033c43d27" />



Retrieved the auto-generated admin credentials from the terminal output and logged into the admin panel at https://127.0.0.1:3333


Completed the forced first-login password reset.


Step 2: Sending Profile Configuration


Created a Sending Profile using Gmail's SMTP relay (smtp.gmail.com:587)


Generated a Gmail App Password (required since Gmail blocks third-party app logins with standard passwords) via Google Account → Security → 2-Step Verification → App Passwords.


Validated the profile with Gophish's built-in "Send Test Email" feature.


Troubleshooting encountered: An initial DNS resolution failure (temporary failure in name resolution) inside the Kali VM blocked outbound SMTP connections. Resolved by restarting the VM and verifying resolution.


Step 3: Landing Page


Built a simulated login page using a basic HTML form (email + password fields).


Enabled Capture Submitted Data and Capture Passwords to log interaction.


Configured a redirect to a real domain post-submission, to mimic a realistic phishing flow.


Step 4: Email Template


Authored a pretext email themed around account security verification, using urgency-based language ("Action Required: Verify Your Account").


Embedded Gophish's tracking variable ({{.URL}}) to generate the unique tracked link per recipient.


Enabled the tracking pixel to log email opens.


<img width="1301" height="668" alt="Screenshot 2026-09-06 192810" src="https://github.com/user-attachments/assets/45e1bbb4-f855-45c7-8f89-87b3568884d4" />



Step 5: Target Group


Created a single-target test group using informed self-consent (myself as the sole recipient) this was a deliberate scoping decision, since running phishing tests on others requires their explicit prior agreement.


Step 6: Campaign Execution


Launched the campaign, linking the sending profile, template, landing page, and target group
Verified email delivery, then manually interacted with the email as a target would: opened → clicked link → submitted test credentials on the landing page.


Full details are captured in the "PHISHING AWARENESS SIMULATION" File.




<img width="678" height="480" alt="Screenshot 2026-09-06 193610" src="https://github.com/user-attachments/assets/9b40853a-fb8a-4936-91b1-123bbe633c23" />

