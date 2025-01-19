# HA Voice Assist Custom Scripts

This repository contains custom scripts for Home Assistant that extend its functionality. These scripts are designed to simplify and automate tasks such as controlling devices, managing calendars, controlling a vacuum cleaner, and managing a to-do list, fully optimized for voice assistants.

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
"Create a calendar event on Monday, January 20th, at 4 PM for a meeting with Mrs. Nováková."

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
"Set the temperature in the office to 23 degrees."

---

### 3. **[AI] vacuum_clean_room (Single Room)**
**Description:**  
Starts vacuuming in a single room based on the room name.

**Fields:**  
| Field   | Description                                                      | Example  |
|---------|------------------------------------------------------------------|----------|
| `room`  | The name of the room to clean (e.g., Bedroom, Kitchen, Office).  | `Office` |

**Example Command:**  
"Send the vacuum to the bedroom."

---

### 4. **[AI] vacuum_clean_multiroom**
**Description:**  
Starts vacuuming in multiple rooms sequentially, based on provided room names.

**Fields:**  
| Field   | Description                                                      | Example          |
|---------|------------------------------------------------------------------|------------------|
| `rooms` | A list of room names to clean (e.g., Bedroom, Kitchen, Office).  | `["Office", "Kitchen"]` |

**Example Command:**  
"Send the vacuum to the bedroom and kitchen."

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
"What is my schedule for Monday, January 20th?"

---

### 6. **[AI] GetItemsFromTodoList**
**Description:**  
Returns items that the user has not yet completed on their to-do or tasks list.

**Fields:**  
| Field | Description                      | Example                |
|-------|----------------------------------|------------------------|
| `name`| The name of the to-do list entity. | `my_todo_list_entity` |

**Example Command:**  
"What tasks are remaining on my to-do list?"

---

### 7. **[AI] CompleteItemOnTodoList**
**Description:**  
Marks an item on a to-do or tasks list as completed.

**Fields:**  
| Field   | Description                                | Example               |
|---------|--------------------------------------------|-----------------------|
| `name`  | The name of the to-do list entity.         | `my_todo_list_entity` |
| `item`  | The name of the item to mark as completed. | `Buy groceries`       |

**Example Command:**  
"Mark 'Buy groceries' as completed on my to-do list."

---

## Setup Instructions

### General Setup
1. **Script Installation:**
   - Copy the `.yaml` files into your Home Assistant configuration.
   - Place them in the `scripts.yaml` or use a dedicated directory.

2. **Adjustments:**
   - Replace placeholder entity IDs with your actual device/entity IDs in the scripts.

---

## Contribution

### Authors
- [matata86](https://github.com/matata86)
- [fsecko1](https://github.com/fsecko1)

Feel free to open issues or create pull requests for improvements or new scripts.

---

## License
This repository is licensed under the MIT License.
