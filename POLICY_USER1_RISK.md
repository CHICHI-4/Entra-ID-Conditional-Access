Policy name: CA001-Risk based password change

Assignment
- Users: Include users and groups; chinwe's user1
- Resources: All cloud apps
- Conditions: user risk levels: Medium, High
- Access controls (Grant): Controls: Require password change
- Enable Policy: On 

Policy name: CA001A-Sign-in risk
Assignment
- Users: Include users and groups; chinwe's user1
- Resources: All cloud apps
- Conditions: sign-in risk: Medium, High
- Access controls (Grant): Block
- Enable Policy: Report-only
