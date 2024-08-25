# SOAR-EDR-PROJECT

---
# SOAR EDR Integration with LimaCharlie, Tines, and Slack

## Overview

This project demonstrates an integration between LimaCharlie for custom detection and response rules, Tines for orchestrating automated workflows, and Slack for real-time communication in a Security Orchestration, Automation, and Response (SOAR) environment. The primary goal of this integration is to enable automated decision-making for isolating potentially compromised systems based on security alerts, with user interaction determining the final action and notifications sent via Slack.

![soar edr 6](https://github.com/user-attachments/assets/1d0da68f-eaa8-4abb-8f23-6a69f5312507)


## Features

- **Custom Detection and Response Rules in LimaCharlie:**
  - Monitor and detect suspicious activities on endpoints.
  - Trigger automated workflows based on custom-defined rules.
 
  - ![image](https://github.com/user-attachments/assets/fb7eae2e-2cba-4cf8-ad46-aa0fe39fc70c)
  ![soaredr project 1](https://github.com/user-attachments/assets/3cd017af-e89a-426f-837f-4b8490668565)


- **Tines Playbook Integration:**
  - Utilize Tines to create a decision-making workflow that interacts with security analysts.
  - Present a user with a prompt to isolate a system upon detection of a security incident.

![soar edr 4](https://github.com/user-attachments/assets/dc9874c4-e273-44b2-8e4a-7c89830b1c67)


  
- **Slack Notifications:**
  - Real-time notifications are sent to a designated Slack channel whenever an incident is detected.
  - The Slack message includes options for the security analyst to isolate the system or decline the action.
 
If You Choose not to Isolate the System  ![SLACK 1](https://github.com/user-attachments/assets/2540f26e-6bfb-4db3-8505-00b48c059137)  If you choose to Isolate the System ![SLACK 2](https://github.com/user-attachments/assets/e81258d1-a945-4169-8265-73fd7852adb3)                                                               

- **Automated System Isolation:**
  - If the user clicks "Yes" to isolate the system via the Slack notification, the decision is sent to Tines, which then communicates with LimaCharlie to isolate the system automatically.
  ![image](https://github.com/user-attachments/assets/3d45b539-63e1-4949-bc0f-e6d5578d46f4)
![image](https://github.com/user-attachments/assets/713bdf2d-08a7-48a4-ad93-7b940ad2e671)

When you isolate the system the ability to ping will fail.
![image](https://github.com/user-attachments/assets/cec39b00-ea0b-4e23-ae60-ba0ec3969c09)


- **User-Initiated Investigation:**
  - If the user clicks "No" in Slack, the system will not be isolated. A message stating "The computer was not isolated, please investigate" will be generated, and the decision along with relevant details will be sent to Tines.
  - Tines will send an email notification to the designated security team with the details of the incident for further investigation.
![image](https://github.com/user-attachments/assets/12917669-96d5-4e19-8b83-5513da3c881c) ![image](https://github.com/user-attachments/assets/25adbe90-ddfc-4b6e-854f-6b7784eda5c1)

When you choose to not isolate the system the ability to ping will function.
![image](https://github.com/user-attachments/assets/189f4d32-3e06-4c2c-badd-599a276521a2)


## How It Works

1. **Detection Phase:**
   - LimaCharlie continuously monitors endpoints based on custom detection rules.
   - Upon detecting a security event that requires attention, a signal is sent to the Tines playbook.

2. **Decision Workflow:**
   - The Tines playbook triggers a notification in Slack, presenting the security analyst with a decision prompt to either isolate the compromised system or decline the action.
   - The analyst can click "Yes" to isolate or "No" to decline the action directly within Slack.

3. **Automated Response:**
   - **Yes:** Tines sends the isolation command to LimaCharlie, which isolates the system from the network.
   - **No:** A notification message stating, "The computer was not isolated, please investigate" is generated. Tines sends an email to the security team with the incident details.

4. **Incident Reporting:**
   - All actions and decisions are logged and reported via email, within the Tines dashboard, and in Slack, ensuring full traceability of the incident response process.

## Installation

1. **LimaCharlie Setup:**
   - Configure your detection and response rules within LimaCharlie.
   - Ensure your LimaCharlie instance can communicate with external tools like Tines and Slack.

2. **Tines Setup:**
   - Import the provided Tines playbook into your Tines environment.
   - Customize the email notifications and Slack prompts as needed.

3. **Slack Integration:**
   - Set up a Slack app or bot that can send messages to your designated security channel.
   - Integrate Slack with Tines to handle the decision-making prompts and notifications.

4. **Integration:**
   - Link LimaCharlie, Tines, and Slack through API keys or webhooks.
   - Test the integration to ensure that detection events trigger the Tines playbook, Slack notifications are sent, and that the system isolation or investigation workflows execute as expected.

## Conclusion

This project provides a robust framework for automated security incident response with human oversight, leveraging Slack for real-time communication and decision-making, ensuring that potentially compromised systems can be isolated quickly while maintaining flexibility for investigation and decision-making.

---

This version includes the use of Slack for real-time notifications and decision-making, providing a clear overview of how it integrates with the SOAR EDR solution.
