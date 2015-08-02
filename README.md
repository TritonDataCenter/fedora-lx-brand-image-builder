# Fedora lx-brand Image Builder

This is a collection of scripts used for creating an LX-brand Fedora image.

## Requirements

In order to use these scripts you'll need:

- A Fedora running in a KVM virtual machine or bare metal (required for the `install` script) with git installed. Running `install` in a Fedora lx-brand zone is not supported. The major version of the Fedora machine you use to run the `install` script must be the same as the version you intend to install in the chroot directory (e.g., if you want to install Fedora 6, your host machine should also be Fedora 6)
- A SmartOS (or SDC headnode) install (required for the `create-lx-image` script)

## Usage

### Create a Fedora install tarball via the `install` script

On a Fedora or CentOS machine, do the following:

1. Clone this repo to your Fedora machine: `git clone https://github.com/joyent/fedora-lx-brand-image-builder`
2. Change to the repo directoru: `cd fedora-lx-brand-image-builder`
3. Run `./install -d <chroot> -m <mirror> -r <release package> -i <image name> -p <proper name> -u <image docs>` to install Fedora in a given directory. This will create a tarball of the installation in your working directory (named `<image name>-$YYMMDD.tar.gz`). See ./install -h for detailed usage.

### Create an lx brand image with the `create-lx-image` script

On a SmartOS in the global zone.

1. Clone this repo (if you have git installed) or download and upack it
2. Copy the tarball you created above to your SmartOS machine or SDC headnode and run `./create-lx-image -t /full/path/to/<image name>-<YYMMDD>.tar.gz` (substituting the name of your tar file). This will create the image file and manifest.
