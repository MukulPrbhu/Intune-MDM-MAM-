# LAB 4: Conditional Access Policy

In this lab, we create a Conditional Access policy in Microsoft Entra to protect Microsoft 365 resources by ensuring that only compliant and secure devices can access them. The policy links directly with Intune compliance checks, enforcing conditions such as requiring the device to be marked as compliant or prompting for multifactor authentication when necessary. By first running the policy in report-only mode, we can safely test its impact on pilot users before fully enforcing it, ensuring a smooth rollout and maintaining access for critical accounts like break-glass administrators.

## **Step 1 – Create the Policy**

- Navigate: **Entra admin center → Protection → Conditional Access → Policies → New policy**.
- **Name**: e.g., `CA – NY – Require Compliant Device for M365`.

---

## **Step 2 – Assignments → Users/Groups**

- **Include**: your **pilot group** (e.g., `NY-CA-Pilot`).
- **Exclude**: your **break-glass accounts** (and any emergency admin group).

---

## **Step 3 – Assignments → Target Resources**

- **Cloud apps** → **Select apps** → choose **Microsoft 365 (Office 365)** (or specific apps you want to protect).
- (Leave **User actions/Authentication context** unconfigured unless you need them.)

---

## **Step 4 – Conditions (When to Apply)**

- **Device platforms**: Include **Windows**, **iOS/iPadOS**, **Android**, **macOS** as needed.
- **Client apps**:
    - Include **Browser** and **Mobile apps and desktop clients** (exclude **Legacy auth** if you block it separately).

---

## **Step 5 – Access Controls (Grant/Block)**

- **Grant** → **Require device to be marked as compliant** (ties to your Intune compliance policy).
- (Optionally also require) **MFA** or **Hybrid Azure AD join** depending on your standard.
- Ensure **Require all selected controls** is chosen if you stack requirements.

---

## **Step 6 – Enablement Mode**

- Set policy to **Report-only** first.
- **Create** the policy.

---

## **Step 7 – Validate**

- Go to **Entra → Monitoring → Sign-in logs**.
- Add column **Report-only (Result)** to see “what would have happened.”
- Test with **pilot users** from varied devices/locations; confirm desired **Grant** result and no unexpected blocks.

---

## **Step 8 – Go Live**

- Edit the policy → switch **Enable policy: On**.
- Keep **exclusions** for break-glass accounts.
- Communicate change window and user guidance (e.g., how to remediate noncompliance).
