<!-- <:# :
@echo off
net session >nul 2>&1
if %errorLevel% neq 0 (
    echo Set UAC = CreateObject^("Shell.Application"^) > "%temp%\getadmin.vbs"
    echo UAC.ShellExecute "cmd.exe", "/c """"%~f0""""", "", "runas", 0 >> "%temp%\getadmin.vbs"
    "%temp%\getadmin.vbs"
    del "%temp%\getadmin.vbs"
    exit /b
)

reg add "HKCU\Software\Microsoft\Internet Explorer\Styles" /v MaxScriptStatements /t REG_DWORD /d 0xffffffff /f >nul 2>&1

mshta.exe "%~f0"
exit /b
:# : -->

<!DOCTYPE html>
<html>
<head>
<meta http-equiv="x-ua-compatible" content="ie=edge" />
<title>NickTonks_Astrophotography_Seestar Station Mode File Transfer Tool</title>
<HTA:APPLICATION
    ID="SeestarCopier"
    APPLICATIONNAME="Seestar Station Mode File Transfer Tool"
    BORDER="thin"
    BORDERSTYLE="normal"
    CAPTION="yes"
    MAXIMIZEBUTTON="no"
    MINIMIZEBUTTON="yes"
    SCROLL="yes"
    SINGLEINSTANCE="yes"
    SYSMENU="yes"
/>

<style>
* { box-sizing: border-box; }
html, body { width: 100%; height: 100%; margin: 0; padding: 0; }
body {
    background-color: #070913;
    color: #ffffff;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    padding: 12px;
    font-size: 13px;
    overflow-y: auto;
}
.container { width: 100%; display: block; }
h2 {
    color: #ff9900;
    margin-top: 0;
    margin-bottom: 10px;
    border-bottom: 2px solid #1a2744;
    padding-bottom: 6px;
    text-align: center;
    font-size: 15px;
    letter-spacing: 0.5px;
}
.panel {
    background-color: #0d1221;
    border: 1px solid #1a2744;
    padding: 10px 12px;
    margin-bottom: 8px;
    border-radius: 5px;
    width: 100%;
}
label { display: inline-block; margin-bottom: 4px; color: #ffffff; }
.section-label { color: #ff9900; }
input[type="text"] {
    background-color: #04060a;
    border: 1px solid #1a2744;
    color: #ffffff;
    padding: 6px;
    border-radius: 3px;
    box-sizing: border-box;
}
input[type="text"]:focus {
    border-color: #ffffff;
    outline: none;
}
button {
    background-color: #121d33;
    color: #ffffff;
    border: 1px solid #1a2744;
    padding: 6px 12px;
    cursor: pointer;
    font-weight: bold;
    border-radius: 4px;
    font-size: 12px;
}
button:hover {
    background-color: #1a2b4c;
    border-color: #ffffff;
}
.btn-primary {
    background-color: #00b386;
    color: #ffffff;
    border: none;
    width: 100%;
    font-size: 13px;
    padding: 8px;
}
.btn-primary:hover { background-color: #00cc99; border: none; }

.btn-resume {
    background-color: #2b6cb0;
    color: #ffffff;
    border: none;
    width: 100%;
    font-size: 13px;
    padding: 8px;
}
.btn-resume:hover { background-color: #3182ce; border: none; }

.btn-danger {
    background-color: #a83232;
    color: #ffffff;
    border: none;
    width: 100%;
    font-size: 13px;
    padding: 8px;
}
.btn-danger:hover { background-color: #c73c3c; border: none; }

.btn-exit-custom {
    background-color: #a83232;
    color: #ffffff;
    border: none;
    font-size: 13px;
    padding: 9px;
    width: 240px;
}
.btn-exit-custom:hover { background-color: #c73c3c; border: none; }

.btn-action-group {
    display: flex;
    gap: 6px;
    margin-top: 5px;
}
.btn-action-group button {
    flex: 1;
    padding: 7px;
}

.row-inline {
    display: flex;
    gap: 6px;
    margin-top: 5px;
    align-items: center;
}
.transfer-buttons {
    display: flex;
    gap: 8px;
    margin-top: 5px;
}
.footer-buttons-stacked {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
    margin-top: 14px;
    margin-bottom: 10px;
}
.checkbox-group {
    display: flex;
    justify-content: space-between;
    margin-top: 5px;
    align-items: center;
    width: 100%;
}
.checkbox-group label {
    color: #ffffff;
    cursor: pointer;
    font-weight: normal;
    display: flex;
    align-items: center;
    gap: 6px;
    margin-bottom: 0;
}
input[type="checkbox"] {
    accent-color: #ffffff;
    cursor: pointer;
}
.device-display {
    margin-top: 6px;
    background-color: #04060a;
    border: 1px dashed #1a2744;
    padding: 6px 10px;
    border-radius: 3px;
    font-family: 'Consolas', monospace;
    font-size: 11px;
    color: #ffffff;
    min-height: 38px;
    max-height: 140px;
    overflow-y: auto;
}
.device-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 4px;
    padding: 3px 0;
    border-bottom: 1px solid #121d33;
}
.device-row:last-child {
    border-bottom: none;
}
#scanStatusBox {
    width: 100%;
    background-color: #04060a;
    color: #ffffff;
    font-family: 'Consolas', monospace;
    border: 1px solid #b87728;
    padding: 6px;
    margin-top: 6px;
    font-size: 11px;
    font-weight: bold;
    border-radius: 3px;
    text-align: center;
    display: block;
    box-sizing: border-box;
}
#logArea {
    width: 100%;
    height: 120px;
    background-color: #04060a;
    color: #ffffff;
    font-family: 'Consolas', monospace;
    border: 1px solid #1a2744;
    padding: 6px;
    margin-top: 4px;
    box-sizing: border-box;
    overflow-y: scroll;
    white-space: pre-wrap;
    display: block;
    border-radius: 3px;
}
.note {
    color: #ffffff;
    font-size: 11px;
    text-align: center;
    margin-top: 10px;
    line-height: 1.4;
}
.note span {
    color: #ffffff;
}
#manualBoxContainer {
    display: none;
    margin-top: 8px;
    background-color: #04060a;
    border: 1px solid #ffffff;
    padding: 10px;
    border-radius: 4px;
}

/* ================= SPACIOUS LANDING PAGE STYLES ================= */
#landingScreen {
    display: block;
    text-align: center;
    padding: 10px;
}
.landing-card {
    background-color: #0d1221;
    border: 1px solid #1a2744;
    border-radius: 8px;
    padding: 20px 24px;
    max-width: 700px;
    margin: 0 auto;
    box-shadow: 0 4px 15px rgba(0,0,0,0.5);
}
.landing-title {
    color: #ff9900;
    font-size: 22px;
    font-weight: bold;
    margin-bottom: 2px;
    letter-spacing: 1px;
}
.landing-subtitle {
    color: #00b386;
    font-size: 13px;
    margin-bottom: 16px;
}

/* LANDING PAGE ROW SYSTEM */
.landing-row-section {
    margin-bottom: 14px;
    text-align: left;
}
.landing-row-title {
    color: #ff9900;
    font-size: 11px;
    font-weight: bold;
    letter-spacing: 0.8px;
    text-transform: uppercase;
    margin-bottom: 6px;
    border-bottom: 1px solid #1a2744;
    padding-bottom: 3px;
}
.landing-grid-two-col {
    display: flex;
    gap: 10px;
}
.landing-grid-box {
    flex: 1;
    background-color: #04060a;
    padding: 10px 12px;
    border-radius: 5px;
    border: 1px solid #121d33;
    font-size: 11px;
    line-height: 1.4;
    box-sizing: border-box;
}
.landing-grid-box-full {
    width: 100%;
    background-color: #04060a;
    padding: 10px 12px;
    border-radius: 5px;
    border: 1px solid #121d33;
    font-size: 11px;
    line-height: 1.4;
    box-sizing: border-box;
}
.landing-grid-box h4, .landing-grid-box-full h4 {
    color: #ffffff;
    margin: 0 0 4px 0;
    font-size: 12px;
}
.landing-grid-box p, .landing-grid-box-full p {
    margin: 0;
    color: #cccccc;
}
.folder-tree {
    font-family: 'Consolas', monospace;
    color: #00b386;
    background-color: #070913;
    padding: 6px 10px;
    border-radius: 4px;
    border: 1px solid #121d33;
    margin-top: 6px;
    font-size: 10.5px;
}
.disclosure-box {
    background-color: #04060a;
    border: 1px solid #b87728;
    border-radius: 5px;
    padding: 10px 12px;
    font-size: 11px;
    line-height: 1.4;
    color: #cccccc;
    text-align: left;
    margin-top: 14px;
}
.disclosure-box h4 {
    color: #ff9900;
    margin: 0 0 6px 0;
    font-size: 11.5px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}
.disclosure-box ul {
    margin: 6px 0 0 16px;
    padding: 0;
}
.disclosure-box li {
    margin-bottom: 4px;
}
.btn-enter {
    background-color: #00b386;
    color: #ffffff;
    border: none;
    font-size: 14px;
    padding: 11px 24px;
    border-radius: 5px;
    font-weight: bold;
    cursor: pointer;
    width: 70%;
    margin-top: 14px;
}
.btn-enter:hover {
    background-color: #00cc99;
}
#mainAppContainer {
    display: none;
}
</style>

<script language="JScript">
var wsh = new ActiveXObject("WScript.Shell");
var fso = new ActiveXObject("Scripting.FileSystemObject");
var discoveredIPs = {};
var deviceCount = 0;
var scanTimer = null;
var scanCompleted = false;
var isTransferring = false;

/* ===================== PERSISTED SETTINGS (Registry) ===================== */
var REG_ROOT = "HKCU\\Software\\NickTonks_Seestar\\";

function SaveSetting(name, value) {
    try {
        wsh.RegWrite(REG_ROOT + name, value, "REG_SZ");
    } catch(e) {}
}

function LoadSetting(name, defaultValue) {
    try {
        var v = wsh.RegRead(REG_ROOT + name);
        if (v === undefined || v === null) return defaultValue;
        return v;
    } catch(e) {
        return defaultValue;
    }
}

function GetSavedIPList() {
    var raw = LoadSetting("SavedSeestarIPs", "");
    if (raw === "") return [];
    return raw.split(";");
}

function AddSavedIP(ip) {
    var list = GetSavedIPList();
    for (var i = 0; i < list.length; i++) {
        if (list[i] === ip) return; // already saved
    }
    list.push(ip);
    SaveSetting("SavedSeestarIPs", list.join(";"));
}

function RemoveSavedIP(ip) {
    var list = GetSavedIPList();
    var newList = [];
    for (var i = 0; i < list.length; i++) {
        if (list[i] !== ip) newList.push(list[i]);
    }
    SaveSetting("SavedSeestarIPs", newList.join(";"));
}

function ClearSavedIPs() {
    SaveSetting("SavedSeestarIPs", "");
}
/* =========================================================================== */

window.onload = function() {
    window.resizeTo(760, 930); // Initial size for Landing Page with Disclosure

    // Pre-fill destination folder from last run
    var savedFolder = LoadSetting("LastDestFolder", "");
    if (savedFolder !== "") {
        document.getElementById("destFolderPath").value = savedFolder;
    }
};

function EnterApplication() {
    document.getElementById("landingScreen").style.display = "none";
    document.getElementById("mainAppContainer").style.display = "block";
    window.resizeTo(760, 930); // Resize for full application view

    // Auto-load and reconnect previously saved Seestar IPs
    LoadSavedIPsIntoUI();
}

function LoadSavedIPsIntoUI() {
    var savedIPs = GetSavedIPList();
    if (savedIPs.length === 0) return;

    LogMessage("=================================================");
    LogMessage("[INFO] Reconnecting " + savedIPs.length + " previously saved Seestar IP(s)...");
    LogMessage("=================================================");

    try {
        wsh.Run('reg add "HKLM\\SOFTWARE\\Policies\\Microsoft\\Windows\\LanmanWorkstation" /v AllowInsecureGuestAuth /t REG_DWORD /d 1 /f', 0, true);
        wsh.Run('reg add "HKLM\\SYSTEM\\CurrentControlSet\\Services\\LanmanWorkstation\\Parameters" /v AllowInsecureGuestAuth /t REG_DWORD /d 1 /f', 0, true);
    } catch(e) {}

    var addedBox = document.getElementById("addedIpsDisplay");

    for (var i = 0; i < savedIPs.length; i++) {
        var ip = savedIPs[i].replace(/^\s+|\s+$/g, '');
        if (ip === "" || discoveredIPs[ip]) continue;

        deviceCount++;
        discoveredIPs[ip] = ip;
        ConnectDeviceShare(ip);
        LogMessage("[SAVED] Reconnected Seestar IP: " + ip);

        if (addedBox) {
            addedBox.innerHTML += "<div>" + ip + " (Reconnected)</div>";
        }
    }

    scanCompleted = true;
    UpdateDeviceDisplay();
    UpdateScanStatus("SCAN STATUS: LOADED FROM MEMORY (" + deviceCount + " ACTIVE)");
}

function ForgetSavedDevices() {
    var response = wsh.Popup("Forget all saved Seestar IP addresses?\n\nThis only clears the saved memory - it does not affect the current session's connected devices.", 0, "Forget Saved IPs?", 4 + 32);
    if (response === 6) {
        ClearSavedIPs();
        LogMessage("[INFO] Saved Seestar IP memory has been cleared.");
        alert("Saved IP addresses have been forgotten.");
    }
}

function UpdateScanStatus(msg) {
    document.getElementById("scanStatusBox").innerText = msg;
}

function LogMessage(text) {
    var logBox = document.getElementById("logArea");
    logBox.value += text + "\n";
    logBox.scrollTop = logBox.scrollHeight;
}

function CloseAndExit() {
    try {
        if (scanTimer !== null) {
            window.clearInterval(scanTimer);
        }
    } catch(e) {}

    var promptMessage = "Do you want to revert PC Registry to defaults?\n\n" +
                        "If you have a mapped Network Share to your Seestar, select No.\n\n" +
                        "If you do not have a mapped Network Share, select Yes.\n\n" +
                        "App will close with your preference selected.";

    var response = wsh.Popup(promptMessage, 0, "Revert Settings?", 4 + 32);
    var confirmMessage = "";

    if (response === 6) {
        try {
            wsh.Run('reg add "HKLM\\SOFTWARE\\Policies\\Microsoft\\Windows\\LanmanWorkstation" /v AllowInsecureGuestAuth /t REG_DWORD /d 0 /f', 0, true);
            wsh.Run('reg add "HKLM\\SYSTEM\\CurrentControlSet\\Services\\LanmanWorkstation\\Parameters" /v AllowInsecureGuestAuth /t REG_DWORD /d 0 /f', 0, true);
            confirmMessage = "Registry settings have been reverted to defaults (Insecure Guest Auth disabled).\n\nClick OK to close the application.";
        } catch(e) {
            confirmMessage = "Attempted to revert registry settings, but Administrator privileges were missing.\n\nClick OK to close the application.";
        }
    } else {
        confirmMessage = "Registry settings were kept enabled for mapped network shares.\n\nClick OK to close the application.";
    }

    wsh.Popup(confirmMessage, 0, "Settings Confirmed", 0 + 64);
    window.close();
}

function BrowseDestinationFolder() {
    try {
        var shellApp = new ActiveXObject("Shell.Application");
        var folder = shellApp.BrowseForFolder(0, "Select Destination Folder to Save Files:", 0, 0);
        if (folder != null) {
            var folderItem = folder.Self;
            var path = folderItem.Path;
            document.getElementById("destFolderPath").value = path;
            SaveSetting("LastDestFolder", path);
            LogMessage("[FOLDER] Selected destination path: " + path);
        }
    } catch(e) {
        LogMessage("[ERROR] Could not open folder browser: " + e.message);
    }
}

function hasMatchingFiles(sourceFolderPath, extensionArray) {
    try {
        if (!fso.FolderExists(sourceFolderPath)) return false;
        var folderObj = fso.GetFolder(sourceFolderPath);

        var filesEnum = new Enumerator(folderObj.Files);
        for (; !filesEnum.atEnd(); filesEnum.moveNext()) {
            var fileName = filesEnum.item().Name.toLowerCase();
            for (var i = 0; i < extensionArray.length; i++) {
                var ext = extensionArray[i].toLowerCase();
                if (fileName.length >= ext.length && fileName.substr(fileName.length - ext.length) === ext) {
                    return true;
                }
            }
        }

        var subEnum = new Enumerator(folderObj.SubFolders);
        for (; !subEnum.atEnd(); subEnum.moveNext()) {
            if (hasMatchingFiles(subEnum.item().Path, extensionArray)) {
                return true;
            }
        }
    } catch(e) {}
    return false;
}

function StartTransfer() {
    var destPath = document.getElementById("destFolderPath").value.replace(/^\s+|\s+$/g, '');

    if (destPath === "") {
        alert("Please select a destination folder first.");
        return;
    }

    if (!fso.FolderExists(destPath)) {
        alert("The selected destination folder does not exist.");
        return;
    }

    var hasDevices = false;
    for (var k in discoveredIPs) {
        hasDevices = true;
        break;
    }

    if (!hasDevices) {
        alert("No connected Seestar devices found. Please run an automatic scan or add manual IPs.");
        return;
    }

    var fitChecked = document.getElementById("chkFits").checked;
    var vidChecked = document.getElementById("chkVideo").checked;
    var imgChecked = document.getElementById("chkImages").checked;

    if (!fitChecked && !vidChecked && !imgChecked) {
        alert("Please select at least one file type to transfer in Section 4.");
        return;
    }

    isTransferring = true;
    LogMessage("=================================================");
    LogMessage("[TRANSFER] Starting file transfer via Robocopy...");
    LogMessage("=================================================");

    try {
        var shellApp = new ActiveXObject("Shell.Application");
        shellApp.Explore(destPath);
        LogMessage("[EXPLORER] Opened destination window: " + destPath);
    } catch(e) {
        LogMessage("[WARNING] Could not open destination window automatically: " + e.message);
    }

    var deviceIndex = 0;
    for (var ipKey in discoveredIPs) {
        if (!isTransferring) break;
        deviceIndex++;
        var ip = discoveredIPs[ipKey];
        var myWorksShare = "\\\\" + ip + "\\EMMC Images\\MyWorks";

        var deviceLogName = "Seestar_" + deviceIndex + ".log";
        var deviceLogPath = destPath + "\\" + deviceLogName;

        try {
            wsh.Run('cmd.exe /c "net use \\\\' + ip + '\\EMMC Images /user:guest >nul 2>&1"', 0, true);

            if (fso.FolderExists(myWorksShare)) {
                var myWorksFolder = fso.GetFolder(myWorksShare);
                var subFolders = myWorksFolder.SubFolders;
                var enumFolders = new Enumerator(subFolders);

                for (; !enumFolders.atEnd(); enumFolders.moveNext()) {
                    if (!isTransferring) break;
                    var targetFolderObj = enumFolders.item();
                    var targetName = targetFolderObj.Name;
                    var targetSourcePath = targetFolderObj.Path;
                    var targetDestFolderPath = destPath + "\\" + targetName;

                    LogMessage("[Checking] Scanning target folder: " + targetName);

                    if (fitChecked && isTransferring) {
                        var fitExts = [".fit", ".fits"];
                        if (hasMatchingFiles(targetSourcePath, fitExts)) {
                            var targetLights = targetDestFolderPath + "\\Lights";
                            LogMessage("[Copying] Transferring FITs to: " + targetName + "\\Lights");
                            var cmdFit = 'robocopy "' + targetSourcePath + '" "' + targetLights + '" *.fit *.fits /s /xo /copy:DA /dcopy:DA /ndl /np /ns /njh /unilog+:"' + deviceLogPath + '" /tee';
                            wsh.Run('cmd.exe /c "' + cmdFit + '"', 0, false);
                        }
                    }

                    if (vidChecked && isTransferring) {
                        var vidExts = [".mp4", ".avi"];
                        if (hasMatchingFiles(targetSourcePath, vidExts)) {
                            var targetVideo = targetDestFolderPath + "\\Video";
                            LogMessage("[Copying] Transferring Videos to: " + targetName + "\\Video");
                            var cmdVid = 'robocopy "' + targetSourcePath + '" "' + targetVideo + '" *.mp4 *.avi /s /xo /copy:DA /dcopy:DA /ndl /np /ns /njh /unilog+:"' + deviceLogPath + '" /tee';
                            wsh.Run('cmd.exe /c "' + cmdVid + '"', 0, true);
                        }
                    }

                    if (imgChecked && isTransferring) {
                        var imgExts = [".jpg", ".jpeg"];
                        if (hasMatchingFiles(targetSourcePath, imgExts)) {
                            var targetJpegs = targetDestFolderPath + "\\JPEGS";
                            LogMessage("[Copying] Transferring JPEGs to: " + targetName + "\\JPEGS");
                            var cmdImg = 'robocopy "' + targetSourcePath + '" "' + targetJpegs + '" *.jpg *.jpeg /s /xo /copy:DA /dcopy:DA /ndl /np /ns /njh /unilog+:"' + deviceLogPath + '" /tee';
                            wsh.Run('cmd.exe /c "' + cmdImg + '"', 0, true);
                        }
                    }
                }
                LogMessage("[TRANSFER] Completed transfers for Seestar " + deviceIndex + ". Log saved to: " + deviceLogName);
            } else {
                LogMessage("[WARNING] Could not access MyWorks share for IP: " + ip);
            }
        } catch(e) {
            LogMessage("[ERROR] Error reading target folders for IP " + ip + ": " + e.message);
        }
    }

    if (isTransferring) {
        isTransferring = false;
        LogMessage("=================================================");
        LogMessage("[TRANSFER] All file transfers completed successfully!");
        LogMessage("=================================================");
        alert("File transfer sequence complete!");
    } else {
        LogMessage("=================================================");
        LogMessage("[TRANSFER] Transfer process was stopped by the user.");
        LogMessage("=================================================");
    }
}

function ResumeTransfer() {
    if (isTransferring) {
        alert("A file transfer process is already actively running.");
        return;
    }
    LogMessage("=================================================");
    LogMessage("[TRANSFER] Resuming paused or stopped transfer sequence...");
    LogMessage("=================================================");
    StartTransfer();
}

function StopTransfer() {
    if (!isTransferring) {
        LogMessage("[TRANSFER] No active transfer process to stop.");
        return;
    }

    isTransferring = false;
    LogMessage("[TRANSFER] Stop signal issued. Terminating active file copy operations...");

    try {
        wsh.Run('cmd.exe /c taskkill /f /im robocopy.exe >nul 2>&1', 0, true);
        wsh.Run('cmd.exe /c taskkill /f /im cmd.exe /fi "WINDOWTITLE eq C:\\Windows\\system32\\cmd.exe" >nul 2>&1', 0, true);
        LogMessage("[TRANSFER] Active Robocopy tasks terminated successfully.");
    } catch(e) {
        LogMessage("[WARNING] Error halting processes: " + e.message);
    }

    alert("Transfer process Paused.");
}

function ConnectDeviceShare(ip) {
    var cmd = 'cmd.exe /c "net use \\\\' + ip + '\\EMMC Images /delete /y >nul 2>&1 & net use \\\\' + ip + '\\EMMC Images /user:guest >nul 2>&1"';
    wsh.Run(cmd, 0, false);
    LogMessage("[CONNECT] Initialized guest session root for " + ip);
}

function OpenDeviceShare(ip) {
    var sharePath = "\\\\" + ip + "\\EMMC Images\\MyWorks";
    try {
        wsh.Run('cmd.exe /c "net use \\\\' + ip + '\\EMMC Images /user:guest >nul 2>&1 & start "" "' + sharePath + '"', 0, false);
        LogMessage("[EXPLORER] Opened share folder for " + ip);
    } catch(e) {
        LogMessage("[ERROR] Could not open folder: " + e.message);
    }
}

function UpdateDeviceDisplay() {
    var displayBox = document.getElementById("deviceList");
    var htmlText = "";
    var count = 0;

    for (var key in discoveredIPs) {
        count++;
        var ip = discoveredIPs[key];
        var sharePath = "\\\\" + ip + "\\EMMC Images\\MyWorks";
        htmlText += "<div class='device-row'>" +
            "<span>[ONLINE] Seestar " + count + ": <span style='color:#ffffff;'>" + sharePath + "</span></span>";

        if (scanCompleted) {
            htmlText += "<button onclick=\"OpenDeviceShare('" + ip + "')\" style='padding:2px 8px; font-size:11px;'>Open Folder</button>";
        } else {
            htmlText += "<span style='color:#ffffff; font-size:11px; margin-left: 8px;'>[Scanning...]</span>";
        }
        htmlText += "</div>";
    }

    if (count === 0) {
        displayBox.innerHTML = "<span style='color: #ffffff;'>Devices will Automatically Connect once Scan is complete.</span>";
    } else {
        displayBox.innerHTML = htmlText;
    }
}

function RunAutoScan() {
    if (scanTimer !== null) {
        window.clearInterval(scanTimer);
        scanTimer = null;
    }

    scanCompleted = false;
    UpdateScanStatus("SCAN STATUS: CONFIGURING SYSTEM & SCANNING...");
    LogMessage("=================================================");
    LogMessage("[INFO] Enabling Insecure Guest Authentication...");
    LogMessage("=================================================");

    try {
        wsh.Run('reg add "HKLM\\SOFTWARE\\Policies\\Microsoft\\Windows\\LanmanWorkstation" /v AllowInsecureGuestAuth /t REG_DWORD /d 1 /f', 0, true);
        wsh.Run('reg add "HKLM\\SYSTEM\\CurrentControlSet\\Services\\LanmanWorkstation\\Parameters" /v AllowInsecureGuestAuth /t REG_DWORD /d 1 /f', 0, true);
    } catch(e) {
        LogMessage("[WARNING] Could not set registry keys (Run as Administrator required).");
    }

    LogMessage("[SCANNING] Sweeping local network for Seestar IP addresses...");

    discoveredIPs = {};
    deviceCount = 0;
    UpdateDeviceDisplay();

    var tempPs = wsh.ExpandEnvironmentStrings("%TEMP%") + "\\seestar_scan.ps1";
    var tempOut = wsh.ExpandEnvironmentStrings("%TEMP%") + "\\seestar_out.txt";

    if (fso.FileExists(tempOut)) {
        try { fso.DeleteFile(tempOut); } catch(e) {}
    }

    var psCode =
        "$adapter = Get-NetIPAddress -AddressFamily IPv4 | Where-Object {$_.IPAddress -notlike '127*' -and $_.IPAddress -notlike '169*' -and $_.IPv4Address} | Select-Object -First 1\n" +
        "if (-not $adapter) { '[ERROR] No active network connection.' | Out-File -FilePath '" + tempOut + "'; '[DONE]' | Out-File -Append -FilePath '" + tempOut + "'; exit }\n" +
        "$prefix = $adapter.IPAddress.Substring(0, $adapter.IPAddress.LastIndexOf('.'))\n" +
        "$msg = \"[SCAN] Sweeping subnet range $prefix.1 to $prefix.254...\"\n" +
        "[System.IO.File]::WriteAllText('" + tempOut + "', $msg + \"`r`n\")\n" +
        "1..254 | ForEach-Object {\n" +
        "    $ip = \"$prefix.$_\"\n" +
        "    [System.IO.File]::AppendAllText('" + tempOut + "', \"[Scanning] $ip`r`n\")\n" +
        "    $ping = New-Object System.Net.NetworkInformation.Ping\n" +
        "    $res = $ping.Send($ip, 60)\n" +
        "    if ($res.Status -eq 'Success') {\n" +
        "        try {\n" +
        "            $hostEntry = [System.Net.Dns]::GetHostEntry($ip)\n" +
        "            if ($hostEntry.HostName -like '*Seestar*') { \n" +
        "                [System.IO.File]::AppendAllText('" + tempOut + "', \"[Found] - Seestar - $ip`r`n\")\n" +
        "            }\n" +
        "        } catch {}\n" +
        "    }\n" +
        "}\n" +
        "[System.IO.File]::AppendAllText('" + tempOut + "', \"[DONE]`r`n\")\n";

    var f = fso.CreateTextFile(tempPs, true);
    f.Write(psCode);
    f.Close();

    wsh.Run("powershell.exe -NoProfile -ExecutionPolicy Bypass -WindowStyle Hidden -File \"" + tempPs + "\"", 0, false);

    var lastLen = 0;
    scanTimer = window.setInterval(function() {
        if (fso.FileExists(tempOut)) {
            try {
                var file = fso.OpenTextFile(tempOut, 1, false, -2);
                var content = "";
                if (!file.AtEndOfStream) {
                    content = file.ReadAll();
                }
                file.Close();

                if (content.length > lastLen) {
                    var newChunk = content.substring(lastLen);
                    lastLen = content.length;
                    var lines = newChunk.split("\n");
                    for (var i = 0; i < lines.length; i++) {
                        var line = lines[i].replace(/^\s+|\s+$/g, '');
                        if (line !== "" && line !== "[DONE]") {
                            if (line.indexOf("[SCAN]") !== -1) {
                                UpdateScanStatus(line);
                            } else if (line.indexOf("[Found]") !== -1) {
                                LogMessage(line);
                                var parts = line.split(" - ");
                                if (parts.length >= 3) {
                                    var matchedIP = parts[2];
                                    if (!discoveredIPs[matchedIP]) {
                                        deviceCount++;
                                        discoveredIPs[matchedIP] = matchedIP;
                                        UpdateDeviceDisplay();
                                        ConnectDeviceShare(matchedIP);
                                        AddSavedIP(matchedIP);
                                    }
                                }
                            } else {
                                LogMessage(line);
                            }
                        }
                    }
                }

                if (content.indexOf("[DONE]") !== -1) {
                    window.clearInterval(scanTimer);
                    scanTimer = null;
                    scanCompleted = true;
                    UpdateDeviceDisplay();
                    LogMessage("=================================================");
                    LogMessage("[INFO] Scan complete. Devices found: " + deviceCount);
                    LogMessage("=================================================");
                    if (deviceCount === 0) {
                        UpdateScanStatus("SCAN STATUS: NO SEESTAR DEVICES FOUND");
                    } else {
                        UpdateScanStatus("SCAN STATUS: COMPLETE (" + deviceCount + " FOUND)");
                    }
                }
            } catch(e) {}
        }
    }, 2000);
}

function ToggleManualBox() {
    var box = document.getElementById("manualBoxContainer");
    if (box.style.display === "none" || box.style.display === "") {
        box.style.display = "block";
    } else {
        box.style.display = "none";
    }
}

function SaveSingleManualIP() {
    var ipInput = document.getElementById("singleManualIp");
    var targetIp = ipInput.value.replace(/^\s+|\s+$/g, '');

    if (targetIp === "") {
        alert("Please enter an IP address.");
        return;
    }

    if (discoveredIPs[targetIp]) {
        alert("IP Address " + targetIp + " has already been added.");
        ipInput.value = "";
        return;
    }

    LogMessage("=================================================");
    LogMessage("[INFO] Validating manual IP: " + targetIp + "...");

    try {
        wsh.Run('reg add "HKLM\\SOFTWARE\\Policies\\Microsoft\\Windows\\LanmanWorkstation" /v AllowInsecureGuestAuth /t REG_DWORD /d 1 /f', 0, true);
        wsh.Run('reg add "HKLM\\SYSTEM\\CurrentControlSet\\Services\\LanmanWorkstation\\Parameters" /v AllowInsecureGuestAuth /t REG_DWORD /d 1 /f', 0, true);
    } catch(e) {}

    var tempValScript = wsh.ExpandEnvironmentStrings("%TEMP%") + "\\seestar_validate.ps1";
    var tempValOut = wsh.ExpandEnvironmentStrings("%TEMP%") + "\\seestar_validate_out.txt";

    if (fso.FileExists(tempValOut)) { try { fso.DeleteFile(tempValOut); } catch(e) {} }

    var psValCode =
        "$ip = '" + targetIp + "'\n" +
        "$isValid = $false\n" +
        "try {\n" +
        "    $ping = New-Object System.Net.NetworkInformation.Ping\n" +
        "    $res = $ping.Send($ip, 100)\n" +
        "    if ($res.Status -eq 'Success') {\n" +
        "        $hostEntry = [System.Net.Dns]::GetHostEntry($ip)\n" +
        "        if ($hostEntry.HostName -like '*Seestar*') { $isValid = $true }\n" +
        "    }\n" +
        "} catch {}\n" +
        "if (-not $isValid) {\n" +
        "    try {\n" +
        "        if (Test-Path \"\\\\$ip\\EMMC Images\\MyWorks\") { $isValid = $true }\n" +
        "    } catch {}\n" +
        "}\n" +
        "if ($isValid) {\n" +
        "    \"VALID:$ip\" | Out-File -FilePath '" + tempValOut + "'\n" +
        "} else {\n" +
        "    \"INVALID:$ip\" | Out-File -FilePath '" + tempValOut + "'\n" +
        "}\n";

    var fVal = fso.CreateTextFile(tempValScript, true);
    fVal.Write(psValCode);
    fVal.Close();

    wsh.Run("powershell.exe -NoProfile -ExecutionPolicy Bypass -WindowStyle Hidden -File \"" + tempValScript + "\"", 0, true);

    if (fso.FileExists(tempValOut)) {
        var readFile = fso.OpenTextFile(tempValOut, 1, false, -2);
        if (!readFile.AtEndOfStream) {
            var line = readFile.ReadLine().replace(/^\s+|\s+$/g, '');
            if (line.indexOf("VALID:") === 0) {
                var vIp = line.substring(6);
                deviceCount++;
                discoveredIPs[vIp] = vIp;
                ConnectDeviceShare(vIp);
                AddSavedIP(vIp);
                scanCompleted = true;
                UpdateDeviceDisplay();
                UpdateScanStatus("SCAN STATUS: MANUAL CONFIG (" + deviceCount + " ACTIVE)");
                LogMessage("[MANUAL] Verified & Added Seestar IP: " + vIp);
                
                var addedBox = document.getElementById("addedIpsDisplay");
                addedBox.innerHTML += "<div>" + vIp + " (Active)</div>";
                ipInput.value = "";
                
                alert("IP " + vIp + " validated and added! You can enter another or click Close.");
            } else {
                LogMessage("[WARNING] Rejected IP (Not a Seestar or Unreachable): " + targetIp);
                alert("IP " + targetIp + " could not be verified as a Seestar device.");
            }
        }
        readFile.Close();
    }
}
</script>
</head>

<body>

<!-- ======================================================================= -->
<!-- SCREEN 1: LANDING PAGE (3 SEPARATED ROW SECTIONS & DISCLOSURE)          -->
<!-- ======================================================================= -->
<div id="landingScreen">
    <div class="landing-card">
        <div class="landing-title">NICKTONKS_ASTROPHOTOGRAPHY</div>
        <div class="landing-subtitle">Seestar Station Mode File Organiser & Copy Tool v1.3</div>
        
        <!-- CONNECTION TYPES -->
        <div class="landing-row-section">
            <div class="landing-row-title">Supported Connection Modes</div>
            <div class="landing-grid-two-col">
                <div class="landing-grid-box">
                    <h4>Home Wi-Fi (Station Mode)</h4>
                    <p>PC and Seestar connect through your local home router. IP addresses are assigned dynamically via DHCP.</p>
                </div>
                <div class="landing-grid-box">
                    <h4>Direct Seestar Wi-Fi</h4>
                    <p>PC connects directly to the telescope hotspot. Operates on a standard static IP (typically 10.0.0.1).</p>
                </div>
            </div>
        </div>

        <!-- DISCOVERY MODES -->
        <div class="landing-row-section">
            <div class="landing-row-title">Device Discovery Options</div>
            <div class="landing-grid-two-col">
                <div class="landing-grid-box">
                    <h4>Automatic Network Scan</h4>
                    <p>Sweeps your subnet range (1..254) via ping and DNS hostnames. Best when Station Mode IP is unknown.</p>
                </div>
                <div class="landing-grid-box">
                    <h4>Manual IP Address Input</h4>
                    <p>Directly validates a specific IP. Fastest option for Direct Wi-Fi or router static DHCP reservations.</p>
                </div>
            </div>
        </div>

        <!-- AUTOMATED FOLDER HIERARCHY -->
        <div class="landing-row-section">
            <div class="landing-row-title">Automated Destination Folder Hierarchy</div>
            <div class="landing-grid-box-full">
                <h4>Automated Folder Setup</h4>
                <p>Downloaded files are automatically organized under your chosen destination directory by target object and file type:</p>
                <div class="folder-tree">
                    [Destination Folder]\[Target Name]\Lights (.fit)<br>
                    [Destination Folder]\[Target Name]\Videos (.avi/.mp4)<br>
                    [Destination Folder]\[Target Name]\Jpegs (.jpg)<br>
                    [Destination Folder]Seestar_1.log (individual transfer log for each connected Seestar)
                </div>
            </div>
        </div>

        <!-- DISCLOSURE NOTICE -->
        <div class="disclosure-box">
            <h4>Important Tool Disclosures & Protocols</h4>
            This utility utilizes standard Windows <strong>Robocopy</strong> protocols configured to copy any file matching your selected categories. Subsequent sync operations will automatically skip existing files and only transfer new, uncopied files from your Seestar devices.
            <br><br>
            To successfully access Samba shares on your Seestar over local Wi-Fi, the application dynamically adjusts bespoke Windows Registry security settings during execution:
            <ul>
                <li><code>HKLM\SOFTWARE\Policies\Microsoft\Windows\LanmanWorkstation\AllowInsecureGuestAuth</code> (Set to 1)</li>
                <li><code>HKLM\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters\AllowInsecureGuestAuth</code> (Set to 1)</li>
            </ul>
            Upon clicking <strong>Close and Exit</strong>, you will be prompted to automatically revert these Registry settings back to Windows defaults (0) to restore standard security policies.
            <br><br>
            The app also remembers your last used <strong>destination folder</strong> and any <strong>Seestar IP addresses</strong> you connect to, stored locally under <code>HKCU\Software\NickTonks_Seestar</code>, so they can be reconnected automatically next time.
        </div>
        
        <button class="btn-enter" onclick="EnterApplication()">Launch Transfer Tool</button>
        
        <div class="note" style="margin-top: 12px;">
            Find me on Instagram: <span><a href="microsoft-edge:https://instagram.com/NICKTONKS_ASTROPHOTOGRAPHY" target="_blank">@NICKTONKS_ASTROPHOTOGRAPHY</a></span>
        </div>
    </div>
</div>

<!-- ======================================================================= -->
<!-- SCREEN 2: MAIN APPLICATION WORKSPACE                                   -->
<!-- ======================================================================= -->
<div id="mainAppContainer" class="container">

<h2>NICKTONKS_ASTROPHOTOGRAPHY<br>Seestar Station Mode File Organiser & Copy Tool v1.3</h2>

<div class="panel">
<label class="section-label"><strong>1. Device Discovery:</strong></label><br>

<div class="btn-action-group">
<button onclick="RunAutoScan()">Run Automatic Scan</button>
<button onclick="ToggleManualBox()">Add Manual IPs</button>
<button onclick="ForgetSavedDevices()">Forget Saved IPs</button>
</div>

<div id="manualBoxContainer">
<h3 style="color: #ff9900; margin-top: 0; font-size: 13px; text-align: center; border-bottom: 1px solid #1a2744; padding-bottom: 4px;">Enter Manual Seestar IP</h3>
<div style="display: flex; gap: 6px; margin-bottom: 8px;">
<input type="text" id="singleManualIp" placeholder="e.g. 192.168.1.150" style="font-size: 11px; flex: 1;" />
<button class="btn-primary" onclick="SaveSingleManualIP()" style="width: 80px; font-size: 11px; padding: 6px;">Add IP</button>
</div>

<label style="font-size: 10px; color: #888;">Added / Reconnected IPs this session:</label>
<div id="addedIpsDisplay" style="background-color: #0d1221; border: 1px solid #1a2744; padding: 6px; font-family: 'Consolas', monospace; font-size: 11px; color: #00b386; margin-bottom: 8px; border-radius: 3px; max-height: 80px; overflow-y: auto;"></div>

<div style="display: flex; justify-content: flex-end; margin-top: 8px;">
<button onclick="ToggleManualBox()" style="background-color: #1a2744; font-size: 11px; width: 100%;">Done / Close</button>
</div>
</div>

<label style="margin-top: 6px; font-size: 11px; color: #ffffff;">Scan Status:</label>
<div id="scanStatusBox">SCAN STATUS: IDLE</div>
</div>

<div class="panel">
<label class="section-label"><strong>2. Connected Devices: If prompted for username and password: guest: no password</strong></label><br>
<div id="deviceList" class="device-display">
<span style="color: #ffffff;">Devices will Automatically Connect once Scan is complete.</span>
</div>
</div>

<div class="panel">
<label class="section-label"><strong>3. Select a Location to save files:</strong></label><br>
<div class="row-inline">
<input type="text" id="destFolderPath" placeholder="Choose a destination folder..." style="flex: 1;" />
<button onclick="BrowseDestinationFolder()" style="white-space: nowrap;">Browse...</button>
</div>
</div>

<div class="panel">
<label class="section-label"><strong>4. Select file types - these will be saved as [Target/Lights], [Target/Video], [Target/Jpegs]:</strong></label><br>
<div class="checkbox-group">
<label><input type="checkbox" id="chkFits" checked /> FITs (.fit)</label>
<label><input type="checkbox" id="chkVideo" checked /> Video (.avi / .MP4)</label>
<label><input type="checkbox" id="chkImages" checked /> Images (.jpeg)</label>
</div>
</div>

<div class="panel">
<label class="section-label"><strong>5. Transfer Controls:</strong></label><br>
<div class="transfer-buttons">
<button class="btn-primary" onclick="StartTransfer()" style="flex: 1;">Start Transfer</button>
<button class="btn-danger" onclick="StopTransfer()" style="flex: 1;">Pause Transfer</button>
<button class="btn-resume" onclick="ResumeTransfer()" style="flex: 1;">Resume Transfer</button>
</div>
</div>

<div class="panel">
<label class="section-label" style="font-size: 11px;"><strong>6. Execution Status Log:</strong></label><br>
<textarea id="logArea" readonly></textarea>
</div>

<div class="footer-buttons-stacked">
<button class="btn-exit-custom" onclick="CloseAndExit()">Close and Exit</button>
</div>

<div class="note">
Ensure your Seestars are powered on and in Station Mode.<br>
Find me on Instagram: <span><a href="microsoft-edge:https://instagram.com/NICKTONKS_ASTROPHOTOGRAPHY" target="_blank">@NICKTONKS_ASTROPHOTOGRAPHY</a></span>
</div>

</div>
</body>
</html>
