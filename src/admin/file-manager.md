# File Manager

The **File Manager** provides a powerful interface for navigating and managing files stored in the object store. It is divided into three primary sections to give users a full view of the storage structure, contents, and activity logs.

The **File Manager** is designed to be used by administrators of a system to identify and delete large files that are no longer required to preserve disk space.

> It is important to note that any manual file deletions via this screen can cause data loss and operational failure. Caution should be taken to ensure the files to be deleted are safe to be deleted.

---

## 🧭 Overview

At the top-right corner of the File Manager page, users can view:

- **Used Space Indicator**: A visual representation showing the percentage of space used in the object store.
- **Refresh Button**: Refresh the current view and sync the latest state of the file system.
- **Documentation Link**: Directs to this help page for guidance on usage.

---

## 📁 Navigation

- The **left pane** features a **directory tree structure**, allowing users to explore buckets and subdirectories within the object store.
- Just above this pane, an **interactive breadcrumb trail** shows the current path and allows quick navigation up the directory hierarchy.

---

## 📂 Tabs

The main panel content changes based on the tab selected:

### 1. **File Browser**
Displays the files and folders within the selected bucket. Users can:

- View file names, sizes, and modification dates.
- Perform operations like viewing, downloading, or deleting files (with restrictions).

**Deletion Confirmation Modal**:  
To prevent accidental deletion, users must type the **full file name** to confirm any delete action.

---

### 2. **Charts**
Visualizes storage usage by recursively searching for and displaying the **top 10 largest files**. Useful for identifying large storage consumers quickly.

---

### 3. **Delete Audit**
A log of deleted items including:

- **File name**
- **User** who performed the deletion
- **Timestamp**
- **Reason**

---

## 🛡️ Deletion Safety

![File Delete Confirmation](/src/assets/file-manager-confirm-delete.png)

Any delete action in the File Browser is gated behind a **confirmation modal**. The modal requires:

- Manual input of the **exact file name**
- This extra step minimizes unintentional data loss.

---
