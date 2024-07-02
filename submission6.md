# **Lab 6: Operating Systems & Networking Lab**
---
## **Task 1: Operating System Analysis**
-   
    ```
    systemd-analyze
    ```
    
    ```
    Startup finished in 4.151s (kernel) + 3min 24.081s (userspace) = 3min 28.232s 
    graphical.target reached after 2min 7.488s in userspace
    ```
-   
    ```
    systemd-analyze blame | head
    ```
    
    ```
    1min 26.955s plymouth-quit-wait.service                           
    1min 19.749s apt-daily-upgrade.service                            
     29.131s containerd.service                                   
     27.183s snapd.seeded.service                                 
     24.584s snapd.service                                        
     24.109s networkd-dispatcher.service                          
     17.975s dev-sda5.device                                      
     17.349s udisks2.service                                      
     16.724s gpu-manager.service                                  
     13.733s NetworkManager.service  
    ```
-   
    ```
    uptime
    ```
    
    ```
     21:47:15 up 1 day, 16:23,  1 user,  load average: 0,47, 1,02, 1,07
    ```
    
-   
    ```
    w
    ```
    
    ```
    21:47:18 up 1 day, 16:23,  1 user,  load average: 0,47, 1,02, 1,07
    USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
    dd       :0       :0               Пн17   ?xdm?   6:39m  0.01s /usr/lib/gdm3/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=ubuntu /usr/bin/gnome-session --s
    ```
- userspace takes a very long time to load.
- the laptop has been switched on for one day.
- plymouth-quit-wait.service and apt-daily-upgrade.service are the most time-consuming services.

## **Task 2: Networking Analysis**
- **traceroute**
    ```
    traceroute google.com
    ```
    ```
    traceroute to google.com (216.239.38.120), 30 hops max, 60 byte packets
     1  _gateway (10.91.48.1)  12.512 ms  12.408 ms  12.452 ms
     2  10.252.6.1 (10.252.6.1)  12.447 ms  12.442 ms  12.449 ms
     3  1.123.18.84.in-addr.arpa (84.18.123.1)  22.460 ms  22.423 ms  22.443 ms
     4  188.170.164.138 (188.170.164.138)  16.937 ms  16.936 ms  16.990 ms
     5  * * *
     6  * * *
     7  * * *
     8  83.169.204.113 (83.169.204.113)  21.193 ms 83.169.204.115 (83.169.204.115)  21.167 ms 83.169.204.119 (83.169.204.119)  20.975 ms
     9  37.29.3.250 (37.29.3.250)  36.538 ms 72.14.222.181 (72.14.222.181)  20.888 ms 178.176.152.61 (178.176.152.61)  20.837 ms
    10  108.170.250.51 (108.170.250.51)  41.525 ms 192.178.241.61 (192.178.241.61)  24.261 ms *
    11  192.178.241.148 (192.178.241.148)  21.822 ms 192.178.241.66 (192.178.241.66)  21.704 ms 142.251.49.158 (142.251.49.158)  34.893 ms
    12  216.239.48.224 (216.239.48.224)  52.154 ms 142.250.238.214 (142.250.238.214)  40.974 ms 72.14.234.54 (72.14.234.54)  66.060 ms
    13  66.249.95.224 (66.249.95.224)  43.568 ms 216.239.43.20 (216.239.43.20)  48.529 ms 142.251.237.146 (142.251.237.146)  35.978 ms
    14  216.239.47.165 (216.239.47.165)  35.978 ms 216.239.47.173 (216.239.47.173)  36.621 ms 216.239.57.229 (216.239.57.229)  39.504 ms
    15  * * *
    16  * * *
    17  * * *
    18  * * *
    19  * * *
    20  * * *
    21  * * *
    22  * * *
    23  any-in-2678.1e100.net (216.239.38.120)  37.442 ms *  37.307 ms
    ```
- **dig**
    ```
    dig google.com
    ```
    ```
    ; <<>> DiG 9.16.48-Ubuntu <<>> google.com
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29125
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1
    
    ;; OPT PSEUDOSECTION:
    ; EDNS: version: 0, flags:; udp: 65494
    ;; QUESTION SECTION:
    ;google.com.			IN	A
    
    ;; ANSWER SECTION:
    google.com.		84917	IN	CNAME	forcesafesearch.google.com.
    forcesafesearch.google.com. 7199 IN	A	216.239.38.120
    
    ;; Query time: 4 msec
    ;; SERVER: 127.0.0.53#53(127.0.0.53)
    ;; WHEN: Tue Jul 02 22:26:25 MSK 2024
    ;; MSG SIZE  rcvd: 85
    ```
- Need 23 hops to the site
- The google search page can be accessed at ip 216.239.38.120.
