# LAB 11: Create an app protection policy for NY iOS devices

In this lab, we create an **App Protection Policy (MAM)** in Intune for iOS/iPadOS devices used by the New York group. The goal is to protect organizational data within managed Microsoft apps—such as Outlook, Teams, and OneDrive—without requiring full device management. The policy targets only **managed apps on enrolled devices**, preventing data leakage by restricting copy/paste, save, or sharing actions to secure locations. This ensures that even on mobile platforms, company data remains protected and accessible only through compliant, policy-enforced applications.

## **Step 1 – Start an iOS/iPadOS App Protection Policy (MAM)**

- Navigate: **Apps → App protection policies → Create policy**.
- **Platform**: **iOS/iPadOS**.
- **Name**: e.g., `NY – iOS/iPadOS App Protection (Managed, MS Apps)`.

---

## **Step 2 – App Targeting**

- **Apps** tab:
    - **Target to apps on all device types** = **No** (i.e., do **not** target unmanaged devices).
    - **Target policy** = **Managed apps**.
    - **Targeted apps** = **All Microsoft apps**.

> This scopes the MAM policy to managed Microsoft apps on enrolled iOS/iPadOS devices only.
> 

---

## **Step 3 – (Optional) Data/Access Controls**

- (Leave defaults for the lab, or later tighten):
    - **Data protection** (e.g., restrict cut/copy/save to managed locations).
    - **Access requirements** (PIN/biometrics).
    - **Conditional launch** (wipe on jailbreak, min app version, etc.).

---

## **Step 4 – Assignments**

- **Assignments → Add groups** → select **New York Users and Devices**.
- (Optional) Use **include/exclude** groups for pilots or exceptions.

---

## **Step 5 – Review + Create**

- **Review** the summary → **Create** the policy.
