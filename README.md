# pfifo scheduler for aqmt

This repository contains the fifo scheduler from Linux patched so
it can be used with https://github.com/henrist/aqmt

New commits in Linux should be cherry-picked to the `kernel-reference`
branch and merged to master. This way the `kernel-reference` should
be a 1-to-1 match to the implementation in Linux.

## Using

Before building you have to symlink `common/testbed.h` from the aqmt project
so it is available in this folder.

To be able to actually use this qdisc you will also have to patch iproute2.
See below.

Building:

```
make
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
