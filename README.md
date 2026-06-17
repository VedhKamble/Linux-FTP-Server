# FTP Server Lab (vsftpd)

##  Project Overview

This project demonstrates the installation, configuration, and testing of an FTP server using **vsftpd (Very Secure FTP Daemon)** on Linux.

The implementation covers different FTP authentication methods, user access restrictions, file transfer operations, and firewall-based service control. The server was tested from a separate Linux client machine to verify real network communication.

---

##  Lab Architecture
```
            FTP Client
         (Linux Machine)
                |
                |
          FTP Connection
                |
                |
      +-------------------+
      |                   |
      |  FTP Server       |
      |  Linux + vsftpd   |
      |                   |
      +-------------------+
                |
    -------------------------
    |           |           |
Anonymous      Real       Chroot
               Users       Users
                
```
---

##  Technologies Used
- Linux
- vsftpd FTP Server
- FTP Protocol
- firewalld
- System Users & Permissions

---

##  Implemented Features

### 1. Anonymous FTP Access
Configured anonymous FTP login.

Tested:
- Login with anonymous user
- Access default FTP directory
- Download files

Restrictions:
- Upload disabled
- Access outside FTP directory blocked

---

### 2. Local / Real User Authentication
Configured system-based FTP users.

Tested:
- Login using Linux username/password
- Upload files
- Download files
- File operations inside user directory

Authentication validation:
- Correct password → Allowed
- Wrong/empty password → Denied

---

### 3. Chroot Restricted Users
Implemented restricted FTP users using chroot environment.

Features:
- Users are locked inside their home directory
- Cannot navigate to other system directories
- Can upload/download only within allowed location

Tested against:
/etc
/root
/var
/proc

Access was restricted successfully.

---

### 4. FTP User Access Control
Configured FTP user restrictions using:

userlist_enable
userlist_deny

Users added to the deny list were blocked before authentication.

---

### 5. Firewall Integration
Verified FTP service dependency on firewall rules.

Testing:

Before firewall rule:
Client → FTP Server
Connection Denied


After enabling FTP service:
firewall-cmd --permanent --add-service=ftp
firewall-cmd --reload


Result:
Client → FTP Server
Connection Successful


---

##  Testing Summary

| Feature | Status |
|---|---|
| FTP Server Installation | ✅ |
| Client-Server Connection | ✅ |
| Anonymous Login | ✅ |
| Anonymous Download | ✅ |
| Anonymous Upload Restriction | ✅ |
| Real User Login | ✅ |
| File Upload/Download | ✅ |
| Chroot User Isolation | ✅ |
| User Deny List | ✅ |
| Firewall Testing | ✅ |

---

##  Learning Outcomes

Through this project I practiced:

- Linux service management
- FTP server deployment
- User authentication
- File permissions
- Access control
- Chroot security
- Firewall configuration
- Client-server troubleshooting

---

##  Author
Vedh Kamble
Linux Server Administration Practice Project
