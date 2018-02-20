# Troubleshooting


## (Self-Hosted) Engine

### "The hosted engine isn't running or isn't accessible"

Check the status of the hosted engine VM:

```shell
hosted-engine --vm-status
```

If the health is bad or the VM stopped = true, you can try enabling global maintenance and starting the VM:

```shell
hosted-engine --set-maintenance --mode=global
hosted-engine ---vm-start # This may take a minute

hosted-engine --vm-status
hosted-engine --set-maintenance --mode=none
```

If the engine VM shows as running, but the web interface isn't accessable:

1. Try SSHing to the engine
2. If SSH isn't working, you can pop a console to the VM by running:

```shell
hosted-engine --console
```

- [Troubleshooting Self-Hosted Engine](https://www.ovirt.org/documentation/self-hosted/chap-Troubleshooting/)