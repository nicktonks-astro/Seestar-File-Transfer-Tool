# NickTonks_Astrophotography Seestar Station Copy & Organiser Tool (v1.3)

A lightweight Windows HTA/Batch utility designed to detect ZWO Seestar devices on your local network (Station Mode or Direct Access) and automatically copy, sort, and organize your astrophotography files using Windows Robocopy.

## Features

- **Dual Connection Modes**: Supports both Home Wi-Fi (Station Mode dynamic IPs) and Direct Access Mode (standard static IP).
- **Automated & Manual Discovery**: Automated subnet scanning via Ping/DNS or manual IP validation for quick targeting.
- **Remembers Your Setup**: Automatically saves your last-used destination folder and any Seestar IP addresses you've connected to, so they're restored and reconnected the next time you launch the tool — no need to re-scan or re-browse every session.
- **Organized Folder Structure**: Automatically categorizes files into subfolders by target name:

  - `[Destination]\[Target Name]\Lights\` (.fit, .fits)
  - `[Destination]\[Target Name]\Video\` (.mp4, .avi)
  - `[Destination]\[Target Name]\JPEGS\` (.jpg, .jpeg)

- **Robocopy Engine**: Fast, incremental transfers that skip existing files and save detailed per-device log files (`Seestar_X.log`).
- **Transfer Controls**: Simple controls to start, pause, and resume ongoing transfer jobs.
- **Automatic Registry Cleanup**: Configures SMB guest authentication settings (`AllowInsecureGuestAuth`) during runtime and offers to revert them to standard Windows defaults upon exit.

## System Requirements & Prerequisites

- **OS**: Windows 10 / 11 (requires Administrator privileges to modify SMB guest auth registry keys).
- **Dependencies**: Microsoft HTML Application (`mshta.exe`), PowerShell, Windows Script Host (`WScript.Shell`), and Robocopy.
- **Network**: PC and Seestar telescope must be on the same Wi-Fi network (Station Mode) or connected directly to the Seestar Wi-Fi hotspot.

## How to Use

1. **Launch the Application**: Run the script file (`.bat` or `.hta`). Accept the Administrator prompt (UAC) to allow registry configuration for SMB access.
2. **Landing Page**: Review connection modes, network scanning options, and the disclosure details, then click **Launch Transfer Tool**.
3. **Discover Devices**:
   - On first launch, click **Run Automatic Scan** to sweep your local network for active Seestar devices, or
   - Click **Add Manual IPs** to directly enter a known IP address (e.g., `192.168.1.150` or `10.0.0.1`).
   - On subsequent launches, any previously connected Seestar IPs are **reconnected automatically** — no scan needed, unless you've added a new device or an IP has changed.
4. **Choose Destination Folder**: Click **Browse...** in Section 3 to choose where your astrophotography files will be saved. This folder is remembered automatically for next time.
5. **Select File Types**: Filter which formats to copy (FITs, Video, Images).
6. **Start Transfer**: Click **Start Transfer**. The app will launch File Explorer to your destination and display real-time logs in the status window.
7. **Exit**: Click **Close and Exit**. Select **Yes** when prompted to revert Windows SMB registry policies back to system defaults.

### Managing Saved Devices

- Every IP added via automatic scan or manual entry is saved locally under `HKCU\Software\NickTonks_Seestar` and reconnected automatically on future launches.
- If a Seestar's IP address changes, or you no longer want a device to reconnect automatically, click **Forget Saved IPs** in Section 1 to clear the saved list, then re-scan or re-add IPs as needed.
- Forgetting saved IPs only clears the *saved memory* — it does not disconnect devices in your current session.

## Network Share Credentials

If Windows prompts for network credentials when accessing the Seestar share (`\\<IP>\EMMC Images`):

- **Username**: `guest`
- **Password**: *(leave blank)*

## Author & Socials

- **Author**: Nick Tonks
- **Instagram**: [@NICKTONKS_ASTROPHOTOGRAPHY](https://instagram.com/NICKTONKS_ASTROPHOTOGRAPHY)