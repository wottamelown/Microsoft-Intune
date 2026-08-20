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
7. iOS devices are enrolled through portal only.
8. Android devices are controlled throuhg "intune company portal application on GooglePlayStore".

-- Device Configuration Profiles --
1. Configuration profiles are enforced device behavior. Like blocking USBs.
2. Settings catalog (modern+recommended) deepest wildest configuration coverage. Searchable and flexible.
3. Templates (Pre-Grouped): these are pre-built can be faster to deploy.
4. Properties catalog: collects device inventory, hHW, Does not enforce settings.
5. Policy status shows the policy has been under success, pending or Error/conflict.
6. Endpoint validation checks for check-in status, local behavior, event logs.

7. We have created the Base windows hardening policy through settings catalogue.

<img width="2810" height="1750" alt="image" src="https://github.com/user-attachments/assets/6996b7ee-66cb-42f0-8e62-3986035f7756" />

------Policy for Wifi enforcement-------

<img width="2846" height="1750" alt="image" src="https://github.com/user-attachments/assets/bb7a2068-d651-4be5-8b05-420b6484e2c2" />
<img width="2846" height="1750" alt="image" src="https://github.com/user-attachments/assets/eb7f64a4-7ad3-4e51-8959-c89fbf3bf2d9" />
<img width="2846" height="1750" alt="image" src="https://github.com/user-attachments/assets/eb5c3eb2-dd71-4eff-9c3c-295633968658" />

-- Creating the Device USB & Camera restriction policy --

1. We will use templates instead of settings catalog. Because blocking USB is quite common. Available in templates menu.

<img width="2846" height="1750" alt="image" src="https://github.com/user-attachments/assets/6da7814c-163d-4c83-81a1-bce8302050d1" />

<img width="2846" height="1750" alt="image" src="https://github.com/user-attachments/assets/c730127f-7ae2-42e7-ac0d-a996e96c7efd" />

<img width="2846" height="1750" alt="image" src="https://github.com/user-attachments/assets/7eb13b9b-94da-4715-8b6f-abc3384f3a70" />

-- Device Compliance & Conditional Access --

1. Device Compliance comes as if the device is compliant or not.
2. If the device is non-compliant, then some of the restrictions would be placed on the device.
3. These restrictions are called Conditional Access policies.

-- Security baselines --

1. Security Baselines are the Microsoft Recommended security policies or templates we can say to be pushed towards the devices in bulk.
2. But it should not conflict with the device configuration profiles. 

-- Microsoft Defender For Endpoint --
1. If Entra ID authenticates, intune manages the device. Then the Defender for Endpoint is the complete XDR concept.
2. Defender for endpoint send the live telemetry of the device and the Intune makes decision making according to that.
3. Defender does not only works on the signature based detections like normal antivirus. Instead it observes the pattern and analytics or abnormal behaviors in the OS. i.e. CPU spike.
4. The telemetry could be network, system, antivirus, file events. 
5. When the Defender detects the nomally, it generates the alerts, create timestamps, reduce alert nosie for the analysis.
6. Once Defender detects a nomally it automatically runs AIR (Automated Investigation & Response) fixes the issue without human intervention.
7. It stops malicious processes, does the device isolation, Contains the threats quickly.
8. Defender for Endpoint can stop the lateral movement of the threat, data loss and limits the attack's damage early as possible.
9. The full visibility shows up on the DEFENDER PORTAL under Security.

10. Now for the intune x Defender to work together, we need to enable the Microsoft Intune connection from the Security Portal > Settings > EndPoints > Microsoft Intune Connection.

<img width="2094" height="1296" alt="image" src="https://github.com/user-attachments/assets/c2127d73-95df-44e5-bc10-a82f998d58be" />

11. Now we can see the Intune admin center is also showing the Microsoft Defender status is availabe.

12. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/72716c2d-bb37-4bff-a1f3-49855d339e9f" />

13. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/466969a6-363b-4105-b563-f870484bab49" />

14. Now Here we will configure the EndPoint Configuration Profile using the Pre-Defined EndPoint Security Policy.
15. We can Configure using Pre Defined. However manual deployment can be done as well.

16. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/70b84a6e-a2ae-429b-9478-d4b55fa5716e" />

17. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/9b913c55-28f6-404d-86a7-725af59beff2" />

18. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/b34e71f6-a196-4c89-941e-af537b929e75" />

19. Here we can see the security Threat Score, recommendations, timeline, incidents and alerts.
20. Now we will create a custom detection rule that will work on specified app powershell if the eicar is executed. 

21. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/c6247e15-a685-49d5-9925-e98d59ecc6a4" />

22. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/a4584cca-31c3-4462-83a7-1007954af3ec" />

23. Now we will Isolate the device. 
24.   <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/a2442310-2165-429e-b0b8-219c123a0ca5" />


-- Now We will See Completely ZTNA: Intune + Conditional Access Policies + Defender For End Point + Risk Score In Action --

25. First we will create a compliance policy. Which will mark the device non-compliant.

26. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/7ab597bf-bf48-42a1-ba38-6e5e63783e77" />

27. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/e4f06f87-bbed-4cb8-9f04-2a293d16a262" />

28. Then we will create a confitional access policy: That if the device is marked out of compliance then this policy will trigger.

29. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/ae30eae6-77f1-4e7c-afd4-6bf1e2494e52" />

30. Now we will go to the Advanced Hunting, write the test KQL and setup an alert,

31. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/1c093cac-95df-42e3-90e6-85f26b2c72b2" />

32. <img width="2860" height="1784" alt="image" src="https://github.com/user-attachments/assets/02de2371-d8f6-4e47-9f9a-93f152dba384" />



-- MAM / Application Management with Intune --

33. We can configure intune to remotely push or manage the devices EndPoints.
34. Intune supports win32, MSI, MS Store, .exe & Line Of Business applications.
35. Most softwares are packaged into win32 and installed silently.
36. MAM also known as  application protection polcies. Like what apps are allowed to be used.
37. Supporting BYOD concepts.
38. It is recommended to install the apps for the users from the application MAM deployment package.
39. MDM = Device Control
40. MAM = App & Data Control
41. Works on Managed & Unmanaged devices.
42. MAM examples: Copy/Paste Restrictions, WhatsApp file transfer restriction, Save-as & data leakage protection, app-level encryption. MAM in BYOD scenarios: Work Profile restrictions.
43. There might be a delay installing apps since it is not SCCM-style.

-- Deployment of a Win32 App --

44. We need to create a folder on Admin machine named as 7zip, Tools
45. We need to download, the (( Microsoft-Win32-Content-Prep-Tool ))
46. This tool generates .intunewin file which is used by intune to push the apps.  

47. We will download the setup file just like AZCOPY from github "Microsoft Intune Content Prep Tool".
48. <img width="1810" height="1026" alt="image" src="https://github.com/user-attachments/assets/ebcb7e88-3131-4903-8a78-d1536f9e8c09" />

49. <img width="2658" height="1496" alt="image" src="https://github.com/user-attachments/assets/a6ecbc0c-5856-4787-91ff-44d893b176bd" />

50. <img width="2658" height="1496" alt="image" src="https://github.com/user-attachments/assets/bf0e8e25-354a-4247-9d57-c6c333c55e1c" />

51. <img width="2658" height="1496" alt="image" src="https://github.com/user-attachments/assets/2cb3669d-4d41-466f-872a-d34a852145f7" />

52. <img width="2658" height="1496" alt="image" src="https://github.com/user-attachments/assets/5832e310-ca64-4137-9b91-adea6e717840" />

53. <img width="2658" height="1496" alt="image" src="https://github.com/user-attachments/assets/5c2d016e-4a41-4732-bc11-99d1b21cef57" />

54. <img width="2658" height="1496" alt="image" src="https://github.com/user-attachments/assets/d59e1a39-2331-498d-a966-4b37ec74bb82" />

-- Now we will Deploy Microsoft Store App --

55. <img width="2854" height="1806" alt="image" src="https://github.com/user-attachments/assets/3e448c7c-5c1d-467b-bd55-df54f0c99ad0" />

56. <img width="2854" height="1806" alt="image" src="https://github.com/user-attachments/assets/aae586c3-00d5-49ac-ad5f-391bd92f9ec1" />


-- App Protection Policy (MAM) on iOS/Android --

57. For example: Outlook For Mobile app restriction, setup passcode to it and copy paste will not be allowed, cannot take a screenshot, file can be saved to phone, wipe data.
   
58. <img width="2854" height="1806" alt="image" src="https://github.com/user-attachments/assets/e2706407-b41a-4e72-bb54-93c8b38965b1" />

59. <img width="2854" height="1806" alt="image" src="https://github.com/user-attachments/assets/f507ecae-e0fd-46fc-ba34-569d9b283a5c" />

60. <img width="2854" height="1806" alt="image" src="https://github.com/user-attachments/assets/0909a16b-2115-4bab-8b01-988abc5473d6" />

61. <img width="590" height="1278" alt="IMG_1310" src="https://github.com/user-attachments/assets/c3cb2d3a-bf3e-48a3-bac0-be8109cf74b5" />



== Endpoint Security Hardening (ASR, Firewall, EPM) ===

62. A Attack Surface Reduction (ASR) in Microsoft Intune is a host-defense capability powered by Microsoft Defender Antivirus that blocks risky software behaviors routinely leveraged by malware such as weaponized Office macros, obfuscated scripts, and credential dumping. It blocks malicious behaviours. It enforces secure OS defaults at the OS level. 
63. End Point Privelege Management: Temporary local admin rights exist only when needed. So ASR is reduced.
64. Microsoft Defender Firewall: Built in host based firewall, controls inbound outbound network traffic. Even if the devices are connected to other networks the access is restricted.
65. Defender firewall in 0 Trust: Firewall enforces least privelege networking Works with ASR, Defender, CA.

-- Active Surface Reduction Policy --

66. ASR policy basically prevents the apps to behave maliciously. For example: Child processes blocking.

67. <img width="2856" height="1792" alt="image" src="https://github.com/user-attachments/assets/17b78674-4ada-4b1d-944f-fe5e3a40579b" />

68. <img width="2856" height="1792" alt="image" src="https://github.com/user-attachments/assets/c3e93e70-1f78-4b87-87ce-f361545a69e6" />

69. <img width="2856" height="1792" alt="image" src="https://github.com/user-attachments/assets/98d40859-be81-47b4-8b62-563631c950de" />

70. Firewall Policy: We will allow or block app accordign to the ports, we will enable enforce the firewall across types of network.

71. <img width="2854" height="1802" alt="image" src="https://github.com/user-attachments/assets/76f5ba0d-a551-49bc-a4b7-68d73c9d2f56" />

72. <img width="2854" height="1802" alt="image" src="https://github.com/user-attachments/assets/32a5b6f1-d97e-4914-8945-061f5ed11c03" />

73. <img width="2854" height="1802" alt="image" src="https://github.com/user-attachments/assets/7d880678-5421-43c1-9e91-3a9748b07e4a" />

74. <img width="2854" height="1802" alt="image" src="https://github.com/user-attachments/assets/0b8e5da8-0c5a-4171-95df-0c6fdc459550" />

75. <img width="2854" height="1802" alt="image" src="https://github.com/user-attachments/assets/8176d57b-9fbc-44cc-be04-07c295738472" />





 


 





