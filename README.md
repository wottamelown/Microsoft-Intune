# Microsoft-Intune

--Microsoft Entra ID--
1. Entra ID - Identity Verification
2. Verifies who the user is.
3. Asks: Is this the right user?
4. Performs validation, check, MFA, policies.

-- Microsoft Intune --
1. Intune - device health & posture check.
2. Check encryption, OS patches, Firewall, Posture.
3. Enforces remediation & blocks the non-compliant devices.
4. Asks: Is this device trusted?

-- Microsoft Defender --
1. Defender -- Detection/prevention of attacks, reduce attack surface.
2. Uses MITRE attack-based behavioral analytics.
3. Can isolate compromised devices.
4. Asks: Is this device safe to be used?


-- Zero trust Unified Protection --
1. Entra: Who is the user?
2. Intune: Is the device trusted?
3. Defender: Is the device safe?
4. Together 3 forms a Zero Trust Access.
5. Enables Continous, real-time protection & access control.

-- Supported Devices --
1. Intune support the following devices:
2. Windows 10,11: Full MAM, MDM, compliance, deep configuration, security controls.
3. MacOS: Profiles, compliance, security & app deployment.
4. iOS: Strong app protection & compliance enforcement.
5. Android: Works Profiles, Fully Managed modes.
6. Linux: Basic Compliance & posture controls.
7. VMs: Same as phyiscal, depends on OS.

-- Deployment Of Intune --
1. First we need to create a MS tenant. And connect the domain.
2. Check the E5 license. Once assigned license we will check the intune & Entra ID portals.
3. Configure MDM & WIP enrollment through Entra ID > Mobility.

 <img width="2554" height="1740" alt="image" src="https://github.com/user-attachments/assets/30aaf5a4-1277-4a37-a254-c9c883a8440d" />

4. Here MDM (Mobile Device Management), MAM (Mobile Application Management) & WIP (Windows Information protection) comes in to knowledge. MDM controls the complete hardware, MAM controls the applications, WIP is related Windows security deep enforcements.

-- Creating an Intune Admin User -- 
1. From Admin Center create a user, then assign a intune administrator role.

<img width="2554" height="1740" alt="image" src="https://github.com/user-attachments/assets/cb296cb5-fb54-4245-b4cb-c42913b97dc3" />

-- Enrollment Methods --

1. Entra ID Join (Cloud-First Approach)
2. Hybrid Entra ID Join (On-Prem+Cloud).
3. Workgroup / MDM-Only Enrollment (For BYOD, Contractors, NO fully Device Management).

-- Entra ID Join --
1. This is commmon directly enrollment to intune without the need of On-Prem AD server. The device becomes the cloud identity. Enables Conditional access and compliance.
2. Once the device is enrolled the auto enrollment happens.
3. Pre-Requisites: No Intune license, user excluded from MDM scope, MDM authority no set, Entra ID joined but not intune enabled at all.
4. If the auto-enrollment fails the device gets enrolled in entra ID but not intune.
5. Once the enrollment is done successfully, the intune checks whether the device is healthy to be enrolled, compliance checks, intune checks whether the device is personally owned or corporate owned.

-- Windows Enrollment --
1. We need to have PRO/ENT/EDU editions for Windows 10&11 in order to fully enroll the windows device to the intune.
2. Timezones should be correct, internet connectivity should be established.
3. Once we enrolled through Settings > Work/School Account > Connect.
4. We can check the enollment through dsregcmd /status.

<img width="2810" height="1750" alt="image" src="https://github.com/user-attachments/assets/a32f50e2-0cf5-4d36-bfae-f9384ea20162" />

5. We can change ownership of the device if it appears as personal from Entra ID > Devices > Properties then select corporate. 
6. For Apple devices, we need to conifgure the APNs Apple Push notification certificates. It allows the apple devices to trust the intune to have the visiblity. 


