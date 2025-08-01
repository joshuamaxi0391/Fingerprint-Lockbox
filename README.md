# ESP32-CAM Fingerprint Lockbox

This project implements a secure fingerprint-activated lockbox using an **ESP32-CAM**, a **FlashTree FPM11A** fingerprint sensor, and a **solenoid lock**. Unauthorized access attempts are captured using the onboard camera and stored on an SD card with accurate timestamps synchronized via NTP.

## Features

- Unlock via fingerprint recognition
- Fingerprint re-enrollment with secure authorization
- Takes a photo on failed access attempts
- Photo filenames include real-time timestamps
- Stores photos on SD card
- Safe SD dismount through long-press button action
- Solenoid-controlled physical locking mechanism
- Built-in flash LED for clear image capture

------------------------------------------------------------------------------------

## 🧩 Components Used

| Components              | Details                         |
|------------------------|----------------------------------|
| Microcontroller        | ESP32-CAM (AI-Thinker module)    |
| Fingerprint Sensor     | FlashTree FPM11A (UART 6-pin)    |
| Lock                   | 12V Solenoid Lock                |
| Storage                | MicroSD Card (FAT32, SPI 1-bit)  |
| Power Supply           | 5V/12V regulated + buck converter|
| Flash                  | GPIO 4 LED control               |
| Re-enroll Button       | Connected to GPIO 13 (pull-up)   |

------------------------------------------------------------------------------------

## 🗂️ File Structure

| File/Folder        | Description                                     |
|--------------------|-------------------------------------------------|
| `ESP32-CAM_Lockbox.ino`       | Main Arduino sketch for fingerprint and camera logic |
| `3D Print Files/`             | 3D-printable files for lockbox enclosure |
| `Lockbox Cutouts/`            | Adobe Illustrator files for laser cutting |

------------------------------------------------------------------------------------

## 📹 Demo Video

A short video demonstration of the project is available on YouTube.  
🔗 **[Watch the demo (Unlisted)](https://youtube.com/shorts/HpiAbvv0W3Y)**

> Note: The video is unlisted and intended for instructors, reviewers, or collaborators with the link.

------------------------------------------------------------------------------------

## 🔧 How It Works

1. **Startup**:
   - Initializes camera, SD card (1-bit mode), fingerprint sensor, and Wi-Fi.
   - If no fingerprint is registered, automatically prompts for enrollment.

2. **Normal Use**:
   - Waits for fingerprint input.
   - Unlocks the solenoid lock on a successful match.
   - Captures and timestamps a photo on failed access.

3. **Re-Enrollment**:
   - Press the physical button (GPIO 13).
   - Authenticate with the current fingerprint to allow safe re-enrollment.

4. **Safe SD Removal**:
   - Hold the button for 3+ seconds.
   - The SD card unmounts safely (like ejecting on a PC).
   - Ready for safe power-off or physical card removal.
