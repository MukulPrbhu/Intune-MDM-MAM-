# LAB 8: Create an update ring policy for Broad Devices

In this lab, we create a Windows Update ring policy in Intune for the **Broad devices group**, which represents the main production environment. The purpose of this policy is to control how and when Windows updates are delivered, ensuring stability and minimizing disruptions. By deferring both quality and feature updates by 30 days, administrators give time for pilot testing before updates reach production users. This structured rollout helps maintain a secure and up-to-date environment while reducing the risk of widespread issues from untested updates.

## **What “Update ring” and “Broad update group” mean**

- **Update ring**: a Windows Update **policy** in Intune that defines *cadence and behavior*—e.g., deferral days for **Quality** (Patch Tuesday) and **Feature** (version upgrades), whether pausing is allowed, deadlines, restart behavior, etc. You assign the ring to devices/users to enforce that update schedule.
- **Broad update group**: the large, production cohort you target **after** pilots prove stable. Typical rollout phases are **Pilot/First** (small test set) → **Broad** (the majority of devices). Your security group (e.g., `WU-Broad-Devices`) contains those production devices and is used in the ring’s **Assignments**.

---

## **Step 1 – Create the Update Ring**

- Navigate: **Devices → Windows → Windows updates → Update rings for Windows 10 and later → Create profile**.
- **Name**: `Broad – Windows Update Ring`.

---

## **Step 2 – Configure Deferrals**

- **Quality update deferral period (days)**: **30**.
- **Feature update deferral period (days)**: **30**.
- *(Deferrals delay when devices see new updates after Microsoft releases them, giving Broad a 30-day buffer.)*

---

## **Step 3 – Configure Pause Behavior**

- **Pause Windows updates**: **Disable**.
- *(If shown separately, set **Pause quality updates** = **Off** and **Pause feature updates** = **Off**.)*

---

## **Step 4 – Assignments**

- **Assignments** → **Add groups** → select **Broad update group**.
- (Optional) Add **filters** if you need to target only certain Windows versions or device attributes.

---

## **Step 5 – Review + Create**

- **Review** configuration → **Create** to publish the update ring.
