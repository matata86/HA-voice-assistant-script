# Home Assistant Custom Scripts

This repository contains custom scripts for Home Assistant that extend its functionality. These scripts are designed to simplify and automate various tasks, such as controlling devices, fetching calendar events, and managing a vacuum cleaner.

---

## Scripts Overview

### 1. **[AI] create_calendar_event**
**Description:**  
Creates a calendar event for a specific calendar entity.

**Fields:**  
| Field            | Description                          | Example               |
|-------------------|--------------------------------------|-----------------------|
| `summary`         | The summary or title for the event. | `Meeting`             |
| `start_date_time` | Start time of the event.            | `2025-12-31 10:00:00` |
| `end_date_time`   | End time of the event.              | `2025-12-31 11:00:00` |

**Usage:**  
Copy the script into your `scripts.yaml` or add it as a standalone script. Customize the entity ID and use it to schedule events.

---

### 2. **[AI] set_temperature_entity**
**Description:**  
Sets the temperature for a specific climate device.

**Fields:**  
| Field         | Description                                    | Example             |
|---------------|------------------------------------------------|---------------------|
| `entityid`    | The entity ID of the climate device to update. | `thermo_livingroom` |
| `temperature` | The temperature (between 0 and 30) to set.     | `20`                |

**Usage:**  
Add the script to your Home Assistant configuration and call it with the required `entityid` and `temperature`.

---

### 3. **[AI] vacuum_clean_room**
**Description:**  
Starts vacuuming in a specific room based on the room name.

**Fields:**  
| Field   | Description                                                      | Example  |
|---------|------------------------------------------------------------------|----------|
| `room`  | The name of the room to clean (e.g., Bedroom, Kitchen, Office).  | `Office` |

**Dependencies:**  
- **Home Assistant Helper:** Create an `input_number` entity named `input_number.vacuum_clean_area`.
- **Node-RED Flow:** Import the provided Node-RED flow to handle room ID mapping and segment cleaning.

**Rooms and IDs:**  
| Room Name       | Room ID |
|------------------|---------|
| Bedroom          | 20      |
| Living room      | 19      |
| Kitchen          | 22      |
| Lobby            | 17      |
| Office           | 21      |
| Kids room        | 16      |
| Bathroom         | 100     |
| Balcon           | 0       |

**Usage:**  
Call the script with the desired room name. Node-RED will trigger the vacuum cleaner for the specified room.

---

### 4. **[AI] get_calendar_events**
**Description:**  
Fetches and lists calendar events for a specified date range.

**Fields:**  
| Field       | Description                                                              | Example                  |
|-------------|--------------------------------------------------------------------------|--------------------------|
| `start_date`| Start of the period (ISO format datetime string). Required.              | `2025-01-19T08:00:00`    |
| `end_date`  | End of the period (ISO format datetime string). Required.                | `2025-01-19T18:00:00`    |

**Functionality:**  
- Retrieves events from a specified calendar entity (`calendar.diar` by default).
- Lists events in the format: `HH:MM Event Title`.
- If no events are found, returns "No events".

**Usage:**  
Copy the script into your `scripts.yaml` and invoke it with `start_date` and `end_date`.

---

## Setup Instructions

1. **Script Installation:**
   - Copy the `.yaml` files from this repository to your Home Assistant configuration.
   - Place them in the `scripts.yaml` or use a separate directory for custom scripts.

2. **Node-RED Setup (for vacuum scripts):**
   - Import the provided Node-RED flow for managing room cleaning.

3. **Entities Required:**
   - `calendar.diar`: Calendar entity for event-related scripts.
   - `input_number.vacuum_clean_area`: Helper for vacuum room selection.

4. **Adjustments:**
   - Replace placeholder entity IDs with your actual device/entity IDs in the scripts.

---

## Contribution
Feel free to open issues or create pull requests for improvements or new scripts.

---

## License
This repository is licensed under the MIT License.
