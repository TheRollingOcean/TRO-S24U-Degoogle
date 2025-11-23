# S24UDegoogle
A running wiki of how I degoogled my S24U and the privacy settings I used. This does not replace the entirety of the Samsung stack and allows for stability. 

Here's my frozen app stack from Shizuku and FreezeYou!

Note that this disables, Findmy, BLE, Smarthings integrations disables GMS, Samsung and Google accounts, and locks the baseline at Android 15 (no OTA). Battery is great! 

It relies on rethink to keep the proprietary app stack from reporting out. 

Debloat inpart from https://xdaforums.com/t/s24-ultra-debloat-and-privacy-list.4654142/

Lots of research on r/fossdroid r/privacy and r/degoogle

**Google / AOSP (system-level)**

    com.google.audio.hearing.visualization.accessibility.scribe
    com.google.android.safetycenter.resources
    com.android.calllogbackup
    com.google.android.partnersetup
    com.android.dreams.phototable
    com.android.dreams.basic
    com.google.android.feedback
    com.android.chrome
    com.google.android.apps.carrier.carrierwifi
    com.google.android.overlay.gmsconfig.asi
    com.google.android.adservices.api
    com.google.android.setupwizard
    com.android.apps.tag
    com.google.android.apps.maps
    com.google.android.overlay.gmsconfig.photos
    com.google.android.tts
    com.google.android.googlequicksearchbox
    com.android.internal.display.cutout.emulation.double
    com.android.theme.font.notoserifsource
    com.google.android.health.connect.backuprestore
    com.android.vending
    com.android.wallpaper.livepicker
    com.android.wallpapercropper
    com.google.ar.core
    com.google.android.overlay.gmsconfig.gsa
    com.google.android.overlay.gmsconfig.geotz
    com.android.role.notes.enabled
    com.google.android.overlay.gmsconfig.common
    com.google.mainline.adservices
    com.android.internal.display.cutout.emulation.corner
    com.google.android.gms
    com.android.printspooler
    com.google.mainline.telemetry
    com.google.android.healthconnect.controller

**Samsung / Sec / Knox / OEM system**

    com.sec.android.gallery3d
    com.samsung.android.widget.pictureframe
    com.samsung.android.app.goodcatch
    com.samsung.android.calendar
    com.samsung.android.app.reminder
    com.samsung.android.wallpaper.magician
    com.samsung.android.mydevice
    com.sec.enterprise.knox.cloudmdm.smdms
    com.samsung.android.knox.zt.framework
    com.sec.android.app.samsungapps
    com.samsung.android.service.tagservice
    com.sec.android.app.SecSetupWizard
    com.sec.location.nsflp2
    com.samsung.android.app.aodservice
    com.samsung.android.knox.mpos
    com.samsung.android.knox.kpecore
    com.sec.android.easyonehand
    com.sec.providers.assisteddialing
    com.sec.android.app.vepreload
    com.sec.android.app.ve.vebgm
    com.samsung.android.service.aircommand
    com.sec.android.app.camera
    com.samsung.android.honeyboard
    com.samsung.android.spayfw
    com.samsung.android.accessibility.talkback
    com.samsung.android.themestore
    com.sec.android.app.magnifier
    com.samsung.android.knox.analytics.uploader
    com.samsung.android.allshare.service.mediashare
    com.samsung.android.wallpaper.live
    com.samsung.android.knox.attestation
    com.sec.android.app.chromecustomizations
    com.knox.vpn.proxyhandler
    com.samsung.android.app.sketchbook
    com.android.wallpaper.livepicker
    com.samsung.android.easysetup
    com.samsung.android.stickercenter
    com.sec.spp.push
    com.android.managedprovisioning
    com.samsung.android.intellivoiceservice
    com.osp.app.signin
    com.samsung.android.wallpaper.live
    com.samsung.android.knox.containercore
    com.samsung.android.bbc.bbcagent
    com.samsung.android.app.notes
    com.samsung.android.sdm.config
    com.samsung.android.mcfserver
    com.android.wallpapercropper
    com.samsung.android.app.clockface
    com.samsung.android.mobileservice
    com.samsung.vzwapiservice
    com.samsung.android.service.stplatform
    com.samsung.android.beaconmanager
    com.samsung.android.smartmirroring
    com.samsung.android.knox.pushmanager
    com.samsung.android.settingshelper
    com.samsung.android.game.gos
    com.sec.android.app.dexonpc
    com.sec.android.easyMover
    com.sec.android.soagent
    com.samsung.videoscan
    com.samsung.sdm
    com.samsung.cmh
    com.samsung.android.knox.app.networkfilter
    com.samsung.android.aware.service
    com.samsung.android.app.dofviewer
    com.samsung.android.da.daagent
    com.sec.android.easyMover.Agent
    com.samsung.android.gru

**Freezing Core Samsung OTA**
```
com.sec.android.soagent
com.wssyncmldm
com.sec.android.fotaclient
com.sec.android.soagent.knox
com.samsung.sdm
com.samsung.syncml.dm
```

**Freezing Verizon Carrier OTA / Push**
```
com.vzw.apnlib
com.vzw.hss.myverizon
com.vzw.hs.android.modlite
```

**On Permissions**
**For BLE, other realated settings** (if they exist after stack removal)
Concise menu-tree (top → child → toggle/action)

    Settings
        Connections
            Bluetooth
                Toggle: Bluetooth → Off
                Optional: Bluetooth device list → Forget any saved devices (tap device → Forget)
            More connection settings (or More connection options)
                Nearby device scanning (or Nearby share / Nearby devices)
                    Toggle: Nearby device scanning → Off
  
                Quick Share (Samsung) / Nearby Share (Google)
                    Quick Share → Off
                    Nearby Share → Off
        
        Location (or Connections > Location)
            Use location → Off (optional; stops location-based BLE scanning)
            Scanning (or Wi‑Fi and Bluetooth scanning)
                Bluetooth scanning → Off
                Wi‑Fi scanning → Off (optional)
        Apps
            Permission manager (or Settings > Privacy > Permission manager)
                Nearby devices (or "Nearby devices" permission)
                    For each app listed → Deny
                Location
                    Review apps that have Location permission → Set to Deny or “While using app” as desired
                Bluetooth (or "Nearby & Bluetooth" permissions)
                    BLUETOOTH_SCAN / BLUETOOTH_CONNECT / BLUETOOTH_ADVERTISE → Deny for apps you don’t trust
            See all apps → (select specific app) → Permissions → Nearby devices / Location / Bluetooth → Deny
        Security & privacy (or Biometrics and security)
            Find My Device (Google)
                Toggle: Find My Device (or “Find My Device” in Security) → Off
                Alternative: Google account → myaccount.google.com/devices → Find My Device settings → Turn off
            Find My Mobile (Samsung) — often under Biometrics and security
                Settings > Biometrics and security > Find My Mobile → Turn off “Find My Mobile”
                Turn off “Remote unlock” / “Send last location” if present
                Sign out of Samsung account (if you want the feature fully disabled on device)
        Google (Settings > Google)
            Device security / Safety & emergency / Account services
                Find My Device → Turn off (if present here)
        Accounts (or Settings > Accounts and backup > Accounts)
            Google account → Remove account (only if you want to sever Find My Device and syncing completely)
            Samsung account → Remove account (only if you want to remove Samsung Find My Mobile)
        Advanced features
            Nearby device-related features (Quick Share / SmartThings Find integration)
                Disable Quick Share / SmartThings Find components as needed

**Disabling Sensors instructions**
Quick summary menu tree (top → child → toggle/action)

    Settings
        About phone
            Software information
                Build number → Tap 7 times → Enable Developer options
        (or) Settings → Search: "Developer options"
        System → Developer options
            USB debugging → ON (required for ADB)
            (Look for) Disable sensors (may appear as)
                “Disable sensors”
                “Disable all sensors”
                “Sensors off”
                Toggle → ON (disables device sensors)
        Privacy (or Security & privacy)
            Sensors Off (or “Sensors” / “Sensors privacy”)
                Add Quick Settings tile (edit tiles) → Sensors off → Tap to enable
        Connections / Location / Apps (for related effects)
            Verify Find My, location services, Bluetooth behavior (these may be impacted)

**BLE ADB Commands:**
```
adb shell settings put global ble_scan_always_enabled 0
adb shell pm disable-user --user 0 com.android.nearby.halfsheet
adb shell pm disable-user --user 0 com.google.android.nearby
adb shell pm disable-user --user 0 com.samsung.android.nearbyscanning
adb shell settings put secure fmm_offline_find_enabled 0
adb shell settings put secure fmm_offline_find_support 0
adb shell settings put secure offline_find_support 0
adb shell settings put secure offline_find_enabled 0
adb shell pm disable-user --user 0 com.google.android.gms.nearby.exposurenotification
adb shell pm disable-user --user 0 com.google.android.gms.nearby.messages
adb shell pm disable-user --user 0 com.google.android.gms.location.reporting
adb shell pm disable-user --user 0 com.google.android.gms.location.history
adb shell settings put global settings_bluetooth_le_scan_mode 0
```
**Cross device communication**
``` com.samsung.android.smartmirroring
com.samsung.android.aware.service
com.samsung.android.nearbyservice
com.samsung.android.upsell
com.samsung.android.uwb
```

**Nearby Devices Scanning**
``` adb shell pm disable-user --user 0 com.android.nearby.halfsheet
adb shell pm disable-user --user 0 com.google.android.nearby
adb shell pm disable-user --user 0 com.samsung.android.nearbyscanning
```

**Replacement APP stack.**

**Rethink** In global firewall Block all except bypassed apps and IPs. This is one of the few firewall and VPNs that use only one slot. Also block installed apps by default. 

**TrackerControl** Configure Tracker control to not take a VPN slot, but it does correctly display correct trackers once apps are installed. 

**Appmanager** Super detailed systems information. 

**Canta** a classic, gives nice writeups on tools before you freeze them. 

**FreezeYou** I really like the freeze shortcuts you can make and save to the homescreen. I prefer this over Canta. 

**PCAP Droid** Not manatory but allows you to see all apps  trying to squack out. 
