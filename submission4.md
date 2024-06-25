# Lab 4: Software Distribution
## Task 1: Configure and Use a Local Package Repository

1. **Create a Local Repository**:
    ```sh
    mkdir -p ~/local-apt-repo
    cp Учеба/Иннополис/DevOps/sublime-text_build-4169_amd64.deb ~/local-apt-repo/
    ```
    
2. **Generate the Package Index**:

     ```sh
     dpkg-scanpackages ~/local-apt-repo /dev/null | gzip -9c > ~/local-apt-repo/Packages.gz
     ```
     
     ```
    dpkg-scanpackages: warning: Packages in archive but missing from override file:
    dpkg-scanpackages: warning:   sublime-text
    dpkg-scanpackages: info: Wrote 1 entries to output Packages file.
     ```

3. **Add the Local Repository to Your Sources List**:

    ```sh
    echo "deb [trusted=yes] file:/home/dd/local-apt-repo ./" | sudo tee /etc/apt/sources.list.d/local-apt-repo.list
    sudo apt update
    ```
 
    ```
    deb [trusted=yes] file:/home/dd/local-apt-repo ./

    Get:1 file:/var/cuda-repo-ubuntu2004-12-2-local  InRelease [1 572 B]
    Get:2 file:/home/dd/local-apt-repo ./ InRelease
    Ign:2 file:/home/dd/local-apt-repo ./ InRelease
    Get:1 file:/var/cuda-repo-ubuntu2004-12-2-local  InRelease [1 572 B]
    Get:3 file:/home/dd/local-apt-repo ./ Release
    Ign:3 file:/home/dd/local-apt-repo ./ Release
    Get:4 file:/home/dd/local-apt-repo ./ Packages
    Ign:4 file:/home/dd/local-apt-repo ./ Packages
    Get:5 file:/home/dd/local-apt-repo ./ Translation-en
    Ign:5 file:/home/dd/local-apt-repo ./ Translation-en
    Get:6 file:/home/dd/local-apt-repo ./ Translation-en_US
    Ign:6 file:/home/dd/local-apt-repo ./ Translation-en_US
    Get:4 file:/home/dd/local-apt-repo ./ Packages                          
    Ign:4 file:/home/dd/local-apt-repo ./ Packages                          
    Get:5 file:/home/dd/local-apt-repo ./ Translation-en                    
    Ign:5 file:/home/dd/local-apt-repo ./ Translation-en                    
    Get:6 file:/home/dd/local-apt-repo ./ Translation-en_US                 
    Ign:6 file:/home/dd/local-apt-repo ./ Translation-en_US                 
    Get:4 file:/home/dd/local-apt-repo ./ Packages                          
    Ign:4 file:/home/dd/local-apt-repo ./ Packages                          
    Get:5 file:/home/dd/local-apt-repo ./ Translation-en                    
    Ign:5 file:/home/dd/local-apt-repo ./ Translation-en                    
    Get:6 file:/home/dd/local-apt-repo ./ Translation-en_US                 
    Ign:6 file:/home/dd/local-apt-repo ./ Translation-en_US                 
    Get:4 file:/home/dd/local-apt-repo ./ Packages [409 B]                  
    Get:5 file:/home/dd/local-apt-repo ./ Translation-en                    
    Ign:5 file:/home/dd/local-apt-repo ./ Translation-en                    
    Get:6 file:/home/dd/local-apt-repo ./ Translation-en_US
    Ign:6 file:/home/dd/local-apt-repo ./ Translation-en_US
    Get:5 file:/home/dd/local-apt-repo ./ Translation-en
    Ign:5 file:/home/dd/local-apt-repo ./ Translation-en
    Get:6 file:/home/dd/local-apt-repo ./ Translation-en_US
    Ign:6 file:/home/dd/local-apt-repo ./ Translation-en_US
    Get:5 file:/home/dd/local-apt-repo ./ Translation-en
    Ign:5 file:/home/dd/local-apt-repo ./ Translation-en
    Get:6 file:/home/dd/local-apt-repo ./ Translation-en_US
    Ign:6 file:/home/dd/local-apt-repo ./ Translation-en_US
    Get:5 file:/home/dd/local-apt-repo ./ Translation-en
    Ign:5 file:/home/dd/local-apt-repo ./ Translation-en
    Get:6 file:/home/dd/local-apt-repo ./ Translation-en_US
    Ign:6 file:/home/dd/local-apt-repo ./ Translation-en_US
    Ign:7 http://robotpkg.openrobots.org/packages/debian/pub focal InRelease
    Hit:8 http://ppa.launchpad.net/git-core/ppa/ubuntu focal InRelease
    Hit:9 http://security.ubuntu.com/ubuntu focal-security InRelease
    Hit:10 http://ru.archive.ubuntu.com/ubuntu focal InRelease
    Hit:11 http://robotpkg.openrobots.org/packages/debian/pub focal Release
    Get:12 http://ru.archive.ubuntu.com/ubuntu focal-updates InRelease [128 kB]
    Hit:13 https://download.docker.com/linux/ubuntu focal InRelease
    Hit:14 https://packages.microsoft.com/repos/code stable InRelease
    Get:15 https://mega.nz/linux/repo/xUbuntu_20.04 ./ InRelease [2 961 B]          
    Hit:16 http://ru.archive.ubuntu.com/ubuntu focal-backports InRelease
    Hit:18 https://librealsense.intel.com/Debian/apt-repo focal InRelease
    Hit:19 http://packages.ros.org/ros/ubuntu focal InRelease                                                                                                              
    Fetched 131 kB in 7s (19,6 kB/s)                                                                                                                                       
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    All packages are up to date.
    ```

4. **Verify the Contents of the Packages.gz File:**:

     ```sh
     zcat Packages.gz
     apt policy sublime-text
     ```
     
    ```
    Package: sublime-text
    Version: 4169
    Architecture: amd64
    Maintainer: Sublime HQ Pty Ltd <support@sublimetext.com>
    Installed-Size: 49330
    Depends: libgtk-3-0, libcurl3 | libcurl4
    Filename: /home/dd/local-apt-repo/sublime-text_build-4169_amd64.deb
    Size: 15622456
    MD5sum: 2eb9b7b1f5090088e5650229355fd302
    SHA1: 93b042aa917c49892962c41be6a72baa44092268
    SHA256: e1bac169546317f246cc58adbdd20264c78486f12112b3c9ee303aa863c38f7f
    Section: editors
    Priority: optional
    Description: Sublime Text is a sophisticated text editor for code, markup and prose
    Build-Depends: libgtk-3-0, libcurl3 | libcurl4
    
    sublime-text:
      Installed: 4169
      Candidate: 4169
      Version table:
     *** 4169 500
            500 file:/home/dd/local-apt-repo ./ Packages
            100 /var/lib/dpkg/status
     ```

5. **Install a Package from the Local Repository**:
    ```sh
    sudo apt install sublime-text
    ```
     
    ```
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Note, selecting 'sublime-text' instead of '/home/dd/Учеба/Иннополис/DevOps/sublime-text_build-4169_amd64.deb'
    The following NEW packages will be installed:
    sublime-text
    0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
    Need to get 0 B/15,6 MB of archives.
    After this operation, 50,5 MB of additional disk space will be used.
    Get:1 file:/home/dd/local-apt-repo ./ sublime-text 4169 [15,6 MB]
    Ign:1 file:/home/dd/local-apt-repo ./ sublime-text 4169
    Get:1 file:/home/dd/local-apt-repo ./ sublime-text 4169 [15,6 MB]
    Selecting previously unselected package sublime-text.
    (Reading database ... 319610 files and directories currently installed.)
    Preparing to unpack .../sublime-text_build-4169_amd64.deb ...
    Unpacking sublime-text (4169) ...
    Setting up sublime-text (4169) ...
    Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
    Processing triggers for mime-support (3.64ubuntu1) ...
    Processing triggers for hicolor-icon-theme (0.17-2) ...
    Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
    ```
    
## Task 2: Simulate Package Installation and Identify Dependencies

1. **Choose a Package to Simulate**:

     ```sh
     apt-cache showpkg sublime-text
     ```
     
     ```
    Package: sublime-text
    Versions: 
    4169 (/var/lib/apt/lists/_home_dd_local-apt-repo_._Packages) (/var/lib/dpkg/status)
     Description Language: 
                     File: /var/lib/apt/lists/_home_dd_local-apt-repo_._Packages
                      MD5: 16307a1906c33fc4b032ad0980022c14
    
    
    Reverse Depends: 
    Dependencies: 
    4169 - libgtk-3-0 (0 (null)) libcurl3 (16 (null)) libcurl4 (0 (null)) 
    Provides: 
    4169 - 
    Reverse Provides: 
     ```

2. **Simulate the Installation**:

     ```sh
     sudo apt-get install -s sublime-text
     ```
     
     ```
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    sublime-text is already the newest version (4169).
    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
     ```

3. **Analyze the Output**:
    -  Dependencies: libgtk-3-0, libcurl3, libcurl4
    -  The latest version is installed

## Task 3: Hold and Unhold Package Versions

1. **Install a Package**:

     ```sh
     sudo apt install sublime-text
     ```
     
     ```
     all sublime-text
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    sublime-text is already the newest version (4169).
    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
     ```

2. **Hold the Package**:

     ```sh
     sudo apt-mark hold sublime-text
     ```
    ```
    sublime-text set on hold.
    ```
3. **Verify the Hold Status**:

     ```sh
     apt-mark showhold
     ```

    ```
    sublime-text
    ```


4. **Unhold the Package**:

     ```sh
     sudo apt-mark unhold sublime-text
     ```
     
     ```
     Canceled hold on sublime-text.
     ```
     
5. **Verify the Unhold Status**:
     
     ```sh
     apt-mark showhold
     ```
    
    ```
    
    ```
