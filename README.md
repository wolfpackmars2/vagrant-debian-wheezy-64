## About

FIRST:
 1. This is a heavily customized modification to the forked code for my very specific use case.
 2. I don't consider this implementation to be suitable for use by others
 3. As of 11 Dec 2013, the preseed files work.  This is using the most recent version of Virtualbox for Windows and Debian 7.2 64-Bit.
 4. Setting up the VM is done using Virtualbox in the Windows Host
 5. A separate Debian Guest is used for building the custom.iso install image
 6. Creating the Vagrant .box is done manually in Windows.
 7. I may clean this up in the future and make it more "public friendly"

This script will:

 1. download the `Debian 7.2 "Wheezy"` server, 64bit iso
 2. ... do some magic to turn it into a vagrant box file
 3. output `debian-wheezy-64.box`

## Requirements

 * mkisofs
 * 7zip

## Usage on OSX

    ./build.sh

This should do everything you need. If you don't have `mkisofs` or `p7zip`, install [homebrew](http://mxcl.github.com/homebrew/), then:

    brew install cdrtools
    brew install p7zip

To add `debian-wheezy-64.box` with name `debian-72` into vagrant:

    vagrant box add "debian-72" debian-wheezy-64.box

## Usage on Linux

    ./build.sh

This should do everything you need. If you don't have `mkisofs` or `p7zip`:

    sudo apt-get install genisoimage
    sudo apt-get install p7zip-full

To add `debian-wheezy-64.box` with name `debian-72` into vagrant:

    vagrant box add "debian-72" debian-wheezy-64.box

### Notes

This script basted on original Carl's [repo](https://github.com/cal/vagrant-ubuntu-precise-64) and with some tweaks to be compatible Debian 7.2.

[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/dotzero/vagrant-debian-wheezy-64/trend.png)](https://bitdeli.com/free "Bitdeli Badge")
