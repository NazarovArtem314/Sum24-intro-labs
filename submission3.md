# Lab 3: Version Control
## Task 2: Practice with Git Reset Command

1. **Create a New Branch:**
    ```sh
     git checkout -b git-reset-practice
     ```

2. **Create a series of commits**:
     ```sh
     echo "First commit" >> file.txt
     git add file.txt
     git commit -m "First commit"
     
     echo "Second commit" >> file.txt
     git add file.txt
     git commit -m "Second commit"
     
     echo "Third commit" >> file.txt
     git add file.txt
     git commit -m "Third commit"
     ```

3. **Task 1: Understanding Version Control Systems**
    * **Last commit hash**
        ```sh
        git log -1
        ```
        ```console
        commit 2474eea2283a58adcbeeef7a6c76c494bca50029 (HEAD -> git-reset-practice)
        Author: NazarovArtem314 <nazarov.artem314@gmail.com>
        Date:   Tue Jun 25 14:48:38 2024 +0300
    
        Third commit
        ```
    * **Output commit contents and properties**
        ```sh
        git cat-file -p 2474eea2283a58adcbeeef7a6c76c494bca50029
        ```
        ```console
        tree cc05bb19569e1baf648e930211eb489e15e7b03e
        parent 11a1177718055f34c6cfbba3caf589c9bac3958f
        author NazarovArtem314 <nazarov.artem314@gmail.com> 1719316118 +0300
        committer NazarovArtem314 <nazarov.artem314@gmail.com> 1719316118 +0300
        gpgsig -----BEGIN SSH SIGNATURE-----
         U1NIU0lHAAAAAQAAADMAAAALc3NoLWVkMjU1MTkAAAAgcIhZaQLAAsiEjEiTHLlvCkTBhT
         nLOd+gre9Nodl/yTYAAAADZ2l0AAAAAAAAAAZzaGE1MTIAAABTAAAAC3NzaC1lZDI1NTE5
         AAAAQG2lYlleMm619oVS4R9AO1+SdlrQrhoAAvt0Enj/HEzCaoffYt/1Rht0Sr4Xbv5ZjC
         WxYOJRm36j0a7XAUb+VQI=
         -----END SSH SIGNATURE-----
        
        Third commit
        ```
    * **Output tree contents and properties**
        ```sh
        git cat-file -p cc05bb19569e1baf648e930211eb489e15e7b03e
        ```
        ```console
        100644 blob ede183da8ef201e5f5737eea502edc77fd8a9bdc    README.md
        100644 blob e91bd8c09b1fcf5281b331cf1beb8be67a24e8b4    URtwerk.gif
        100644 blob 5b3c010a011b95052efe998176ef18ca8efd4adf    file.txt
        100644 blob c9ac9e3d62c27867db68fd880d6e3dc531f8d31f    index.html
        100644 blob c54a520ec380d5cc77c55f2e40fe921fc5580de5    lab1.md
        100644 blob 1b99cc0044f93f556a0f6a599c7edf2f33f4944a    lab2.md
        100644 blob f20554f4d07bc93986c0024d66b5d98be7c487cb    lab2_status.png
        100644 blob 2f8463cc188ec6ca69ae7a0f98d38e132280becb    lab3.md
        100644 blob d66a6867f90e48f6f44d9d80821aa1d866a24882    lab4.md
        100644 blob 2ff5995a25b74c9c02a143c09a9601ce66001a9f    lab5.md
        100644 blob 793bb19cd158fae333205f524eba5adc16718c58    lab6.md
        100644 blob ddb182f5a4382632e01d45f485e8ffc9722e359b    submission1.md
        100644 blob 39e4e66da5882ebe3f088364a7808438a9ef536c    submission2.md
        ```
    * **Output blob contents and properties**
        ```sh
        git cat-file -p 5b3c010a011b95052efe998176ef18ca8efd4adf
        ```
        ```console
        First commit
        Second commit
        Third commit
        ```

4. **Explore Advanced Reset and Reflog Usage**
    + **file.txt before reset**
        ```sh
        git show
        ```
        ```console
        commit 2474eea2283a58adcbeeef7a6c76c494bca50029 (HEAD -> git-reset-practice)
        Author: NazarovArtem314 <nazarov.artem314@gmail.com>
        Date:   Tue Jun 25 14:48:38 2024 +0300
        
            Third commit
        
        diff --git a/file.txt b/file.txt
        index 6a3adff..5b3c010 100644
        --- a/file.txt
        +++ b/file.txt
        @@ -1,2 +1,3 @@
         First commit
         Second commit
        +Third commit
        ```
    + **file.txt after soft reset**
        ```sh
        git reset --soft HEAD~1
        git show
        ```
        ```console
        Author: NazarovArtem314 <nazarov.artem314@gmail.com>
        Date:   Tue Jun 25 14:48:11 2024 +0300
        
            Second commit
        
        diff --git a/file.txt b/file.txt
        index 6eaf244..6a3adff 100644
        --- a/file.txt
        +++ b/file.txt
        @@ -1 +1,2 @@
         First commit
        +Second commit
        ```
        contents of file.txt:
        ```
        First commit
        Second commit
        Third commit
        ```
    + **file.txt after hard reset**
        ```sh
        git reset --hard HEAD~1
        git show
        ```
        
        ```
        HEAD is now at 3901752 First commit
        
        commit 390175207f6edb979e286f5f20ca0af4cd099e49 (HEAD -> git-reset-practice)
        Author: NazarovArtem314 <nazarov.artem314@gmail.com>
        Date:   Tue Jun 25 14:47:25 2024 +0300
        
            First commit
        
        diff --git a/file.txt b/file.txt
        new file mode 100644
        index 0000000..6eaf244
        --- /dev/null
        +++ b/file.txt
        @@ -0,0 +1 @@
        +First commit
        ```
        
        contents of file.txt:
        ```
        First commit
        ```

    + **file.txt after hard reflog reset**
        use reflog
        ```sh
        git reflog
        ```
        ```
        3901752 (HEAD -> git-reset-practice) HEAD@{0}: reset: moving to HEAD~1
        11a1177 HEAD@{1}: reset: moving to HEAD~1
        2474eea HEAD@{2}: commit: Third commit
        11a1177 HEAD@{3}: commit: Second commit
        3901752 (HEAD -> git-reset-practice) HEAD@{4}: commit: First commit
        5d21350 (origin/master, origin/HEAD, master) HEAD@{5}: checkout: moving from master to git-reset-practice
        5d21350 (origin/master, origin/HEAD, master) HEAD@{6}: pull: Fast-forward
        74e5427 HEAD@{7}: commit: Lab2 submission
        19f2ff9 HEAD@{8}: commit: site and UR
        66d30c2 HEAD@{9}: commit: Your signed commit message
        44a900d HEAD@{10}: clone: from https://github.com/NazarovArtem314/Sum24-intro-labs.git
        ```
        use restore --hard with hash from reflog
        ```sh
        git reset --hard 2474eea
        ```
        ```
        HEAD is now at 2474eea Third commit
        ```
        use reflog
        ```sh
        git reflog
        ```
        ```
        2474eea (HEAD -> git-reset-practice) HEAD@{0}: reset: moving to 2474eea
        3901752 HEAD@{1}: reset: moving to HEAD~1
        11a1177 HEAD@{2}: reset: moving to HEAD~1
        2474eea (HEAD -> git-reset-practice) HEAD@{3}: commit: Third commit
        11a1177 HEAD@{4}: commit: Second commit
        3901752 HEAD@{5}: commit: First commit
        5d21350 (origin/master, origin/HEAD, master) HEAD@{6}: checkout: moving from master to git-reset-practice
        5d21350 (origin/master, origin/HEAD, master) HEAD@{7}: pull: Fast-forward
        74e5427 HEAD@{8}: commit: Lab2 submission
        19f2ff9 HEAD@{9}: commit: site and UR
        66d30c2 HEAD@{10}: commit: Your signed commit message
        44a900d HEAD@{11}: clone: from https://github.com/NazarovArtem314/Sum24-intro-labs.git
        ```
        use show
        ```sh
        git show
        ```
        ```
        commit 2474eea2283a58adcbeeef7a6c76c494bca50029 (HEAD -> git-reset-practice)
        Author: NazarovArtem314 <nazarov.artem314@gmail.com>
        Date:   Tue Jun 25 14:48:38 2024 +0300
        
            Third commit
        
        diff --git a/file.txt b/file.txt
        index 6a3adff..5b3c010 100644
        --- a/file.txt
        +++ b/file.txt
        @@ -1,2 +1,3 @@
         First commit
         Second commit
        +Third commit
        ```
        contents of file.txt:
        ```
        First commit
        Second commit
        Third commit
        ```
        
5. Explanation of the reset and reflog process

    + The git reset --soft command is used to reset HEAD to a specific commit, leaving changes to the working directory and index intact. This means that any changes made after the specified commit will remain in the index and can be committed in a new commit.

    + The git reset --hard command is used to reset HEAD to a specific commit, whereby changes to the working directory, index, and commit history will be removed and replaced with the state of the specified commit. This means that any unindexed changes to the working directory will be lost without being recoverable.
    
    + The git reflog command shows a history of all pointer movement activities (such as HEAD or branches) in the Git repository. 

