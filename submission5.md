# **Lab 5: GitOps & SRE Lab**
---
## **Task 1: Key Metrics for SRE and SLAs**
1. **Monitor System Resources**:
    - **CPU**: 
        1. firefox **5.9%**
        2. gnome-system-monitor **2.0%**
        3. gnome-shel **2.0%**
    - **memory**:
        1. firefox **9.1%**
        2. telegram **5.6%**
        3. vscode **4.5%**
    - **I/O**:
        1. firefox **207 kb/s**
        2. telegram **94 kb/s**
        3. vscode **46 kb/s**
2. **Disk Space Management**:
    Command:
    ```
    sudo du -hS /var | sort -rh | head -n 3
    ```
    Output:
    ```
    1,3G	/var/lib/snapd/cache
    1011M	/var/lib/snapd/snaps
    598M	/var/lib/snapd/seed/snaps
    ```
