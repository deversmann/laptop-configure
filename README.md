# Using Ansible to Configure Laptop - SA

## Requirements and Steps
- Fedora installed
  - 32 GiB RAM (16 GiB Minimum)
  - "/" 40 GiB
  - "/home/" 200+ GiB
  - "/boot" 200 MiB
  - "swap" 6 GiB
- Set hostname to laptop.rnelson-demo.com
- Install Atom from <https://atom.io/>
  - "Ctrl + Shift + P", install Beautify and File Icons
- Modify the following files with the correct variables for environment
  - /home/deversma/git/laptop-configure/group_vars/all
- Execute the following command to pull down the run.sh script which will configure the environment and execute the main.yml playbook
  - bash wget -qO- https://github.com/deversmann/laptop-configure/raw/master/run.sh | sudo bash

## Roles

- firewall (configure firewall ports for SSH and HTTP/HTTPS)
- packages (install necessary packages)
- myfiles (local files needing to be copied to laptop)
- libvirtd (configures libvirtd)
- httpd (configures httpd for hosting necessary files)
- openscap (makes separate directory, clone GitHub for scap-security-guide, copy combine-tailoring.py)
- create-libvirt-network (creates libvirt network from user defined variables)

## Vars

All variables are located in `group_vars/all`.

## Tags

##
- `ansible-playbook -i hosts main.yml -t firewall,packages,libvirtd,httpd,openscap,files`
- `ansible-playbook -i hosts main.yml -t network`
- firewall
- myfiles
- packages
- libvirtd
- httpd
- openscap
- network

## Remaining Items to Complete

- include private and public ssh key
- automate installation of Atom and Beutify / File Icons
- store inventory-tower-initial-setup and manifest-rnelson-sales.zip

## License

Red Hat, the Shadowman logo, Ansible, and Ansible Tower are trademarks or registered trademarks of Red Hat, Inc. or its subsidiaries in the United States and other countries.

All other parts of this project are made available under the terms of the [MIT License](LICENSE).
