# Retroid Pocket Mini / 5 - Qualcomm Flash Image Loader (QFIL) Recovery Guide

## ⚠️ WARNING

**Proceed at your own risk!** This process is intended for advanced users only. I take no responsibility for any issues, malfunctions, or damage that may occur to your device as a result of following this guide. Flashing firmware and modifying system files can be risky, and if done incorrectly, may lead to further software or hardware issues. 

By following this guide, you also acknowledge that this process will **void any warranty** you have with Retroid. Make sure to back up your data before proceeding, as this process may result in data loss.

This guide will walk you through using the Qualcomm Flash Image Loader (QFIL) Tool and the QFILHelper tool to recover your Retroid Pocket Mini / 5, a Snapdragon 865 device, from a software brick.

## Included Files:

Download the relevant files for your device from releases: https://github.com/TheGammaSqueeze/Retroid_Pocket_Stock_Firmware/releases

You will need 7-Zip to decompress the split package. Download all parts, then extract either Android10_RPMini_V1.0.0.310_20240926_181623_user.7z.001 for RP MINI or Android13_RP5_V1.0.0.31_20241026_190102_user.7z.001 for RP5 using 7-Zip.

The extracted folder will contain:
- `flash/`: Firmware files for flashing
- `prog_ufs_firehose_sm8250_lite_lp5.elf`: Firehose programmer file for communication with the Retroid Pocket Mini in Emergency Download (EDL) mode.
- `QFILHelper.exe`: Script to execute the flashing process.
- `qpst.win.2.7_installer_00495.1.zip`: QFIL tools and dependencies installer.
- `Qualcomm_USB_Driver_v1.0.10061.1.zip`: Qualcomm USB drivers.

## Step-by-Step Instructions:

### Video guide (skips Drivers and QPST install, works on both RP Mini and RP 5): 
[![Retroid Pocket Mini - Restoring the stock firmware - QFIL flashing guide](https://github.com/user-attachments/assets/76368fe6-9c53-4ae0-83f7-5a49cbb860c6)](https://www.youtube.com/watch?v=Qlpwn4KPZr0 "Retroid Pocket Mini - Restoring the stock firmware - QFIL flashing guide")

### 1. Install Qualcomm USB Drivers
Extract and install `Qualcomm_USB_Driver_v1.0.10061.1.zip`.  
Follow the install instructions available at: [Qualcomm Driver Installation](https://qcomdriver.com/install-qualcomm-usb-driver)

### 2. Install QPST (Qualcomm Product Support Tools)
Extract `qpst.win.2.7_installer_00495.1.zip`.  
Run the `QPST.2.7.495.1.exe` installer to install the tools, which includes the QFIL application.

### 3. Open QFIL Application
After installing QPST, launch the QFIL application from the Start Menu.  
In QFIL, choose the **Flat Build** option.  
Set the Programmer Path to the file in the extracted firmware package:  
`prog_ufs_firehose_sm8250_lite_lp5.elf`.  
At the bottom right of the QFIL window, change the **Storage Type** to **UFS**.

### 4. Enter EDL Mode on the Retroid Pocket Mini / 5
Connect your Retroid Pocket Mini / 5 via the USB cable.  
Press and hold the **Power + Volume Down + Volume Up** buttons simultaneously until the device enters EDL Mode.  
You will know the device is in EDL mode when QFIL shows **"Please Select an Existing Port"** at the top.

### 5. Select the Qualcomm HS-USB QDLoader Port
In QFIL, click the **Select Port** button.  
Choose **Qualcomm HS-USB QDLoader 9008** from the list.

### 6. Open Partition Manager in QFIL
Go to the **Tools** menu in QFIL and select **Partition Manager**.  
Click **OK** on the programmer confirmation popup.  
Wait a few seconds for the partition list to load, then leave QFIL running.  
**Do not modify any partitions here.**

### 7. Run QFILHelper for Flashing
Open the `QFILHelper.exe` application from the package.  
A terminal window will appear. Choose option **"5 - Flash files (from Flash folder)"**.

You'll first be asked to confirm if you want to flash the GPT headers:

```txt
WARNING: You're about to flash GPT headers:

lun0_gpt_header.bin, lun1_gpt_header.bin, lun2_gpt_header.bin, 
lun3_gpt_header.bin, lun4_gpt_header.bin, lun5_gpt_header.bin, lun6_gpt_header.bin

C - Continue | A - Abort
```
**Choose option C.**

You'll then be asked again to confirm if you want to flash the firmware files:

```txt
WARNING: You're about to flash these files:

lun0_frp.bin, lun0_keystore.bin, lun0_metadata.bin, lun0_misc.bin, 
lun0_nvdata1.bin, lun0_nvdata2.bin, lun0_persist.bin, lun0_qpdata1.bin, 
lun0_qpdata2.bin, lun0_rawdump.bin, lun0_reserve1.bin, lun0_reserve2.bin, 
lun0_ssd.bin, lun0_super.bin, lun0_vbmeta_system_a.bin, lun0_vbmeta_system_b.bin, 
lun1_last_parti.bin, lun1_xbl_a.bin, lun1_xbl_config_a.bin, lun2_last_parti.bin, 
lun2_xbl_b.bin, lun2_xbl_config_b.bin, lun3_align_to_128k_1.bin, lun3_cdt.bin, 
lun3_ddr.bin, lun3_last_parti.bin, lun3_mdmddr.bin, lun4_abl_a.bin, lun4_abl_b.bin, 
lun4_aop_a.bin, lun4_aop_b.bin, lun4_apdp.bin, lun4_bluetooth_a.bin, 
lun4_bluetooth_b.bin, lun4_boot_a.bin, lun4_boot_b.bin, lun4_cmnlib64_a.bin, 
lun4_cmnlib64_b.bin, lun4_cmnlib_a.bin, lun4_cmnlib_b.bin, lun4_devcfg_a.bin, 
lun4_devcfg_b.bin, lun4_devinfo.bin, lun4_dip.bin, lun4_dsp_a.bin, lun4_dsp_b.bin, 
lun4_dtbo_a.bin, lun4_dtbo_b.bin, lun4_featenabler_a.bin, lun4_featenabler_b.bin, 
lun4_hyp_a.bin, lun4_hyp_b.bin, lun4_imagefv_a.bin, lun4_imagefv_b.bin, 
lun4_keymaster_a.bin, lun4_keymaster_b.bin, lun4_last_parti.bin, 
lun4_limits-cdsp.bin, lun4_limits.bin, lun4_loader_a.bin, lun4_loader_b.bin, 
lun4_logdump.bin, lun4_logfs.bin, lun4_mdtpsecapp_a.bin, lun4_mdtpsecapp_b.bin, 
lun4_mdtp_a.bin, lun4_mdtp_b.bin, lun4_modem_a.bin, lun4_modem_b.bin, lun4_msadp.bin, 
lun4_multiimgoem_a.bin, lun4_multiimgoem_b.bin, lun4_multiimgqti_a.bin, 
lun4_multiimgqti_b.bin, lun4_qupfw_a.bin, lun4_qupfw_b.bin, lun4_recovery_a.bin, 
lun4_recovery_b.bin, lun4_secdata.bin, lun4_splash.bin, lun4_spunvm.bin, 
lun4_storsec.bin, lun4_tz_a.bin, lun4_tz_b.bin, lun4_uefisecapp_a.bin, 
lun4_uefisecapp_b.bin, lun4_uefivarstore.bin, lun4_vbmeta_a.bin, lun4_vbmeta_b.bin, 
lun4_vm-data.bin, lun4_vm-keystore.bin, lun4_vm-linux_a.bin, lun4_vm-linux_b.bin, 
lun4_vm-system_a.bin, lun4_vm-system_b.bin, lun5_align_to_128k_2.bin, lun5_fsc.bin, 
lun5_fsg.bin, lun5_last_parti.bin, lun5_mdm1m9kefs1.bin, lun5_mdm1m9kefs2.bin, 
lun5_mdm1m9kefs3.bin, lun5_mdm1m9kefsc.bin, lun5_modemst1.bin, lun5_modemst2.bin

C - Continue | A - Abort
```

**Once again, choose C.**

The overall flashing process will begin and may take up to 20 minutes.
Ignore any errors during the flashing until the process completes, at which point a success message will confirm the firmware flash:

```txt
Process completed successfully...
Press any key to return to the menu
```

### 8. Reboot and Factory Reset
Disconnect the USB cable.
Hold the **Power** button for up to 60 seconds until the Retroid logo appears.
The device will boot into Android Recovery. Use the **Volume** buttons to select Factory Data Reset, and press the **Power** button to confirm.
After the reset, the device will reboot into the newly flashed firmware.

You may close all applications after this is complete.
