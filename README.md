# Jeff Geerling's Vagrant Box Packer Builds

This project contains the Packer build configurations for all of Jeff Geerling's (box's) Vagrant Boxes. Each box builds a minimal base box for use with VirtualBox. Available boxes include:

  - [box/ubuntu1804](https://app.vagrantup.com/box/boxes/ubuntu1804) - [`ubuntu1804` directory](ubuntu1804/)
  - [box/ubuntu1604](https://app.vagrantup.com/box/boxes/ubuntu1604) - [`ubuntu1604` directory](ubuntu1604/)
  - [box/centos8](https://app.vagrantup.com/box/boxes/centos8) - [`centos8` directory](centos8/)
  - [box/centos7](https://app.vagrantup.com/box/boxes/centos7) - [`centos7` directory](centos7/)
  - [box/centos6](https://app.vagrantup.com/box/boxes/centos6) - [`centos6` directory](centos6/)
  - [box/debian10](https://app.vagrantup.com/box/boxes/debian10) - [`debian10` directory](debian10/)
  - [box/debian9](https://app.vagrantup.com/box/boxes/debian9) - [`debian9` directory](debian9/)
  - [box/debian8](https://app.vagrantup.com/box/boxes/debian8) - [`debian8` directory](debian8/)

All of these boxes are available as public, free Vagrant boxes and can be used with the command:

    vagrant init box/[box name here]

You can also fork this repository and customize a build configuration with your own Ansible roles and playbooks to build a fully custom Vagrant box using Packer. For one such example, see the [Drupal VM Packer Build](https://github.com/box/packer-drupal-vm).

## Requirements

The following software must be installed/present on your local machine before you can use Packer to build any of these Vagrant boxes:

  - [Packer](http://www.packer.io/)
  - [Vagrant](http://vagrantup.com/)
  - [VirtualBox](https://www.virtualbox.org/)
  - [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## Usage

Make sure all the required software (listed above) is installed, then cd into one of the box directories and run:

    $ packer build -var 'version=1.2.0' box-config.json

After a few minutes, Packer should tell you the box was generated successfully, and the box was uploaded to Vagrant Cloud.

> **Note**: This configuration includes a post-processor that pushes the built box to Vagrant Cloud (which requires a `VAGRANT_CLOUD_TOKEN` environment variable to be set); remove the `vagrant-cloud` post-processor from the Packer template to build the box locally and not push it to Vagrant Cloud. You don't need to specify a `version` variable either, if not using the `vagrant-cloud` post-processor.

## Testing built boxes

There's an included Vagrantfile that allows quick testing of the built Vagrant boxes. From the same box directory, run the following command after building the box:

    $ vagrant up

Test that the box works correctly, then tear it down with:

    $ vagrant destroy -f

## License

MIT

## Author

These configurations are maintained by [Jeff Geerling](https://www.jeffgeerling.com), author of [Ansible for DevOps](https://www.ansiblefordevops.com).
