# LAB 9: Create a security baseline for NY devices

In this lab, we deploy a **Microsoft Security Baseline** in Intune for the New York devices group to enforce standardized security configurations. Security baselines provide preconfigured best-practice settings recommended by Microsoft, helping ensure consistent protection across all managed devices. In this exercise, we customize the baseline by increasing the minimum password length to strengthen account security and then assign it to the New York group, ensuring all targeted devices comply with the updated security standard.

## **Step 1 – Choose the Right Baseline Version**

- Navigate: **Endpoint.microsoft.com → Endpoint security → Security baselines**.
- Open **Security Baseline for Windows 10 and later** → **Create profile**.
- **Version**: pick the **latest** available (recommended).
- **Name**: e.g., `NY – Security Baseline – Min Password Length 10`.

---

## **Step 2 – Configure Device Lock (Password Settings)**

- In the baseline settings, expand **Device lock**.
- Set **Minimum password length** = **12.**
- **Next** to continue.

---

## **Step 3 – Assignments**

- **Assignments → Add groups** → select **New York Users and Devices**.
- **Next**.

---

## **Step 4 – Review + Create**

- Review summary → **Create** to deploy the baseline.
