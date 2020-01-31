# Backup Linux Kernel-Based Virtual Machines (KVMs)

This script backs up local and remote virtual machines into ZIP files.  Each
ZIP file contains the domain definition XML file, copies of any firmware
files used by the VM, and the VM's disk image files.

This script cannot back up VMs that have existing disk snapshots.  The 
script checks if the domain (VM) has existing snapshots and returns an error
if it does.

If the VM is active when the backup is run, a temporary disk snapshot is 
created to freeze the disk image file(s) while the backup disk image 
file copy is being performed.

If the KVM domain name entered on the command line matches a domain name in the
"known_domains" list inside the script, then we look for a domain with 
that name on the host at the matching "host_uri".

If the KVM name entered on the command line is not in the "known_domains"
list, then we look for a domain by that name on the host at the 
"default_host_uri".

Set up SSL key-based ssh access for the userid doing the backups to the
root userid on the KVM host server(s) before using this script.
