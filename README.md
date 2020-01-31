# Backup Linux Kernel Virtual Machines (KVM)

This script backs up local and remote virtual machines in a ZIP file.  The
ZIP file domtains the domain definition XML file, copies of any firmware
files used by the VM, and the VM's disk image files.

This script cannot back up VMs that have existing disk snapshots.  The 
script checks if the domain has existing snapshots and returns an error
if it does.

If the KVM is active when the backup is run, a temporary disk snapshot is 
created to freeze the disk image file(s) while the backup (disk image 
file copy) is being performed.

If the KVM name entered on the command line matches a domain name in the
"known_domains" list inside the script, then we look for a domain with 
that name on the host at the matching "host_uri"

If the KVM name entered on the command line is not in the "known_domains"
list, then we look for a domain by that name on the host at the 
"default_host_uri"

Set up SSL key-based ssh access to the root userid on remote KVM
servers before using this script.
