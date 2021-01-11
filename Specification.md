Application Registration Specification
============================================

Application registration files are used to indicate that an application is installed on the system. This then allows third party launchers and applications to be aware of how to launch other applications. It's meant to facilitate package managers adding and removing applications and automatically reloading third party launchers. These files must have a file extension of `remarkable` and must be located in `/opt/usr/share/applications`.

## Draft Sample
```ini
# Shared
displayName=Sample application
description=This is a sample application
bin=/opt/bin/sample-application
workingDirectory=/home/root
user=sample
group=root
environment=QDBUS_DEBUG=1
events=stop=rm /tmp/.sample-running
# Oxide specific
flags=chroot, autoStart
directories=/home/root, /tmp
type=foreground
permissions=power, wifi
events=resume=touch /tmp/.sample-running
events=pause=rm /tmp/.sample-running
```
## JSON Sample

```json
{
    // Shared
    "displayName": "Sample application",
    "description": "This is a sample application",
    "bin": "/opt/bin/sample-application",
    "workingDirectory": "/home/root",
    "user": "sample",
    "group": "root",
    "environment": {
        "QDBUS_DEBUG": "1"
    },
    "events": {
        "stop": "rm /tmp/.sample-running"
    },

    // Oxide specific
    "flags": ["chroot", "autoStart"],
    "directories": ["/home/root", "/opt/etc"],
    "type": "foreground",
    "permissions": ["power", "wifi"],
    "events": {
        "resume": "touch /tmp/.sample-running",
        "pause": "rm /tmp/.sample-running"
    }
}
```

## YAML Sample

```yaml
---
# Shared
displayName: Sample application
description: This is a sample application
bin: /opt/bin/sample-application
workingDirectory: /home/root
user: sample
group: root
environment:
  QDBUS_DEBUG: 1
events:
  stop: rm /tmp/.sample-running
---
# Oxide specific
flags: [chroot, autoStart]
directories:
- /home/root
- /etc
type: foreground
permissions: [power, wifi]
events:
  resume: touch /tmp/.sample-running
  pause: rm /tmp/.sample-running
```



Oxide Properties Documentation
----------

| Property         | Type         | Required | Description                                                  |
| ---------------- | ------------ | -------- | ------------------------------------------------------------ |
| bin              | string       | Yes      | The path to the application. If this file doesn't exist, the application will not be registered. |
| type             | string       | Yes      | The type of application this is. <ul><li>`"background"`: This application runs in the background and does not display anything on the screen.</li><li>`"foreground"`: This application runs in the foreground and must be paused when it's not the active application.</li><li>`"backgroundable"`: This application runs in both the foreground and the background and supports being notified with `SIGUSR1` and `SIGUSR2` when being swapped between the two states by the user.</li></ul> |
| flags            | string array | No       | An array of flags for the application.<ul><li>`"hidden"`: Do not display this application to the user.</li><li>`"autoStart"`: Start this application automatically when tarnish starts up. Should only be used on applications with a type of `"backgroundable"` or `"background"`.</li><li>`"chroot"`: Run this application in a chroot.</li><li>`"system"`: This is a system application and cannot be removed by the user. This is set by default as applications using an application registration file are intended to be removed by a package manager.</li></ul> |
| displayName      | string       | No       | The human readable name to display to the user.              |
| description      | string       | No       | Description of the app meant to be displayed to the user.    |
| icon             | string       | No       | Path to an image file to use as the icon for this application. |
| user             | string       | No       | User to run this application as. Default is `root`.          |
| group            | string       | No       | Group to run this application in. Default is `root`.         |
| workingDirectory | string       | No       | Directory to set as the current working directory of the application. Default is `/`. |
| directories      | string array | No       | When an application is running in a chroot, also map these directories into the chroot with read/write privileges. |
| permissions      | string array | No       | API permissions to grant this application. Without these, any calls to the API will be refused or return incorrect results.<ul><li>`"permissions"`: Application can modify applications settings/permissions in the Apps API.</li><li>`"apps"`: Apps API access</li><li>`"notification"`: Notification API access</li><li>`"power"`: Power API access</li><li>`"screen"`: Screen API access</li><li>`"system"`: System API access</li><li>`"wifi"`: Wifi API access</li></ul> |
| environment      | string map   | No       | Extra environment variables to set before running the application. |
| events           | string map   | No       | Custom commands to run on an event.<ul><li>`"resume"`: Run when the application is resumed</li><li>`"pause"`: Run when the application is paused</li><li>`"stop"`: Run when the application is stopped</li></ul> |