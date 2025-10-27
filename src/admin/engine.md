# 🧠 Engine Overview

The **Engine** page provides a live operational snapshot of all active automation events within our environment. It serves as the central monitoring hub for bot status, queue activity, workflow execution, and event tracking.

---

## ⚙️ Bot Overview

Each bot listed under the **Engine** section represents a separate running automation instance.  
For each bot, the following key details are displayed:

| Field | Description |
|-------|--------------|
| **Name** | The unique identifier or hostname for the bot. |
| **Status** | Indicates whether the bot is running or stopped. It shows separate statuses for *Stateless* and *GUI* modes. |
| **Version** | Displays the bot versions for both Stateless and GUI services. |
| **UUID / RunID** | Unique identifiers used to track the current or most recent execution session. |
| **User** | The user account or service identity under which the bot is executing. |

## Examples

### 🟢 Running Bots
- `Bot-0002` and `Bot-0004` are currently **running** with both Stateless and GUI services active.  
- `Bot-0001` is also **running** but only with a GUI service installed, indicating a healthy state.

### 🔴 Stopped Bots
- If a bot is stopped, for example, seeing `Bot-0003` is currently **stopped**, meaning their automation services are not active and will be unable to complete any tasks.

---

## ⏳ Bot Queue

The **Bot Queue** tab tracks all pending and in-progress jobs awaiting execution by available bots.  
This queue shows the task distribution across bots. When bot pooling is enabled in jobs, this will show how we minimise idle time and optimise allocations.

---

## 🔁 Workflows

The **Workflows** section displays the automation processes currently running in the engine.  
Each workflow includes:
- EngineID   
- Current execution status.
- Duration and recent activity timestamps (Created date) 

This view helps ensure that long-running automations are monitored and that any stalled workflows can be identified quickly.

---

## 📅 Events

The **Events** section tracks active events being processed:

This live event tracking counter enables system administrators to maintain transparency and respond promptly to issues or anomalies.

---

## 🤖 Summary

This centralised view ensures visibility into the performance of your workflows, allows for faster debugging of issues, and helps to determine efficient workload distribution across the platform.
