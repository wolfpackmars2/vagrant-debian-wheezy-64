### Download Wheezy 64 Base Box
If you are looking for a Wheezy 64 box, you can download the Vagrant box created by the scripts in this repository.

**2013-Dec-11, 324.58MiB [debian-wheezy-64_7.2.box](http://files.idatasys.net/debian-wheezy-64_7.2.box)**

**Get it with Vagrant:**
    
    vagrant init wheezy64 http://files.idatasys.net/debian-wheezy-64_7.2.box --checksum 31F5D4C07131E7B1CA7766E895468D38 --checksum-type md5

### Updating The Base Box
If you would like to create a more up to date base box, set up the base box per above and then:
 1. Start and login to the box as user: vagrant password: vagrant
 2. Run all commands after **# Update and clean up** in *late_command.sh*, currently
  1. sudo apt-get -y update
  2. sudo apt-get -y upgrade
  3. sudo apt-get -y dist-upgrade -- *optional*
  4. sudo apt-get -y clean
  5. sudo apt-get -y autoclean
  6. sudo apt-get -y --purge autoremove
 3. Shutdown the vagrant box
 4. Use Vagrant to package the box, i.e.: *vagrant package --base "wheezy64" --output "20131230-debian-wheezy-64_7.2.box"*

### About The Base Box
This is a very bare Debian Wheezy x64 Vagrant Base Box.  It does **not** include Puppet, Chef or Ruby.  It is a bare bones Wheezy installation with the bare minimum required to work with Vagrant.  Some key information:
 1. It does include the standard Vagrant user and a default password of vagrant
 2. It also includes the default Vagrant user public key
 3. User 'Vagrant' has passwordless SUDO privileges
 4. It features an 80GB Dynamic HDD configured with LVM, so it can easily be expanded if needed
 5. Other settings and features per the configuration files in this repository

### About The Code

 1. This is a heavily customized modification to the forked code for my very specific use case.
 2. I don't consider this implementation to be suitable for use by others
 3. As of 11 Dec 2013, the preseed files work.  This is using the most recent version of Virtualbox for Windows and Debian 7.2 64-Bit.
 4. Setting up the VM is done using Virtualbox in the Windows Host
 5. A separate Debian Guest is used for building the custom.iso install image
 6. Creating the Vagrant .box is done manually in Windows.
 7. I may clean this up in the future and make it more "public friendly"
 8. Some things are hard coded which shouldn't be.  For example, the final line copies the custom.iso to my sf_shared folder so I can access the iso on my Windows Host.

####This script will:

 1. download the `Debian 7.2 "Wheezy"` server, 64bit iso
 2. ... do some magic to turn it into a vagrant box file
 3. output `debian-wheezy-64.box`

### Requirements

 * mkisofs
 * 7zip

### Usage on OSX

    ./build.sh

This should do everything you need. If you don't have `mkisofs` or `p7zip`, install [homebrew](http://mxcl.github.com/homebrew/), then:

    brew install cdrtools
    brew install p7zip

To add `debian-wheezy-64.box` with name `debian-72` into vagrant:

    vagrant box add "debian-72" debian-wheezy-64.box

### Usage on Linux

    ./build.sh

This should do everything you need. If you don't have `mkisofs` or `p7zip`:

    sudo apt-get install genisoimage
    sudo apt-get install p7zip-full

To add `debian-wheezy-64.box` with name `debian-72` into vagrant:

    vagrant box add "debian-72" debian-wheezy-64.box

### Notes

This script basted on original Carl's [repo](https://github.com/cal/vagrant-ubuntu-precise-64) and with some tweaks to be compatible Debian 7.2.

[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/dotzero/vagrant-debian-wheezy-64/trend.png)](https://bitdeli.com/free "Bitdeli Badge")
