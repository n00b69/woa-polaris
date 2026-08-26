<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Running Windows on the Xiaomi Mix 2s

## Restoring your device with EDL

### Prerequisites
- [Stock fastboot rom](https://xmfirmwareupdater.com/miui/polaris/)

- [EDL tools](https://github.com/n00b69/woa-polaris/releases/download/Files/MiFlashPatched.Better.Free.EDL.for.845.zip)

> [!IMPORTANT]
> Use a MiFlash build that has already been patched to work with Snapdragon 845 devices. The normal Xiaomi MiFlash release may reject the device or require authorization when attempting to flash through EDL.

### Extracting the stock ROM

Download the appropriate **fastboot ROM** for the Mi Mix 2S. It should normally be provided as a `.tgz` archive.

Extract the `.tgz` file, then extract the `.tar` archive inside it.

After extraction, you should have a folder containing an `images` directory. For example:

```text
C:\Users\Pidoraz\Downloads\polaris_global_images_V12.0.3.0.QDGMIXM_20201228.0000.00_10.0_global\images
```

You will need the full path to this `images` folder later.

## Entering EDL mode

There are two ways to enter EDL mode depending on the state of the bootloader.

### Unlocked bootloader

If the bootloader is **unlocked**, the easiest method is to enter EDL directly from fastboot.

1. Power the phone off.
2. Hold **Volume Down + Power** to boot into fastboot mode.
3. Connect the phone to your PC.
4. Open a Command Prompt or PowerShell window.
5. Verify that fastboot detects the phone:

```cmd
fastboot devices
```

6. Enter EDL mode:

```cmd
fastboot oem edl
```

The phone should turn off and appear in Windows as:

```text
Qualcomm HS-USB QDLoader 9008 (COM##)
```

You can now continue with the **Finding the COM## number** section below.

### Locked bootloader

If the bootloader is **locked**, `fastboot oem edl` generally cannot be used.

In that case, EDL must be entered using the **test points** on the motherboard.

Use the following reference image for the Mi Mix 2S test-point location:

[Mi Mix 2S test-point image](https://gsmmafia.com/wp-content/uploads/2019/09/mi-mix-2s-test-point.jpg)

Once the test points are correctly shorted while connecting the phone to USB, Windows should detect:

```text
Qualcomm HS-USB QDLoader 9008 (COM##)
```

Release the test points after the device has entered EDL mode.

## Finding the COM## number

Open **Device Manager** in Windows.

Expand:

**Ports (COM & LPT)**

Look for:

```text
Qualcomm HS-USB QDLoader 9008 (COM##)
```

For example:

```text
Qualcomm HS-USB QDLoader 9008 (COM10)
```

Take note of the COM number.

> [!IMPORTANT]
> If the device appears with a yellow warning triangle, install the Qualcomm EDL drivers before continuing.

## Flashing the stock ROM with MiFlash

1. Launch the **pre-patched MiFlash**.
2. Click **Select**.
3. Select the `images` folder extracted from the stock fastboot ROM.

The selected folder should contain files such as the Qualcomm programmer and the various partition images.

3. Make sure MiFlash detects the phone on the correct COM port.
4. At the bottom of MiFlash, select the desired flash option.

For a normal clean restoration, **clean all** is generally the appropriate option.

> [!WARNING]
> Do not select **clean all and lock** unless you specifically know that the ROM is appropriate for your exact device and region. Relocking the bootloader with an incompatible ROM can result in a device that will not boot normally.

5. Click **Flash**.

MiFlash will send the required programmer and partition images to the phone through EDL. The process may take several minutes.

Wait until MiFlash reports that the operation has completed successfully.

## Rebooting into Android

Once flashing has finished:

1. Disconnect the USB cable.
2. Hold the **Power** button until the phone starts.
3. The first boot may take considerably longer than usual after a full restore.

The phone should now boot into the freshly flashed stock Xiaomi firmware.

## Finished!

Your Xiaomi Mi Mix 2S should now be restored to the stock ROM and ready for further Windows-on-ARM setup.

> [!NOTE]
> If MiFlash fails before actually writing partitions, first check that the phone is still detected as **Qualcomm HS-USB QDLoader 9008**, that the correct `images` directory was selected, and that the EDL drivers are installed correctly.












