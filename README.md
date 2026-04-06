# NOTE: This repository currently serves as a log book. The full program is not included currently.
# BlackIron: Encrypted End-to-End Secure Chat Application
- **What is BlackIron?**
  BlackIron is a secure, terminal-based chat application built with end-to-end encryption (E2EE) and advanced session management. It allows users to create and join private chat sessions with full control over membership, messaging, and administrative privileges. The system is designed with security-first principles, leveraging modern cryptography to protect user communications and session integrity.
# Features:
# **Secure Messaging:**
- AES-GCM Encryption: All messages are encrypted using 256-bit AES in Galois/Counter Mode (GCM), ensuring both confidentiality and integrity.
- Authenticated Additional Data (AAD): Each message includes session ID, sender UUID, and sequence number to prevent tampering.
- Sequence Tracking: Each message carries a sequence counter to prevent replay attacks.
# **Authentication & Identity:**
- Ed25519 Digital Signatures: Administrative commands are signed with Ed25519 private keys, ensuring only session owners can execute critical actions (e.g., kick, ban, delete session).
- Recovery Tokens: Secure hash-based recovery tokens allow owners to regain administrative access if needed.
# **Session Management:**
- User Roles: Sessions distinguish between owners and regular participants.
- Access Control: Owners can define allowed and banned users for their sessions.
- Session Persistence: Active sessions maintain secure state across reconnects for verified users.
- Administrative Commands:
  - /kick <uuid> – Remove a user from the session.
  - /ban <uuid> – Ban a user permanently from the session.
  - /delete – Delete the session entirely.
  - /role <token> – Restore owner privileges via a secure recovery token.
# **Robust Server Architecture**
- Multi-threaded Socket Server: Supports concurrent client connections using Python’s socket and threading.
- Replay Protection: Sequence counters prevent message replay attacks.
- Real-time Broadcast: Encrypted messages are securely broadcasted to all session participants except the sender.
- Session Safety: Each session tracks active users, banned users, and ownership securely with thread-safe access.
# **Technical Stack**
- Language: Python 3
- Cryptography: cryptography library (AES-GCM, Ed25519)
- Networking: TCP sockets with JSON message protocol
- Concurrency: Threading for client handling and message listening
