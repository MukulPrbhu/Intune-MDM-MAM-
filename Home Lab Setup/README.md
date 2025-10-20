# Hyper-V & Windows 11 Lab

I built a nested Hyper‑V lab on an Azure VM (E4s_v6) to run Windows Server 2022 (AD/DNS) and Windows 11 clients. Along the way I solved nested virtualization availability, Windows 11 installer blocks (TPM/Secure Boot), OOBE internet/MSA requirements, and unstable networking caused by Azure public IP churn. This repo/page documents the steps, commands, and troubleshooting notes so the setup is reproducible.

## Goals

- Run Hyper‑V inside an Azure VM for lab purposes (Active Directory, DNS, client VMs).
- Install Windows 11 in a VM (support or bypass TPM/Secure Boot checks as needed).
- Provide stable internal DNS & NAT for VMs so Azure public IP changes don’t break resolution.
- Keep a concise checklist so the environment can be rebuilt quickly.

---

## Quick architecture (recommended)

- **Azure host (nested Hyper‑V)**: Azure VM in West US, Availability Zone 3, SKU: `E4s_v6` (supports nested virtualization)
- **Hyper‑V host**: runs an internal NAT switch `MyNAT` (192.168.100.0/24) with host IP `192.168.100.1`
- **Windows Server VM**: `192.168.100.2` — DNS (forwarders configured to 8.8.8.8 / 1.1.1.1), optionally DHCP
- **Windows 11 VMs**: DHCP/static clients pointing DNS to `192.168.100.2`

## Important decisions / notes

- Use **Availability Zone 3** in West US and choose `Standard security` when launching the Azure VM to expose CPU SKUs compatible with nested Hyper‑V. E.g., `E4s_v6`.
- Prefer **Gen‑2 + vTPM + Secure Boot** for supported Windows 11 installs. If host/hypervisor prevents vTPM, use the documented installer bypass (registry or offline SYSTEM hive) for lab/testing only.
- Avoid the **Default Switch** for long‑running labs — create a dedicated NAT switch with a fixed subnet.

# from OOBE network screen (Shift+F10)
OOBE\BYPASSNRO
# from WinPE or installer environment (Shift+F10)
reg add "HKLM\SYSTEM\Setup\LabConfig" /f

reg add "HKLM\SYSTEM\Setup\LabConfig" /v BypassTPMCheck /t REG_DWORD /d 1 /f

reg add "HKLM\SYSTEM\Setup\LabConfig" /v BypassSecureBootCheck /t REG_DWORD /d 1 /f

reg add "HKLM\SYSTEM\Setup\LabConfig" /v BypassRAMCheck /t REG_DWORD /d 1 /f

reg add "HKLM\SYSTEM\Setup\LabConfig" /v BypassCPUCheck /t REG_DWORD /d 1 /f

