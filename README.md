# Task-1-
Performed network reconnaissance using Nmap on Kali Linux to scan the local network (192.168.248.0/24), identify live hosts, and detect open or filtered ports. Captured packets with Wireshark, analyzed port 53 (DNS), assessed security risks, and saved results in text and HTML formats for documentation.

Task 1: Scan Your Local Network for Open Ports – Summary Steps

1. Install Nmap (if not already installed):
   sudo apt update && sudo apt install nmap -y
   
2. Find Your Local IP and Subnet:
   ip a
    IP: 192.168.248.128
    Subnet: /24 → 192.168.248.0/24

3. Run TCP SYN Scan:
   sudo nmap -sS 192.168.248.0/24

4. Scan Output Summary:
  IP Address	      Status	    Open Ports	      Service	          Remarks
  192.168.248.1	    Up	          None	             —	            All 1000 TCP ports filtered
  192.168.248.2	    Up	          53/tcp     Filtered (domain)	    Likely running DNS service
  192.168.248.254	  Up           	None	             —              All ports filtered
  192.168.248.128	  Up	          None	             —              This is the Kali machine itself

5. Wireshark (Optional):
    Start capture on eth0
    Run Nmap scan
    Filter: tcp.flags.syn == 1 && tcp.flags.ack == 0
    Save as: nmap_scan_capture.pcapng

6. Service Found:

    Port 53/tcp on 192.168.248.2 → DNS

7. Risks of Open Port 53:

    DNS amplification, cache poisoning, info leakage

8. Mitigations:

    Restrict access, disable zone transfers, update DNS software

9. Save Results:

   As text:
   sudo nmap -sS 192.168.248.0/24 -oN scan_results.txt
   
  
