# pfifo scheduler for aqmt

This repository contains the fifo scheduler from Linux patched so
it can be used with https://github.com/henrist/aqmt

New commits in Linux should be cherry-picked to the `kernel-reference`
branch and merged to master. This way the `kernel-reference` should
be a 1-to-1 match to the implementation in Linux.

## Using

When building, we need to add the `common` directory of the `aqmt`
repository to the inclusion path.

To be able to actually use this qdisc you will also have to patch iproute2.
See below.

Building:

```
CPATH=/path/to/aqmt/common make
```

Loading kernel module:

```
sudo make load
```

The scheduler will now be available as a qdisc with the name `pfifo_aqmt`,
as long as you have also patched iproute2/tc.

Unloading:

```
sudo make unload
```

## Patching iproute2

See provided `iproute2.patch`.
