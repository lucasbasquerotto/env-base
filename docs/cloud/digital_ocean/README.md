# DigitalOcean

Supported cloud contexts (can be used in the place of `{{ project_ctxs }}`):

- [vpn](#vpn)
- [volume](#volume)
- [node](#node)

See the [environment base file](../../../cloud/digital_ocean.yml) for details about the deployment.

## VPN

Creates tags and firewalls at DigitalOcean to restrict access to and from droplets.

The DigitalOcean VPN documentation can be seen at http://github.com/lucasbasquerotto/ext-cloud/tree/master/tasks/vpn#digitalocean.

## Volume

Manages block storages at DigitalOcean that can be attached to droplets to expand te disk size.

The DigitalOcean Volume documentation can be seen at http://github.com/lucasbasquerotto/ext-cloud/tree/master/tasks/volume#digitalocean.

## Node

Creates a `s-1vcpu-1gb` (1GB and 1CPU) Droplet at DigitalOcean in the region `AMS3` with the image `ubuntu-18-04-x64` (Ubuntu 18.04).

The DigitalOcean Node documentation can be seen at http://github.com/lucasbasquerotto/ext-cloud/tree/master/tasks/node#digitalocean.
