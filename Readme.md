# MQTT Topics for TV Control

## 1. Power Control

- **Topic**: `sony/tv/cmd/power_on`
  - **Attribute**: None (Command to turn on the TV; no argument needed).

- **Topic**: `sony/tv/cmd/power_off`
  - **Attribute**: None (Command to turn off the TV; no argument needed).

- **Topic**: `sony/tv/cmd/power_toggle`
  - **Attribute**: None (Command to toggle power state; no argument needed).

- **Topic**: `sony/tv/cmd/power_get`
  - **Attribute**: None (Command to check if the TV is powered on/off; no argument needed).

---

## 2. Volume Control

- **Topic**: `sony/tv/cmd/vol_get`
  - **Attribute**: None (Request the current volume level; no argument needed).

- **Topic**: `sony/tv/cmd/vol_set`
  - **Attribute**: Integer (Volume level, 0-99, e.g., `25`).

- **Topic**: `sony/tv/cmd/mute_on`
  - **Attribute**: None (Mute the TV; no argument needed).

- **Topic**: `sony/tv/cmd/mute_off`
  - **Attribute**: None (Unmute the TV; no argument needed).

- **Topic**: `sony/tv/cmd/mute_get`
  - **Attribute**: None (Request mute status; no argument needed).

---

## 3. Input Selection

- **Topic**: `sony/tv/cmd/input_hdmi`
  - **Attribute**: Integer (HDMI input selection, 1-99, e.g., `1`).

- **Topic**: `sony/tv/cmd/input_composite`
  - **Attribute**: None (Switch to composite input; no argument needed).

- **Topic**: `sony/tv/cmd/input_component`
  - **Attribute**: None (Switch to component input; no argument needed).

- **Topic**: `sony/tv/cmd/input_mirror`
  - **Attribute**: None (Switch to mirror input; no argument needed).

- **Topic**: `sony/tv/cmd/input_get`
  - **Attribute**: None (Request current input; no argument needed).

---

## 4. Picture Mute Control

- **Topic**: `sony/tv/cmd/pmute_on`
  - **Attribute**: None (Mute the picture; no argument needed).

- **Topic**: `sony/tv/cmd/pmute_off`
  - **Attribute**: None (Unmute the picture; no argument needed).

- **Topic**: `sony/tv/cmd/pmute_toggle`
  - **Attribute**: None (Toggle picture mute; no argument needed).

- **Topic**: `sony/tv/cmd/pmute_get`
  - **Attribute**: None (Request picture mute status; no argument needed).

---

## 5. Scene Selection

- **Topic**: `sony/tv/cmd/scene_auto`
  - **Attribute**: None (Set auto scene; no argument needed).

- **Topic**: `sony/tv/cmd/scene_auto24p`
  - **Attribute**: None (Set auto 24p scene; no argument needed).

- **Topic**: `sony/tv/cmd/scene_general`
  - **Attribute**: None (Set general scene; no argument needed).

- **Topic**: `sony/tv/cmd/scene_get`
  - **Attribute**: None (Request current scene; no argument needed).

---

## 6. Network Information

- **Topic**: `sony/tv/cmd/net_broadcast`
  - **Attribute**: None (Request broadcast network info; no argument needed).

- **Topic**: `sony/tv/cmd/net_mac`
  - **Attribute**: None (Request MAC address; no argument needed).

---

## 7. IRCC / Remote Control Keys

For all remote control key commands, the **attribute** is either `null` or used to trigger specific actions on the TV. The actual attribute value corresponds to the key press or action:

- **Topic**: `sony/tv/cmd/ir_display` to `sony/tv/cmd/ir_0`
  - **Attribute**: None (Each of these represents a specific key press; no additional value required).

  Example:
  - `ir_home`: Press the **Home** button.
  - `ir_up`: Press the **Up Arrow** button.
  - `ir_red`: Press the **Red** button, etc.

---

## 8. TV Configuration (For Changing TV IP/Port)

- **Topic**: `sony/tv/config/ip`
  - **Attribute**: String (IP address of the TV, e.g., `"192.168.3.200"`).

- **Topic**: `sony/tv/config/port`
  - **Attribute**: String (Port number, e.g., `"20060"`).

---

## General Command Structure

- **Topic Format**: `sony/tv/cmd/{command}`

- **Payload**:
  - For most commands, the payload could be `null` (i.e., no argument is passed with the command).
  - For commands like volume, input selection, and TV configuration, the payload would typically carry an argument (e.g., volume level, HDMI input index, TV IP address, etc.).

---

## Summary of Attributes

- Power control commands typically don’t require additional attributes (just send the command).
- Volume control uses a numeric attribute (0-99).
- Input selection commands take a numeric input for HDMI or other types of input.
- Remote control keys don’t need a payload; the action is triggered by the key topic itself.
- TV configuration commands use string values (IP and port).

---


# MQTT Topic Mapping – Previous vs Updated Format

This table compares the previous MQTT topic structure used in the Sony TV app with the updated standardized format:

| **Previous Topic**                  | **Updated Topic**                                                                 |
|------------------------------------|----------------------------------------------------------------------------------|
| `sony/tv/cmd/power_on`             | `nrk/meeting_room/request/display_service/power/on`                             |
| `sony/tv/cmd/power_off`            | `nrk/meeting_room/request/display_service/power/off`                            |
| `sony/tv/cmd/power_toggle`         | `nrk/meeting_room/request/display_service/power/toggle`                         |
| `sony/tv/cmd/power_get`            | `nrk/meeting_room/request/display_service/power/get`                            |
| `sony/tv/cmd/vol_get`              | `nrk/meeting_room/request/display_service/volume/get`                           |
| `sony/tv/cmd/vol_set`              | `nrk/meeting_room/request/display_service/volume/set`                           |
| `sony/tv/cmd/mute_on`              | `nrk/meeting_room/request/display_service/volume/mute_on`                       |
| `sony/tv/cmd/mute_off`             | `nrk/meeting_room/request/display_service/volume/mute_off`                      |
| `sony/tv/cmd/mute_get`             | `nrk/meeting_room/request/display_service/volume/mute_get`                      |
| `sony/tv/cmd/input_hdmi`           | `nrk/meeting_room/request/display_service/input/hdmi`                           |
| `sony/tv/cmd/input_composite`      | `nrk/meeting_room/request/display_service/input/composite`                      |
| `sony/tv/cmd/input_component`      | `nrk/meeting_room/request/display_service/input/component`                      |
| `sony/tv/cmd/input_mirror`         | `nrk/meeting_room/request/display_service/input/mirror`                         |
| `sony/tv/cmd/input_get`            | `nrk/meeting_room/request/display_service/input/get`                            |
| `sony/tv/cmd/pmute_on`             | `nrk/meeting_room/request/display_service/advanced_controls/picture_mute_on`    |
| `sony/tv/cmd/pmute_off`            | `nrk/meeting_room/request/display_service/advanced_controls/picture_mute_off`   |
| `sony/tv/cmd/pmute_toggle`         | `nrk/meeting_room/request/display_service/advanced_controls/picture_mute_toggle`|
| `sony/tv/cmd/pmute_get`            | `nrk/meeting_room/request/display_service/advanced_controls/picture_mute_get`   |
| `sony/tv/cmd/scene_auto`           | `nrk/meeting_room/request/display_service/advanced_controls/scene_auto`         |
| `sony/tv/cmd/scene_auto24p`        | `nrk/meeting_room/request/display_service/advanced_controls/scene_auto24p`      |
| `sony/tv/cmd/scene_general`        | `nrk/meeting_room/request/display_service/advanced_controls/scene_general`      |
| `sony/tv/cmd/scene_get`            | `nrk/meeting_room/request/display_service/advanced_controls/scene_get`          |
| `sony/tv/cmd/net_broadcast`        | `nrk/meeting_room/request/display_service/network/broadcast`                    |
| `sony/tv/cmd/net_mac`              | `nrk/meeting_room/request/display_service/network/mac`                          |
| `sony/tv/cmd/ir_home`              | `nrk/meeting_room/request/display_service/remote_keys/ir_home`                  |
| `sony/tv/cmd/ir_vol_up`            | `nrk/meeting_room/request/display_service/remote_keys/ir_vol_up`                |
| `sony/tv/cmd/ir_mute`              | `nrk/meeting_room/request/display_service/remote_keys/ir_mute`                  |
| `sony/tv/config/ip`                | `nrk/meeting_room/status/display_service/config/ip`                             |
| `sony/tv/config/port`              | `nrk/meeting_room/status/display_service/config/port`                           |

> Replace `nrk` with your actual site name and `meeting_room` with the correct room identifier as per deployment.



# Sony Bravia TV MQTT Topics

This document defines the MQTT topics and payloads for controlling Sony Bravia TVs via MQTT.

---

##  MQTT Topic Structure for version 3


Where:

- `<TV_NAME>` → Name of the TV (e.g., `TV-1`, `MeetingRoomTV`)  
- `<COMMAND>` → Commands like `power_on`, `vol_set`, `input_hdmi`  
- `<PROPERTY>` → TV properties to monitor (`power`, `volume`, `mute`, `input`)  
- `<IRCC_KEY>` → IRCC remote buttons (`home`, `up`, `down`, `vol_up`, `vol_down`, etc.)

---

##  Full MQTT Topic List

### Power

| Topic | Payload |
|-------|---------|
| `sony/tv/<TV_NAME>/cmd/power_on` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/power_off` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/power_toggle` | `"true"` |
| `sony/tv/<TV_NAME>/status/power` | `"ON"` / `"OFF"` |

---

### Volume / Mute

| Topic | Payload |
|-------|---------|
| `sony/tv/<TV_NAME>/cmd/vol_set` | `{"level": 20}` |
| `sony/tv/<TV_NAME>/cmd/vol_up` | `"1"` |
| `sony/tv/<TV_NAME>/cmd/vol_down` | `"1"` |
| `sony/tv/<TV_NAME>/cmd/vol_get` | `"true"` |
| `sony/tv/<TV_NAME>/status/volume` | `0-99` |
| `sony/tv/<TV_NAME>/cmd/mute_on` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/mute_off` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/mute_toggle` | `"true"` |
| `sony/tv/<TV_NAME>/status/mute` | `"ON"` / `"OFF"` |

---

### Input Selection

| Topic | Payload |
|-------|---------|
| `sony/tv/<TV_NAME>/cmd/input_hdmi` | `"1"` / `"2"` / `"3"` / `"4"` |
| `sony/tv/<TV_NAME>/cmd/input_composite` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/input_component` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/input_mirror` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/input_get` | `"true"` |
| `sony/tv/<TV_NAME>/status/input` | `"HDMI1"`, `"HDMI2"`, `"Composite"`, `"Screen Mirroring"` |

---

### Picture Mute

| Topic | Payload |
|-------|---------|
| `sony/tv/<TV_NAME>/cmd/pmute_on` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/pmute_off` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/pmute_toggle` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/pmute_get` | `"true"` |
| `sony/tv/<TV_NAME>/status/pmute` | `"ON"` / `"OFF"` |

---

### Scene / Picture Mode

| Topic | Payload |
|-------|---------|
| `sony/tv/<TV_NAME>/cmd/scene_auto` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/scene_auto24p` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/scene_general` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/scene_get` | `"true"` |
| `sony/tv/<TV_NAME>/status/scene` | `"Auto"`, `"Auto24p"`, `"General"` |

---

### Network Info

| Topic | Payload |
|-------|---------|
| `sony/tv/<TV_NAME>/cmd/net_broadcast` | `"true"` |
| `sony/tv/<TV_NAME>/cmd/net_mac` | `"true"` |
| `sony/tv/<TV_NAME>/status/broadcast` | `"192.168.x.x"` |
| `sony/tv/<TV_NAME>/status/mac` | `"AA:BB:CC:DD:EE:FF"` |

---

### IRCC Remote

| Topic | Payload |
|-------|---------|
| `sony/tv/<TV_NAME>/ircc/<IRCC_KEY>` | `"true"` |

**Example IRCC keys:**  
`home`, `options`, `return`, `hdmi1`, `hdmi2`, `vol_up`, `vol_down`, `mute`, `play`, `pause`, `red`, `green`, `blue`, `yellow`, `0-9`, `input`, `up`, `down`, `left`, `right`, `enter`

---


**Turn on TV-1 via MQTT:**

```
mosquitto_pub -h localhost -t "sony/tv/TV-1/cmd/power_on" -m "true"
```
---

**Set volume to 25:**

```mosquitto_pub -h localhost -t "sony/tv/TV-1/cmd/vol_set" -m '{"level":25}'
```

---

**Press the “Home” IRCC button:**
```mosquitto_pub -h localhost -t "sony/tv/TV-1/ircc/home" -m "true"
```

**Subscribe to volume updates:**
```mosquitto_sub -h localhost -t "sony/tv/TV-1/status/volume"
```

