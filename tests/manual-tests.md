# Manual Test Cases from KubeVirt Velero Plugin

---

## 1. VM Backup with Backend Storage PVC

**Steps:**
1. Create a VM using a backend storage PVC (e.g., persistent UEFI state).
2. Start the VM and confirm PVC is mounted and active.
3. Run a Velero backup including this VM.
4. Delete the VM and the PVC.
5. Perform a Velero restore.
6. Verify that the VM and the backend PVC are restored.
7. Start the VM and verify it boots and uses the old state.

**Expected Result:**
- VM and backend PVC restored.
- Persistent data preserved.
- VM starts without errors.

**Actual Result:**  
_(To be filled by tester.)_

---

## 2. VM Backup with Access Credentials

**Steps:**
1. Create a Secret or ConfigMap with credentials.
2. Attach to a VM via accessCredentials.
3. Start VM and verify credential injection.
4. Backup the VM with Velero.
5. Delete VM and credential source.
6. Restore from backup.
7. Verify Secret and VM are restored, credentials functional.

**Expected Result:**
- VM and credential Secret restored.
- Credentials work (e.g., SSH login).

**Actual Result:**  
_(To be filled by tester.)_

---

## 3. VM Backup with Hotplug Disk

**Steps:**
1. Create a VM and start it.
2. Create a PVC and hotplug into running VM.
3. Confirm disk is attached and write test data.
4. Backup VM with Velero.
5. Delete VM and hotplugged PVC.
6. Restore from Velero backup.
7. Confirm PVC and VM are back, data intact.

**Expected Result:**
- VM and hotplugged disk restored.
- Disk attached, data preserved.

**Actual Result:**  
_(To be filled by tester.)_

---

## 4. VM Backup with Instancetype & Preference (Namespace-scoped)

**Steps:**
1. Create namespaced instancetype and preference CRs.
2. Create VM referencing these.
3. Backup the VM with Velero.
4. Delete the VM, instancetype, and preference.
5. Restore from backup.
6. Verify CRs and VM are restored.
7. Start VM, confirm it matches original specs.

**Expected Result:**
- Instancetype/preference CRs restored.
- VM config matches original.

**Actual Result:**  
_(To be filled by tester.)_

---

## 5. VM Backup with Instancetype & Preference (Cluster-scoped)

**Steps:**
1. Create ClusterInstancetype and ClusterPreference.
2. Create VM referencing those.
3. Backup the VM (CRs not backed up).
4. Delete only VM (keep CRs).
5. Restore VM from backup.
6. Confirm it works with existing cluster CRs.

**Expected Result:**
- VM restored.
- References valid cluster-scoped CRs.

**Actual Result:**  
_(To be filled by tester.)_

---

## 6. DataVolume-Only Backup Restoration (Negative Test)

**Steps:**
1. Create DV that imports data.
2. Backup only the DV (no volume snapshots).
3. Delete DV and PVC.
4. Restore from backup.
5. Observe DV re-imports from source.
6. Verify final content matches original.

**Expected Result:**
- DV restored and re-imports.
- Data matches original source.

**Actual Result:**  
_(To be filled by tester.)_

---
