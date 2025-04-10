# Bot Pooling

## Overview

Bot Pooling provides a mechanism to group, organize, and manage your bot resources effectively. By creating pools, you can logically segment bots based on their capabilities or intended use, streamlining assignment and utilization.

Each Bot Pool is assigned a specific **Type**, which dictates the nature of the bots it can contain and influences how jobs are allocated to that pool.

## Key Concepts

* **Bot Pool:** A named collection of bot resources.
* **Pool Type:** A mandatory attribute assigned during pool creation that defines the fundamental characteristic of the bots within the pool. This helps in matching tasks to appropriate resources.

## Pool Types

When creating a Bot Pool, you must select one of the following types:

1.  **Gui (Graphical User Interface):**
    * **Purpose:** Designed for bots that need to interact with graphical user interfaces (e.g., desktop applications, specific web browsers requiring screen interaction).
    * **Characteristics:** These bots typically require a dedicated user session, may have specific operating system or screen resolution requirements, and often cannot run multiple instances concurrently on the same resource.
    * **Use Case:** Automating tasks in legacy desktop software, complex web UI testing, attended automation scenarios.

2.  **Stateless:**
    * **Purpose:** Intended for bots performing background tasks, API interactions, data processing, or other operations that do not require direct interaction with a graphical user interface.
    * **Characteristics:** These bots are often more lightweight, can run many jobs in parallel, and can be scaled more easily. They don't maintain session state between executions in the same way a GUI bot does.
    * **Use Case:** Processing data feeds, interacting with web services (APIs), running scripts, background system maintenance.

## Managing Bot Pools

Basic management of Bot Pools involves creating pools, adding/removing bots, viewing details, and deleting pools.

### 1. Creating a Bot Pool

To create a new pool:

1.  Navigate to the Bot Pool management section in your interface.
2.  Select the option to "Create New Pool" (or similar).
3.  Provide a unique and descriptive **Name** for the pool.
4.  **Crucially, select the Pool Type:** Choose either `Gui` or `Stateless` based on the intended function of the bots that will reside in this pool.
5.  Save the new pool.

### 2. Adding Bots to a Pool

Once a pool exists, you can populate it with available bot resources:

1.  Select the desired Bot Pool from the list.
2.  Select the bot(s) you wish to add to this specific pool.
    * *Note: Only bots of a single type can be added to a pool.(Gui/Stateless).*
3.  Confirm the addition. The selected bots are now part of the pool and available to be used in Activities.

### 3. Removing Bots from a Pool

If a bot needs to be reassigned or is no longer required in a specific pool:

1.  Select the Bot Pool containing the bot(s) you wish to remove.
2.  View the list of bots currently in the pool.
3.  Select the bot(s) you want to remove.
4.  Confirm the removal.
    * *Note: This action removes the bot's association with the pool. The bot resource itself is usually **not** deleted from the system, it simply becomes unassigned from this pool.*

### 4. Viewing Pool Details

You can typically select any existing pool to view its details, including:

* Pool Name
* Pool Type (`Gui` or `Stateless`)
* List of bots currently assigned to the pool

### 5. Deleting a Bot Pool

If a pool is no longer needed:

1.  Select the Bot Pool you wish to delete.
2.  Find the "Delete Pool" option.
3.  Confirm the deletion. The pool will be permanently removed. Understand the consequences before confirming, **Important:** All activities that are utilising this pool, will need re-assigning.

---
