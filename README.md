# Senior Design Project Final Report: Table of Contents

Team Members: Harshil Patel (patel3hs@mail.uc.edu) (CS) & Bartosz Kawalkowski (kawalkba@mail.uc.edu) (CS)

Academic Advisor: Nitin Nitin (nitinfu@ucmail.uc.edu

## Project Abstract

The Windows Process Protector is an anti-cheat system designed to monitor and safeguard Windows application processes from unauthorized access. By leveraging techniques like memory protection, code integrity checks, and process monitoring, the system ensures secure and reliable application performance. The project includes a user-friendly web interface that allows users to monitor running processes, receive alerts about potential threats, and prevent malicious activities. This system prioritizes privacy and data security while addressing key challenges in cybersecurity and gaming fairness. Developed with a focus on professional growth, the project integrates knowledge from operating systems, software engineering, and real-world software development practices.

# User Interface Specification

### User Stories and Design Diagrams

- [User Stories](https://github.com/Harshilp20/Senior-Design/blob/main/User-Stories.md)
- [Design Diagrams](https://github.com/Harshilp20/Senior-Design/blob/main/Class-Assignments/Design_Diagrams.pdf)
  - This link for the Design Diagrams will show D0, D1, and D2 diagrams along with their descriptions

# Test Plan and Results

The Windows Process Protector's protection DLL implements four sophisticated security mechanisms to defend processes against common attack vectors:
PE Header Encryption provides fundamental protection by XOR-encrypting the first 4KB of process memory containing critical DOS and PE headers. This renders the executable's structure and entry points unreadable to static analysis tools while maintaining a backup of the original headers for legitimate program execution. When enabled, the protection carefully modifies memory protection attributes to make the headers writable, applies the encryption key to each byte, and then restores the original protection, effectively obfuscating important metadata like section tables, import directories, and entry points.
Memory Scan Detection employs a strategic approach by allocating special "canary" memory regions and monitoring the system's working set information through low-level NT API calls. By examining which memory pages appear in the working set, the system can detect when debugging tools or malware attempt to scan or read process memory. Upon detection, it captures detailed information about the scanning process including PID, process name, and timestamp, then alerts the user through a security notification. This effectively identifies tools attempting memory inspection without authorization.
Anti-Tampering protection implements continuous runtime integrity verification for critical code sections. It identifies read-only executable sections like .text and .rdata, calculates precise CRC32 hashes of their contents during initialization, and then periodically recalculates these hashes to detect any modifications. A dedicated monitoring thread performs these checks at regular intervals, immediately alerting users if any unauthorized code modifications are detected. This protects against runtime code patching, hot-patching, and similar code injection techniques.
Thread Monitoring provides an advanced defense layer by mapping all legitimate code regions from loaded modules, then continuously scanning for threads whose execution begins from unexpected memory locations. The protection maintains a detailed registry of all loaded module address ranges and uses the NtQueryInformationThread API to retrieve thread start addresses. When threads originate from memory regions outside known modules—a common indicator of shellcode injection—the system captures comprehensive diagnostic information including thread IDs, start addresses, and related process details before alerting the user to the potential security breach.

### We Have Currently Demoed the 3 Major Tests As Well:

#### Showcasing Encryption Of PE Headers

- Click [here](https://gyazo.com/1ba593b026f0f37104ae013b4dff1962)
- [Detection Pop-up image](https://github.com/Harshilp20/Senior-Design/blob/main/Testing/InvalidPEFile.png)

#### Showcase Anti-Tampering (Detects CODE or RDATA Modifications)

- Click [here](https://gyazo.com/744e8fd44c80ea856f4bbdc621d8b92a)
- [Detection Pop-up image](https://github.com/Harshilp20/Senior-Design/blob/main/Testing/UnauthorizedCodeTampering.png)

#### Showcasing Suspicious Thread Detection/Thread Monitoring

- Click [here](https://gyazo.com/4bdba0c8e19dd8b0d17f365d5e1cc46e)
- [Detection Pop-up image](https://github.com/Harshilp20/Senior-Design/blob/main/Testing/SuspiciousThreadDetected.png)


# User Manual

Our current User Manual with details about our software and strategies can be found [here](https://github.com/Harshilp20/Senior-Design/blob/main/WindowsProcessProtector_ResearchDocument.pdf)

# Spring Final PPT Presentation

- [Click here to view Slides]()

# Final Expo Poster

Our final Expo Poster can be found [here](https://github.com/Harshilp20/Senior-Design/blob/main/Windows_Process_Protector.pdf)


# Self Assessment Essays

- [Bartosz Kawalkowski Fall Initial Assessment](https://github.com/Harshilp20/Senior-Design/blob/main/Class-Assignments/Assignment3_kawalkba.pdf)
- [Bartosz Kawalkowski Final Assessment](https://github.com/Harshilp20/Senior-Design/blob/main/Class-Assignments/CS5002_Assignment6_BartoszKawalkowski.pdf)
- [Harshil Patel Initial Assessment](https://github.com/Harshilp20/Senior-Design/blob/main/Class-Assignments/Assignment3_patel3hs.pdf)
- [Harshil Patel Final Assessment](https://github.com/Harshilp20/Senior-Design/blob/main/Class-Assignments/CS5002_Assignment6_HarshilPatel.pdf)

# Summary of Hours and Justification

### Harshil Patel

- Fall Semester Hours: 45 hrs
- Spring Semester Hours: 90 hrs
- Total Hours: 135 hrs

Justification:

Throughout the year, I worked extensively on designing and implementing major components of the Windows Process Protector. My efforts were focused on the memory protection module, code integrity checks, behavior analysis, and network monitoring subsystems. I led the development of the web interface and took charge of real-time dashboard features. I also handled testing for all subsystems and ensured the system performed reliably under real-world scenarios. I contributed equally to documentation and presentations, including the Final Report and Expo preparation. Tasks were verified through meeting notes and development logs in our GitHub repository.

### Bartosz Kawalkowski

- Fall Semester Hours: 45 hrs
- Spring Semester Hours: 100 hrs
- Total Hours: 145 hrs

Justification:

Over the course of the project, I led the system architecture design and core development of memory protection and code integrity verification modules. I performed in-depth research on Windows kernel security and anti-cheat strategies. I also developed much of the backend logic for the behavior and network monitoring subsystems. I was heavily involved in writing the technical specification and documentation. I contributed equally to design reviews, testing strategy, and final deliverables including the Final Design Report and Expo presentation.

[Meeting Notes and Logs](https://github.com/Harshilp20/Senior-Design/blob/main/WindowsProcessProtector_MeetingNotes.pdf)

### Total Hours on Project: 280 Hours

- [Task List](https://github.com/Harshilp20/Senior-Design/blob/main/TaskList.md)
- [Timeline](https://github.com/Harshilp20/Senior-Design/blob/main/Assignment6Timeline.csv)
- [Effort Matrix](https://github.com/Harshilp20/Senior-Design/blob/main/Assignment6EffortMatrix.csv)

# Professional Biographies

- [Bartosz Kawalkowski Biography](https://github.com/Harshilp20/Senior-Design/blob/main/Bartosz_Kawalkowski_Biography.md)
- [Harshil Patel Biography](https://github.com/Harshilp20/Senior-Design/blob/main/Harshil_Patel_Biography.md)

# Expenses

- There have not been any expenses for this project up to this date. We have utilized our own equipment and open source tools.
- We have used the following tools:
  - Visual Studio 2022 (Personal License)
  - GitHub (Used for CI/CD tools, also free)
  - We used our personal machines for development as well

# Appendix

- All meeting notes and time spent has been documented, access these notes [here](https://github.com/Harshilp20/Senior-Design/blob/main/WindowsProcessProtector_MeetingNotes.pdf)
- A summary of the research conducted for this assignment can be found [here](https://github.com/Harshilp20/Senior-Design/blob/main/WindowsProcessProtector_ResearchDocument.pdf)
- Our current source code for the Windows Process Protector w/ Interactive Web-based Monitoring can be found on GitHub [here](https://github.com/BartoszK002/WPP)

