# Module 10: Enterprise Microsoft Defender for Endpoint (EDR) & ASR Hardening Lab

**Tenant:** `ApexModernWork.onmicrosoft.com`  
**Architect:** Varun Mahajan (`varun25293`)  
**Focus Areas:** Microsoft Defender for Endpoint / Defender for Business Zero-Touch Onboarding, Intune Attack Surface Reduction (ASR) Hardening Policies, and Live EDR Process-Tree Alert Investigation.

---

## Architecture & Endpoint Defense Flow

```text
Windows 11 Endpoint (TESTUSER-1 / AzureAD\PilotUser1)
        │
        ▼
┌───────────────────────────────────────────────────────────────────┐
│ Layer 1: Zero-Touch MDE Onboarding & Sensor Telemetry             │
│ • Connector: Intune-to-Defender Auto-Onboarding (All Devices)     │
│ • Endpoint: TESTUSER-1 (Windows 11 26H2, 10.19.23.212, AAD Joined)│
│ • Status: Onboarding Status = Onboarded | Sensor Health = Active  │
└───────────────────────────────────────────────────────────────────┘
        │
        ▼
┌───────────────────────────────────────────────────────────────────┐
│ Layer 2: Attack Surface Reduction (ASR) Hardening (Intune)        │
│ • Policy: Apex Corporate ASR Hardening Policy (All Devices)       │
│ • Enforced (Block): LSASS Credential Theft, Office Child/Exec     │
│   Processes, Email/Webmail Executables, & Obfuscated Scripts      │
└───────────────────────────────────────────────────────────────────┘
        │
        ▼
┌───────────────────────────────────────────────────────────────────┐
│ Layer 3: Real-Time EDR Detection & Process-Tree Forensics         │
│ • Alert: 'EICAR_Test_File' malware was prevented                  │
│ • Process Tree: userinit.exe → explorer.exe → powershell.exe      │
│ • Verdict & Status: Malicious | Prevented (Client.Heuristic)      │
└───────────────────────────────────────────────────────────────────┘
