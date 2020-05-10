# decompress-lz4-kernels
A Debian/Ubuntu kernel postinst hook which decompresses LZ4-compressed kernels.

Ubuntu started compressing their kernels with LZ4 as of the 19.10 release, and not all software yet supports that.

## Who needs this
If you've ordered a new VM from BitFolk or installed one yourself from [BitFolk's Xen Shell](https://tools.bitfolk.com/wiki/Xen_Shell) then this hook will be installed automatically and you _don't_ need to be reading any of this.

This repository exists for people who are upgrading from an earlier version of Ubuntu and need the hook to have a bootable kernel, or just in case it helps anyone else.

## Prerequisites
* [extract-vmlinux](https://raw.githubusercontent.com/torvalds/linux/master/scripts/extract-vmlinux). Put it in **`/usr/local/sbin/`** and make sure it is executable
* lz4 binary from the lz4 package
* readelf binary from the binutils package

## Installation

Place the decompress-lz4-kernels file in the **`/etc/kernel/postinst.d/`** directory and make sure it is executable.

It will be called next time you install a kernel. If you'd like it to be run on a kernel you already have installed then you can force a reinstall of the package like this:

```
$ sudo apt reinstall linux-image-5.4.0-29-generic
```

## Support
If you are stuck then please contact [the BitFolk Users mailing list](https://lists.bitfolk.com/mailman/listinfo/users).
