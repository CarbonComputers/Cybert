## **Installing Other Operating Systems on the Cybert**

The Cybert supports many operating systems designed for the Raspberry Pi 5 series. However, keep in mind that the Raspberry Pi 5 (BCM2712) is still a relatively new platform, so some OS builds—such as Kali—may not yet offer complete support.

On this page, you’ll find OS-specific folders with instructions on installing the display driver for this screen.
If you want to try an operating system *not* listed, you can follow the general method below.

---

## **General Installation Method**

### **Step 1:**

Download the following files from this page:

* `vc4-kms-dpi-hyperpixel4sq.dtbo`
* `hyperpixel4.dtbo`

### **Step 2:**

Copy both files into the `/overlays/` directory of the OS image.

### **Step 3:**

Add the following lines to `/boot/config.txt`:

```
dtoverlay=vc4-kms-v3d
dtoverlay=vc4-kms-dpi-hyperpixel4sq
```

This installs and activates the display driver.
As long as the OS has basic Pi 5 support, the screen should function correctly.

---

## **Important Note About GPIO Conflicts**

The display uses the default hardware I²C and SPI pins.
Make sure to **disable any OS features or services** that attempt to use those GPIOs to avoid conflicts.

---

## **Fixing Shifted Pixels on the First Column**

Some users may notice a pixel shift on the first column of the display.

To fix this:

### **Step 1:**

Download the file:

* `cybert.dtbo`

### **Step 2:**

Copy it into the `/overlays/` directory of the OS image.

### **Step 3:**

Remove the previous overlay line:

```
dtoverlay=vc4-kms-dpi-hyperpixel4sq
```

Then add:

```
dtoverlay=cybert
```

This will correct the shifted pixel issue.