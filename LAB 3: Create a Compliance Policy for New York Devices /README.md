# LAB 3: Create a Compliance Policy for New York Devices

In this lab, we create and deploy a compliance policy in Microsoft Intune to ensure that all Windows devices used by the New York group meet the organization’s baseline security requirements. The policy enforces key protections such as enabling the firewall, antivirus, and antispyware, helping maintain a secure device posture. Once assigned to the target group, Intune automatically evaluates each device’s compliance status and marks any that fail these checks as noncompliant, restricting access until the issues are resolved.

## **Step 1 – Create the Compliance Policy**

---

- Navigate: **Intune admin center → Devices → Compliance policies → Policies → Create**.
- **Platform**: **Windows 10 and later**.
- **Name**: `New York – Windows Compliance`.
- (Optional) **Description**: Brief purpose (e.g., “NY baseline: firewall/AV/AS required”).

---

## **Step 2 – Configure Compliance Settings**

- In **Settings**, configure (as used in lab):
    - **Require firewall** = **On**
    - **Require antivirus** = **On**
    - **Require antispyware** = **On**
- (Optional, explored): BitLocker, Secure Boot, Code Integrity, OS min/max version, **Defender for Endpoint risk level**.

---

## **Step 4 – Define Actions for Noncompliance**

- **Actions for noncompliance** → keep default: **Mark device noncompliant**.
- (Optional) Add actions like **Send email to end user**, **Notify admin**, or **Schedule retire after X days**.

---

## **Step 5 – Assign the Policy**

- **Assignments** → **Include groups** → select **New York Users and Devices**.
- (Optional) **Scope tags**: select NY tag if used.

---

## **Step 6 – Create & Deploy**

- Review summary → **Create**.
- Policy is now active; devices in scope will be evaluated at next check-in.

---

## **Step 7 – Validate Compliance**

- Go to **Devices → Compliance policies → Policies → New York – Windows Compliance**.
- Check **Device status/User status** and **Per-setting status**.
- Pick a NY device → **Device compliance** blade → verify it’s **Compliant** when firewall/AV/AS are on.
[!LAB 3](lab3.png)
