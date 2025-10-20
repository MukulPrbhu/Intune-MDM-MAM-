# LAB 10: Deploy Microsoft 365 apps to devices, set Open file format and current channel update

In this lab, we deploy the **Microsoft 365 Apps suite** through Intune to ensure that all Windows devices in the New York group have the latest Office applications installed and configured consistently. The policy specifies the **Current Channel** for updates so users receive new features and security fixes as soon as they’re released. Additionally, we set the **default file format** to Office Open XML (e.g., .docx, .xlsx, .pptx) to maintain compatibility and standardization across the organization. This configuration helps automate app deployment, streamline updates, and enforce consistent Office settings across all managed devices.


## **Step 1 – Add the Microsoft 365 Apps Suite**

- Go to **endpoint.microsoft.com → Apps → Windows apps → Add**.
- **App type**: **Microsoft 365 Apps for Windows 10 and later** → **Select**.
- **Name**: e.g., `NY – Microsoft 365 Apps (Current Channel + Default File Format)`.
- **Publisher**: Microsoft | **Category**: Productivity | **Show as featured app**: ✅ (optional).
- **Next**.

---

## **Step 2 – Configure App Suite (Core Settings)**

- **Update channel**: **Current Channel** (gets features as soon as they’re ready).
- **Version**: Latest (or specify if you require a fixed build).
- **Architecture**: 64-bit (recommended unless you have 32-bit dependencies).
- **Languages**: **English** (add more if needed).
- **Exclude apps**: leave default or deselect any apps you don’t want (e.g., Access/Publisher).
- **Shared computer activation**: Off (enable if using pooled devices like RDS/VDI).
- **Next**.

---

## **Step 3 – Set the Default Open File Format (Application Preferences)**

- **Configuration settings format**: **Configuration designer**.
- Expand **Application preferences** → **Microsoft Office** (and individual apps if needed).
- **Default file format**: set to **Office Open XML** (DOCX/XLSX/PPTX).
    - *(If your standard is OpenDocument, choose **OpenDocument Format** instead—apply per app if the global toggle isn’t available.)*
- (Optional) Apply per-app overrides:
    - **Word** → Default save format = Office Open XML (.docx)
    - **Excel** → Default save format = Office Open XML (.xlsx)
    - **PowerPoint** → Default save format = Office Open XML (.pptx)
- **Next**.

---

## **Step 4 – Assignments**

- **Assignments → Add group(s)** → select **New York Users and Devices**.
- (Optional) Add **availability** = Required (auto-install) or Available (Company Portal).
- **Next**.

---

## **Step 5 – Review + Create**

- Review summary: Update channel = **Current Channel**, language = **English**, default file format = **Office Open XML** (or your chosen standard).
- Click **Create** to deploy.
