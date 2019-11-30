### Network Searches

So people are increasingly doing searches on network data for things like T1043, "Commonly Used Ports." Like searches for LOLBins (living off the land techniques) these need to be very refined searches in order to have a useful signal to noise ratio. Here is a first pass at a set of searches for the Lateral Movement/Remote Services https://attack.mitre.org/techniques/T1021/ and Command and Control / Commonly Used Ports (https://attack.mitre.org/techniques/T1043/) techniques. Some of these include differential searches for the activity with a choice of an Internet source or destination. The reason for this is that there is not a universal set of network searches that describes normal vs. suspicious network behavior because different organizations have very different workflows and security policies. While all of these network behaviors are used by threat activity, you may need to whitelist any servers or subnets that use these ports and protocols for normal workflows.

| Name                                                        | Techniques                            | Tactics                                            | Search                                                                                                                                                                                                                                   |
|-------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Network - DNS Directly to the Internet                                | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:53 and not destination.ip: 169.254.169.254/32 and not destination.ip:127.0.0.53/32 and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                         |
| Network - FTP (File Transfer Protocol) Activity to the Internet       | Commonly Used Port                    | T1043 / Command and Control                        | (destination.port:20 or destination.port:21) and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                                                                                |
| Network - IRC (Internet Relay Chat) Protocol Activity to the Internet | Commonly Used Port                    | T1043 / Command and Control                        | (destination.port:6665 or destination.port:6666 or destination.port:6667 or destination.port:6668 or destination.port:6669) and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16 |
|Network - NAT Traversal Port Activity                                 | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:4500                                                                                                                                                                                                                    |
| Network - Port 26 Activity                                            | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:26                                                                                                                                                                                                                      |
| Network - Port 8000 Activity                                          | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:8000                                                                                                                                                                                                                    |
| Network - Port 8000 Activity to the Internet                          | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:8000 and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                                                                                                       |
| Network - PPTP (Point to Point Tunneling Protocol) Activity           | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:1723                                                                                                                                                                                                                    |
| Network - Proxy Port Activity to the Internet                         | Commonly Used Port                    | T1043 / Command and Control                        | (destination.port:8080 or destination.port:3128) and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                                                                            |
| Network - RDP (Remote Desktop Protocol) from the Internet             | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:3389 and not source.ip:10.0.0.0/8 and not source.ip:172.16.0.0/12 and not source.ip:192.168.0.0/16                                                                                                                      |
| Network - RDP (Remote Desktop Protocol) to the Internet               | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:3389 and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                                                                                                       |
| Network - RPC (Remote Procedure Call) from the Internet               | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:135 and not source.ip:10.0.0.0/8 and not source.ip:172.16.0.0/12 and not source.ip:192.168.0.0/16                                                                                                                       |
| Network - RPC (Remote Procedure Call) to the Internet                 | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:135 and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                                                                                                        |
| Network - SMB (Windows File Sharing) Activity to the Internet         | Commonly Used Port                    | T1043 / Command and Control                        | (destination.port:139 or destination.port:445) and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                                                                              |
| Network - SMTP to the Internet                                        | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:25 and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                                                                                                         |
| Network - SQL Server Port Activity to the Internet                    | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:1433 and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                                                                                                       |
| Network - SSH (Secure Shell) from the Internet                        | Lateral Movement; Command and Control | T1021 / Remote Services; T1043, Commonly Used Port | destination.port:22 and not source.ip:10.0.0.0/8 and not source.ip:172.16.0.0/12 and not source.ip:192.168.0.0/16                                                                                                                        |
| Network - SSH (Secure Shell) to the Internet                          | Lateral Movement; Command and Control | T1021 / Remote Services; T1043, Commonly Used Port | destination.port:22 and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                                                                                                         |
| Network - Telnet Port Activity                                        | Commonly Used Port                    | T1043 / Command and Control                        | destination.port:23                                                                                                                                                                                                                      |
| Network - Tor Activity to the Internet                                | Commonly Used Port                    | T1043 / Command and Control                        | (destination.port:9001 or destination.port:9030) and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                                                                            |
| Network - VNC (Virtual Network Computing)  From the Internet          | Lateral Movement                      | T1021 / Remote Services                            | destination.port:5800 and not source.ip:10.0.0.0/8 and not source.ip:172.16.0.0/12 and not source.ip:192.168.0.0/16                                                                                                                      |
| Network - VNC (Virtual Network Computing)  To the Internet            | Lateral Movement                      | T1021 / Remote Services                            | destination.port:5800 and not destination.ip:10.0.0.0/8 and not destination.ip:172.16.0.0/12 and not destination.ip:192.168.0.0/16                                                                                                       |