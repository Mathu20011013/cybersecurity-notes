
purpose of the wireshark
- detecting and troubleshooting the network problems.
- detecting security anomalies
- investigate and learn protocol details

- its not the IDS. only allow to discover and investigate the packets in depth. 
- it  doesn't modify the packets, detecting anomaly or network problems highly rely on the analyst knowledge and investigation skills.

| Component                       | Function                                                      | Easy Recall                    |
| ------------------------------- | ------------------------------------------------------------- | ------------------------------ |
| **Toolbar**                     | Tools for capture, filter, sort, export, merge                | Main control panel             |
| **Display Filter Bar**          | Search and filter packets                                     | Find specific traffic          |
| **Recent Files**                | Shows previously opened PCAP files                            | Reopen quickly                 |
| **Capture Filter & Interfaces** | Select network interface (eth0, lo) and apply capture filters | Choose where & what to capture |
| **Status Bar**                  | Shows packet count, tool status, profile info                 | Quick summary                  |

After upload the file in the wire shark we get 3 panes,
- packet list pane - we can see all the packets here
- packet details panel -  show the details of the selected packet 
- packet bytes pane - hex and decoded ascii representation of the selected packet. 

## Packet Dissection


**breaking a network packet into parts to analyze its details**
also known as protocol dissection
