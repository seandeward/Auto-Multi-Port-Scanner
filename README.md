# __Auto Multi-Port Scanner__ - Overview
An automatic multi-port scanner. Enter FQDNs or hostnames into the local plaintext file (hostnames.txt), and it will check any open ports on those hostnames!

# How to Build and Run
This program can be run with the single python file and the external plaintext file named "hostnames.txt". No special configurations or libraries neccessary!

To run it, you only need to add hostnames to hostnames.txt (one name per line) and then run multi_port_scanner.py. The script will then rapidly test a socket connection through ports 1-10000.

### Configuration
To change what hosts you want scanned, edit the "hostnames.txt" file.
By default, the script will scan ports 1-10000. If you wish to scan a smaller, more defined list of ports, you can edit the "ports" variable near the top of "port_scanner.py".

# Detailed Script Process
__Here's the process:__
- Two variables are defined at the top: 
    - __hostnames_file_path__ - The file path for the required hostnames.txt file.
    - __default_timeout__ - The default timeout for the socket connections that test the ports (I've got it set to 0.001 seconds to make it fast, but feel free to adjust this as needed).
- multi_port_scanner.py opens the local text file (called hostnames.txt) and checks that there are hostnames inside of it.
- The __port_scan__ function is defined (more on that in a moment)
- For each hostname listed in hostnames.txt, the script will attempt to get it's IP Address.
- If successful, the script then calls the __port_scan__ function for that host.
    - __port_scan__ contains a for loop where it opens and closes a socket connection on each port specific in the script.
    - If the connection is successful, a message is printed in the terminal notifying that the port is open.
- After all specified ports with all specified hostnames have been checked, the script ends.

### How do I make this go faster or slower? / I'm not getting any positives!
On line 9, you can adjust amount of time each connection will take before it times out. I have it set to 0.001 seconds, but you can adjust this as you see fit.

# Rundown of Development Process
The big feature I wanted to learn was how to import a list from an external file and process it, which this script does. Another big feature that I learned about with this project was using sockets, which were easy to set up!

The only other issue I encountered was that the script was running very slowly, it took about a second for each port to be tested before it would time out. I was able to drasitcally speed this process up by changing the _setdefaulttimeout_ to 0.001 seconds. (To some that may seem like it wouldn't work, it actually works very well for what this needs!)

Once I had those in place, the rest of the script was largely setting up variables and for loops.

# Wishlist of Future Features
### Make It Into a Full-On Vulnerability Scanner
- This is the long term result I want for this project. I want to make an application that is a full-fledge vulnerability scanner. Checking ports is a simple way to start towards that larger project, so this was a great way to start making some functions that larger project would need using this smaller application.

# Disclaimer
This script is only meant to be used ethically, and with a company's legal consent.
