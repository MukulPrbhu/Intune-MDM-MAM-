# LAB 5: Restrict user to the number of enrolled devices and Platform type

In this lab, we configure Intune enrollment restrictions to control how many devices each user can enroll and which operating systems are allowed. By setting a device limit (e.g., 15 devices per user), organizations can prevent excessive enrollments that may pose management or licensing issues. Additionally, blocking specific platforms such as macOS helps enforce company policies and ensure that only approved device types can access corporate resources, maintaining a consistent and secure device environment.

## **Step 1 – Allow Up to 15 Devices Per User**

- Navigate: **Devices → Enroll devices → Enrollment device limit restrictions**.
- Open the **Default (All users)** (or your targeted) policy → **Edit properties**.
- **Device limit**: set to **15** → **Review + save**.
- (If you created a custom policy, ensure it’s **above** Default in **Priority**.)

---

## **Step 2 – Block macOS Enrollment for All Users**

- Navigate: **Devices → Enroll devices → Enrollment device platform restrictions**.
- Open the **Default (All users)** (or your targeted) policy → **Edit properties**.
- **Platform settings** → set **macOS = Block** → **Review + save**.
- Confirm this policy is **higher priority** than any exception policy.
