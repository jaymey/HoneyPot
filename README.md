# HoneyPot
HoneyPot Data Deployed with GCloud Platform

# Deployed HoneyPots
1. cowrie: medium interaction SSH and Telnet honeypot designed to log brute force attacks and the shell interaction performed by the attacker.

2. p0f: tool that utilizes an array of sophisticated, purely passive traffic fingerprinting mechanisms to identify the players behind any incidental TCP/IP communications (often as little as a single normal SYN) without interfering in any way.

3. snort: open source intrusion prevention system capable of real-time traffic analysis and packet logging.

4. suricata: capable of real time intrusion detection (IDS), inline intrusion prevention (IPS), network security monitoring (NSM) and offline pcap processing.

# Issues Encountered
I had completed the lab portion a week prior, and since Dionaea appears to be an exceptionally popular honeypot, I had collected close to 4,000,000 samples, making the session file too large to work with and examine, as well as completely drowning out any data collected by other honeypots. 

To resolve this I decided to drop my mhn database collection and remove the dionaea honeypot. By doing this, I would have a smaller more manageable dataset that would contain a variety of data from different honeypots.

# Data Collected
Attacks Logged:
- cowrie: 320

If we take a look at the cowrie data, we see that the logs contain authorization attempts using a login and password. These attacks repeat multiple times and most likely indicate the brute force login attacks that are perpetrated on the honeypot. Some entries also contain a data string which appear to be hex encoded attachments, most likely containing malware to execute once the login attempt was successful.
  
- p0f: 3300

The p0f logs all contain source ips of where the attacks originated from as well as the source port. This data can help to identify the attackers by finding any type of repeated data between logs, such as source ip.

- snort: 901

The snort logs contain similar information to the p0f logs, but also include a signature field which contains a quick snippet that identifies the type of attack that was attempted such as: "ET SCAN Suspicious inbound to MSSQL port 1433", "ET SCAN Sipvicious User-Agent Detected (friendly-scanner)", and "ET CINS Active Threat Intelligence Poor Reputation IP TCP group 81". These signatures help us to categorize the traffic that passes through the honeypot and logs the packets.

- suricata: 2904

The suricata logs also contain similar information to the snort logs, but they act as a real-time intrusion detection and prevention system, so they log similar information regarding the signature field, and try to categorize the attacks. The signatures are very similar to the snort logs, but also contain some like "ET POLICY Python-urllib/ Suspicious User Agent". 

# Summary
This data points to some types of attacks being more popular than others, or that they are just low-interaction attacks. For example, it is clear that p0f attacks, where it simply fingerprints traffic to identify attackers will obviously collect more data by its passive scanning of TCP/IP communications, whereas cowrie attacks log brute force attacks and any shell interaction performed by the attacker, which is a high-interaction attack since it requires more work on part of the attacker.

If we take a look at the cowrie data, we see that the logs contain authorization attempts using a login and password. These attacks repeat multiple times and most likely indicate the brute force login attacks that are perpetrated on the honeypot. Some entries also contain a data string which appear to be hex encoded attachments, most likely containing malware to execute once the login attempt was successful.

# Unresolved Questions
Most of my data analysis above was the result of taking a look at what each sensor detects and logs and trying to extrapolate reasonable conclusions from the data collected, as well as to what the fields in the data represent. I attempted this to the best of my ability, along with the help of google, but more information could be useful in understanding what these massive amounts of data mean and how they could be used to capture attackers, or aid in system security and intrustion prevention. 

I suppose the main unresolved question would be: "What is the most useful way I can apply this data and observed trends to my everyday life and career?"
