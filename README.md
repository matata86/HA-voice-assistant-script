# HA Voice assist Custom Scripts

This repository contains custom scripts for Home Assistant that extend its functionality. These scripts are designed to simplify and automate tasks such as controlling devices, managing calendars, and controlling a vacuum cleaner.

---

## Setup Overview

This repository is optimized for the following setup:

- **Speech-to-Text (STT):** Home Assistant Cloud.  
- **Text-to-Speech (TTS):** Home Assistant Cloud.  
- **Conversation Agent:** ChatGPT integrated into Home Assistant for advanced conversational capabilities.

This configuration ensures seamless voice control and natural language understanding for your smart home automation.

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

**Important Note:**  
If you are using the GPT-4o-Mini model, you must specify the exact date and time for the event. For example:
- Instead of saying: "Create an event for next Monday."
- Provide a detailed request: "Create a calendar event on Monday, January 20th, where I have a meeting with Mrs. Nováková at 4 PM."

**Example Command:**  
"Jaký je můj program v pondělí 20.1.?"

---

### 2. **[AI] set_temperature_entity**
**Description:**  
Sets the temperature for a specific climate device.

**Fields:**  
| Field         | Description                                    | Example             |
|---------------|------------------------------------------------|---------------------|
| `entityid`    | The entity ID of the climate device to update. | `thermo_livingroom` |
| `temperature` | The temperature (between 0 and 30) to set.     | `20`                |

**Example Command:**  
"Nastav teplotu v pracovně na 23 stupňů."

---

### 3. **[AI] vacuum_clean_room (Single Room)**
**Description:**  
Starts vacuuming in a single room based on the room name.

**Fields:**  
| Field   | Description                                                      | Example  |
|---------|------------------------------------------------------------------|----------|
| `room`  | The name of the room to clean (e.g., Bedroom, Kitchen, Office).  | `Office` |

**Functionality:**  
- The script directly sends a cleaning command to the vacuum cleaner for the specified room.

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

**Example Command:**  
"Pošli vysavač do ložnice."

---

### 4. **[AI] vacuum_clean_multiroom**
**Description:**  
Starts vacuuming in multiple rooms sequentially, based on provided room names.

**Fields:**  
| Field   | Description                                                      | Example          |
|---------|------------------------------------------------------------------|------------------|
| `rooms` | A list of room names to clean (e.g., Bedroom, Kitchen, Office).  | `["Office", "Kitchen"]` |

**Dependencies:**  
- **Home Assistant Helper:** Create an `input_number` entity named `input_number.vacuum_clean_area`.
- **Node-RED Flow:** Import the provided Node-RED flow to handle room ID mapping and segment cleaning.

**Functionality:**  
- Processes multiple rooms and sends cleaning commands to the vacuum cleaner for each specified room.
- Resets the helper value after the cleaning sequence is completed.

**Example Command:**  
"Pošli vysavač do ložnice a kuchyně."

---

### 5. **[AI] get_calendar_events**
**Description:**  
Fetches and lists calendar events for a specified date range.

**Fields:**  
| Field       | Description                                                              | Example                  |
|-------------|--------------------------------------------------------------------------|--------------------------|
| `start_date`| Start of the period (ISO format datetime string). Required.              | `2025-01-19T08:00:00`    |
| `end_date`  | End of the period (ISO format datetime string). Required.                | `2025-01-19T18:00:00`    |

**Example Command:**  
"Jaký je můj program v pondělí 20.1.?"

---

## Setup Instructions

### General Setup
1. **Script Installation:**
   - Copy the `.yaml` files into your Home Assistant configuration.
   - Place them in the `scripts.yaml` or use a dedicated directory.

2. **Adjustments:**
   - Replace placeholder entity IDs with your actual device/entity IDs in the scripts.

### Multi-Room Vacuum Script Setup
1. **Home Assistant Helper:**
   - Create an `input_number` entity named `input_number.vacuum_clean_area`.

2. **Node-RED Setup:**
   - Import the provided Node-RED flow.
   - Ensure the flow manages `input_number.vacuum_clean_area` for multi-room cleaning.

---

## Contribution
Feel free to open issues or create pull requests for improvements or new scripts.

---

## License
This repository is licensed under the MIT License.
