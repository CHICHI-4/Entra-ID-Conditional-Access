Task 1 — Test users & licenses
- Usernames: chinwes_user1@skt42.onmicrosoft.com,  chinwes-user2@skt42.onmicrosoft.com
- License assignments: Microsoft 365 E5 subscription for User 1 and  User2.
- Reason:    Identity Protection features (risk detection + remediation) require Azure AD Premium P2 for both detection and "require password change" remediation.


Task 2 — Sign-in risk CA policy (User1)
- Policy name: CA001-Risk based password change
- Users: include chinwe's user1
- Cloud apps: All cloud apps 
- Conditions: User risk = Medium, High
- Grant controls (Grant): Require password change 
- Session controls: none

Sign-in risk CA policy (User1)
- Policy name: Sign in risk
- Users: include chinwe's user1
- Cloud apps: All cloud apps 
- Conditions: sign in risk = Medium, High
- Grant controls (Block): none
- Session controls: none
- Limitations: The condition "Sign in risk" cannot go with the grant control "password change"
- Policy state:Toggle to On


  Task 3 — Simulate Medium/High sign-in risk
- Methods: Ran a Simulation  on Microsoft graph using this "https://graph.microsoft.com/v1.0/identityprotection/riskyusers/230e8955-6703-4613-8f5d-eb878dcc15f8/confirmcompromised
  Used Tor browser to try to sign in anonymously; opened my windows machine on my host system's virtual box, and downloaded Tor browser,put in login details.
- Reason: Tor browser can be used for anonymous sign-in risk.


Task 4 — Enforcement outcome
- Visible experience: User sees a remediation prompt to change their password or receives an email to change password depending on remediation path.
<img width="958" height="540" alt="Simulation result for User 1" src="https://github.com/user-attachments/assets/8b43f0d0-d78b-4a07-8a8f-7857c7873234" />
<img width="850" height="14" alt="User 1 log" src="https://github.com/user-attachments/assets/42c9e73e-6b84-4a6d-bf29-97f92321021f" />
<img width="1920" height="1080" alt="Security result for User 1 on Entra ID" src="https://github.com/user-attachments/assets/1bdfaf01-ac70-4898-82a8-354097c11f5f" />

Task 5 — Location CA policy (User2)
- Policy name: `CA002-Location base
- Users: include chinwe's user2
- Named location: Nigeria block 1 (create by Microsoft location), Location:Nigeria
- Network — Include: Nigeria
- Condition: Sign-in risk
- Grant: Block access
- Enabled policy: on


Task 6 — Test blocking
- Methods: Used firefox browser on my host system and attempted sign in.
  <img width="944" height="532" alt="Simulation result for User 2" src="https://github.com/user-attachments/assets/5514fc49-4e01-47a9-8017-2c2f50503016" />
<img width="870" height="13" alt="User 2 log" src="https://github.com/user-attachments/assets/68d1389f-da1a-4cfe-b372-d4607fd70507" />


