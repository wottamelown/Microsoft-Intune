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

4. <img width="2554" height="1740" alt="image" src="https://github.com/user-attachments/assets/30aaf5a4-1277-4a37-a254-c9c883a8440d" />

