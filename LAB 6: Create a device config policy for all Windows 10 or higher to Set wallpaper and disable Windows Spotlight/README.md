# LAB 6: Create a device config policy for all Windows 10 or higher to Set wallpaper and disable Windows Spotlight

In this lab, we create a device configuration policy in Intune to manage desktop personalization across all Windows 10 and later devices. The policy sets a standardized wallpaper using a specific image URL to ensure a consistent visual identity across the organization, while also disabling Windows Spotlight to minimize distractions and potential privacy concerns. By assigning the policy to all Windows devices, administrators can enforce a uniform desktop experience and maintain better control over device appearance and usability.

## **Step 1 – Create the Device Configuration Policy**

- Navigate: **Devices → Configuration → Create → New policy**.
- **Platform**: **Windows 10 and later**.
- **Profile type**: **Device restrictions** → **Create**.
- **Name**: e.g., `All Windows – Set Wallpaper & Block Spotlight`.

---

## **Step 2 – Configure Personalization**

- In **Configuration settings** → **Personalization**.
- From the dropdown **Desktop background picture URL** → enter a **valid, reachable URL** to the image (e.g., HTTPS link or internal CDN).
- (Ensure devices/users have **read access** to the file location.)

---

## **Step 3 – Disable Windows Spotlight**

- Still under **Personalization** → **Windows Spotlight**.
- Set **Block Windows Spotlight** = **On** (toggle to block).

---

## **Step 4 – Assignments**

- **Assignments** → **Add groups** → select **All devices** (or your Windows device group).
- (Optional) Add **filters** to target only Windows 10/11.

---

## **Step 5 – Review + Create**

- **Review** settings → **Create** to publish the profile.
