This is a collection of various helper scripts intended to be run
inside an ec2 instance.

# Scripts
## stack-volume-attach
This script takes a 'volume id' and mountpoint, then tries to find a
volume tagged with the given volume id in the same AZ as the instance.
If found and not attached anywhere else, it gets attached and mounted
to the specified mountpoint.
If there is no filesystem found, it will create one.
