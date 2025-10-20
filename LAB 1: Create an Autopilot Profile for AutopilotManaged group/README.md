# LAB 1: Create an Autopilot Profile for AutopilotManaged group

The goal of this lab is to enable **zero/low-touch Windows provisioning** by creating a Windows Autopilot deployment profile and targeting it to a dynamic **AutopilotManaged** device group. When a registered device boots into **OOBE (out-of-box experience)**, it’s automatically recognized by the tenant, **joins Microsoft Entra ID** (or Hybrid), **auto-enrolls into Intune** for management, and receives a standardized first-run experience (naming, admin rights, skipped screens, pre-provisioning). In short, we’re replacing ad-hoc imaging with a **repeatable, compliant, and scalable** setup that onboards devices quickly and consistently with the right policies and apps.

## **Autopilot Deployment Preparation**

- **Device IDs registered** → must link them to a **deployment profile**.
- Requires a **special group** to associate devices with Autopilot.

---

## **Step 1 – Create a Security Group**

- Go to **Endpoint → Groups → Create new group**.
- **Type**: Security group (only type that can contain devices).
- **Membership**: Dynamic device (so new devices auto-join).
- Add query rule → Microsoft provides sample queries (search: *Autopilot dynamic security group*).
- This ensures all devices with registered **device IDs** are included.

---

## **Step 2 – Create Deployment Profile**

- Navigate: **Devices → Enroll devices → Deployment profiles → Create profile**.
- **OS**: Windows only (Windows 10+).
- **Profile options**:
    - **Mode**: User-driven (user participates in setup) or Self-deployment (zero-touch).
    - **Join type**: Azure AD or Hybrid AD.
    - **Terms & privacy**: Show or hide (hiding = IT accepts on behalf of user).
    - **Account options**: Restrict admin rights (recommended: standard user).
    - **Pre-provisioning (White Glove)**: Keep pre-installed apps/configs.
    - **Language/region**: Set defaults.
    - **Device name template**: e.g. `COMP-%RAND:5%` (random unique ID).

---

## **Step 3 – Assign Deployment Profile**

- Assign to the **Autopilot managed group** created earlier.
- Can also use **inclusion/exclusion groups**.
    - Rule: *Excluded groups override included groups*.

---

## **Step 4 – Enable Auto Enrollment**

- Navigate: **Devices → Enroll devices → Automatic enrollment**.
- Ensure **MDM** = All and **MAM** = All.
- Default may be “None” in new Intune tenants → must enable.

---

## **Step 5 – Customize Branding (Optional)**

- Go to **Azure Portal → Azure Active Directory → Company branding**.
- Add logos, colors, background, or sign-in text.
- Example: “Welcome to Exam Lab Practice” during OOBE setup.

---

## **Outcome**

- Devices boot → contact Intune → match device IDs → apply group rules.
- Deployment profile configures **OOBE**, joins Azure AD (or hybrid), installs apps, applies policies, and enforces settings.
