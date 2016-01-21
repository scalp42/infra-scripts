This is a collection of various small helper scripts

# Scripts
## stack-volume-attach
This script takes a 'volume id' and mountpoint, then tries to find a
volume tagged with the given volume id in the same AZ as the instance.
If found and not attached anywhere else, it gets attached and mounted
to the specified mountpoint.
If there is no filesystem found, it will create one.

## consul-register
This script takes a consul service definition and a command to run. After
executing the command, it will copy the service definition to the consul
config directory and reload consul. Once the command exits, it will remove
the service file and reload consul again.
This makes it easy to dynamically register services and can be especially
useful with `consul lock` where you want to register only services that
acquired an lock:

    $ consul lock locks/my-service consul-register \
        -d /etc/consul/my-service.json /var/lib/consul-services \
        my-service
