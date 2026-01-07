# Auto Multi-Port Scanner

An automatic multi-port scanner. Enter FQDNs or hostnames into a local plaintext file, and it will check any open ports on those hostnames!

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

I have plans to add features, like exporting the result to a csv or excel spreadsheet, but this is the first step to getting there.

## Configuration

port_scanner.py scans the hostnames listed in "hostnames.txt", and 

By default, the script will scan ports 1-10000. If you wish to scan a smaller, more defined list of ports, you can edit the "ports" variable near the top of "port_scanner.py"

## How do I make this go faster or slower? / I'm not getting any positives!
On line 9, you can adjust amount of time each connection will take before it times out. I have it set to 0.001 seconds, but you can adjust this as you see fit.

## Disclaimer

This script is only meant to be used ethically, and with a company's legal consent.