# LAB 7: Create an Android config profile that blocks Screen Capture and Camera use but allows USB Storage

In this lab, we create an Android device configuration profile in Intune to enforce security and privacy controls on corporate devices. The policy blocks both screen capture and camera usage to prevent unauthorized data sharing or image capture, while still allowing USB storage access for legitimate file transfers. By applying these restrictions to managed Android devices, organizations can balance security with usability, protecting sensitive information without disrupting productivity.

### **Step 1 – Create the Android Enterprise Policy**

- Navigate: **Devices → Configuration profiles → Create profile**.
- **Platform**: **Android Enterprise**.
- **Profile type**: **Device restrictions** → **Create**.
- **Name**: e.g., `Android – Block Screen Capture & Camera, Allow USB Storage`.
- (If prompted) pick the correct **enrollment scenario** (Work profile / Fully managed / COPE) to match your devices.

---

## **Step 2 – Configure Restrictions**

- In **Configuration settings**, open **General**.
- **Screen capture** = **Block**.
- **Camera** = **Block**.
- **USB storage** = **Allow**.

---

## **Step 3 – Assignments**

- **Assignments** → **Add groups** → select the appropriate Android device/user group(s).
- (Optional) Add **filters** if you need to target specific OS versions or ownership types.

---

## **Step 4 – Review + Create**

- **Review** your settings → **Create** to publish the profile.
