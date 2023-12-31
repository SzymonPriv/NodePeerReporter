# NodePeerReporter

Welcome to the Node Peer Reporter for the Linux Kernel AX.25 and NET/ROM stack.
This simple script is designed to report your packet node to the M0LTEmap hosted
at http://nodes.ukpacketradio.network/packet-network-map.html

## Requirements
1. Bash must be installed in /bin/bash
2. Curl must be installed and in the path
3. JQ must be installed and in the path

## Installation
1. Copy the main npr script to `/usr/sbin/npr` (as root)
2. Make the npr script executable e.g. `chmod 755 /usr/sbin/npr`
3. Create an `/etc/npr.conf` file based on the example file in this repository
4. Run `/usr/sbin/npr -d` (debug) to confirm that it works correctly
5. Add a crontab entry as root `*/20 * * * * /usr/sbin/npr >> /var/log/npr.log`

## Notes
- Location of the conf file is hard coded
- The script uses `/proc/net/nr_neigh` to determine peer nodes
- The script stores a copy of `nr_neigh` in `/tmp` as a cache when run
- The script will only make a network call if there has been a change or
  3 hours have passed since the last update
