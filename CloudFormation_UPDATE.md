# CloudFormation Status: UPDATE_IN_PROGRESS and UPDATE_ROLLBACK_IN_PROGRESS

---

### **UPDATE_IN_PROGRESS**

**What it means:** AWS is currently **applying your changes** (creating, modifying, or deleting resources).

* **Action:** You can still manually **Cancel** this if you made a mistake.
* **End Goal:** Move forward to the new version (`UPDATE_COMPLETE`).

---

### **UPDATE_ROLLBACK_IN_PROGRESS**

**What it means:** AWS is **undoing the update** to return the stack to its last stable version. This happens because the update failed or you clicked "Cancel."

* **Action:** You **cannot stop or cancel** a rollback. You must wait for it to finish.
* **End Goal:** Return to the original state (`UPDATE_ROLLBACK_COMPLETE`).

---

**Summary for Admin:** Since you are currently in **UPDATE_ROLLBACK_IN_PROGRESS**, the stack is "locked" while it cleans itself up. Once it finishes, the environment will be back to normal, and you can try a fresh update.


