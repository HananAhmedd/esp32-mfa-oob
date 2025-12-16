# esp32-mfa-oob
# SecureMFA – ESP32 Out-of-Band Approval System

SecureMFA is a university project that explores an approval-based Multi-Factor Authentication (MFA) system using an ESP32 as a physical authenticator and an out-of-band communication channel.

The goal of the project is to move beyond traditional OTP-based MFA and instead require explicit user approval from a trusted hardware device before granting access.

---

## Project Idea

The authentication flow works as follows:

- The user logs in with username and password
- The server pauses the login process (pending authentication)
- A login request is shown on a separate out-of-band page
- The user approves the request using an ESP32 device
- Only after approval, the server completes the login

The ESP32 acts as a physical trust anchor, making it difficult to spoof authentication without possession of the device.

---

## Architecture Overview

The system is composed of three main components:

- **Web Application**  
  Handles login, session management, and verification of approval requests  
  (PHP + MySQL, running on XAMPP)

- **ESP32 Hardware Authenticator**  
  Used by the user to approve or deny login attempts

- **Out-of-Band Notification Page**  
  A separate interface that displays pending login requests and improves user awareness

For development and local testing, the ESP32 communicates with the web application through a serial bridge.

---

## Project Status

This project is under active development.

Planned milestones:

- [x] Repository initialization
- [ ] Define authentication state flow
- [ ] Design database schema
- [ ] Implement login and waiting logic
- [ ] Create out-of-band notification page
- [ ] Integrate ESP32 approval via serial bridge
- [ ] Security improvements and documentation

---

## Notes

This project is developed for educational purposes as part of a System Security course.
