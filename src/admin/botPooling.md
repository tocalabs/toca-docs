# Bot Pooling

## Overview

Bot Pooling provides a mechanism to group, organize, and manage your bot resources effectively. By creating pools, you can logically segment bots based on their capabilities or intended use, streamlining assignment and utilization.

![image](https://github.com/user-attachments/assets/107b6189-d0f2-4ed7-993d-9e314bf0148a)

Each Bot Pool is assigned a specific **Type**, which dictates the nature of the bots it can contain and influences how jobs are allocated to that pool. You can group your bots however makes sense for you, selecting all bots, or a sub-section, according to your needs.

## Key Concepts

* **Bot Pool:** A named collection of bot resources.
* **Pool Type:** A mandatory attribute assigned during pool creation that defines the bots within the pool.

## Pool Types

When creating a Bot Pool, you must select one of the following types:

1.  **Gui (Graphical User Interface):**
    * **Purpose:** Designed for bots that need to interact with graphical user interfaces (e.g., desktop applications, specific web browsers requiring screen interaction).
    * **Characteristics:** These bots typically require a dedicated user session, may have specific operating system or screen resolution requirements, and often cannot run multiple instances concurrently on the same resource.
    * **Use Case:** Automating tasks using legacy desktop software, complex web UI testing, and attended automation scenarios.

2.  **Stateless:**
    * **Purpose:** Intended for bots performing background tasks, API interactions, data processing, or other operations that do not require direct interaction with a graphical user interface.
    * **Characteristics:** These bots are often more lightweight, can run many jobs in parallel, and can be scaled more easily. They don't maintain session state between executions in the same way a GUI bot does.
    * **Use Case:** Processing data feeds, interacting with web services (APIs), running scripts, and background system maintenance.

## Managing Bot Pools

The management of Bot Pools involves creating pools, adding/removing bots, viewing details, and deleting pools.

### 1. Creating a Bot Pool

To create a new pool:

1.  Navigate to the Bot Pools Tab within the Bot section in Admin.
2.  Select the `+` option to Create a New Pool.
3.  Provide a unique and descriptive **Name** for the pool.
4.  **Crucially, select the Pool Type:** Choose either `Gui` or `Stateless` based on the intended function of the bots that will reside in this pool.
5.  Optionally, select the bots to be added to the pool.
6.  Create the new pool.

### 2. Adding / Removing Bots to/from a Pool

Once a pool exists, you can remove and add bots to it:

1.  Select the desired Bot Pool from the list.
2.  Select the bot(s) you wish to remove/add to this specific pool.
    * *Note: Only bots of a single type can be added to a pool.(Gui/Stateless).*
3.  Update the pool. The selected bots are now part of the pool and available to be used in Activities.

### 3. Viewing Pool Details

You can typically select any existing pool to view its details, including:

* Pool Name
* Pool Type (`Gui` or `Stateless`)
* List of bots currently assigned to the pool

### 4. Deleting a Bot Pool

If a pool is no longer needed:

1.  Select the Bot Pool you wish to delete.
2.  Find the "Delete Pool" which uses the bin icon option.
3.  Confirm the deletion. The pool will be permanently removed. Please understand the consequences before confirming, **Important:** All activities utilising this pool will need re-assigning.

# Selection of Pools

The Bot Pooling feature introduces a new way to manage and allocate bots to activities within a workflow. Here's how it works:

## Key Concepts

- Bot Pools can now be assigned to activities.
- The bot selected at queue time will remain assigned during the execution of that activity.
- A single, consistent bot from each pool runs all tasks associated with that pool in a given job.

![image](https://github.com/user-attachments/assets/78556f24-7dcd-41b7-8aa4-dc876ab2cf51)

## Allocation and Execution Logic

- Across all activities in a workflow, the system determines the minimum number of bots required to run the job.
- If a bot is unavailable, the system will attempt alternative combinations of available bots that satisfy the required pools.
- If no valid combinations remain, the job will be queued. We will then wait for bots to become available before attempting to lock the next job off the queue.

## Dynamic Bot Management

- Bots can be added or removed from pools while a job is queued.
- These changes will be picked up the next time the job queue is processed.
- Only the bots utilized during execution will be locked, allowing unused bots to remain available.

## Visibility
- The assigned pool and bot will be visible on the pipeline nodes.
- Reports will reflect the bots used, as per standard reporting functionality.

### Error Handling and Access
- If a bot becomes unavailable, the job is not cancelled immediately.
- If a user lacks access to a bot in the pool, that bot is simply skipped.
- However, if all bots within a pool are inaccessible, the job will be cancelled.

### Stateless Pools
- Stateless-type pools allow for restricted sets of bots to be used for stateless jobs.
- Bots in these pools are used in a round-robin fashion to ensure even load distribution.
