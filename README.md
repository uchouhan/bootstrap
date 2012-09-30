Bootstrap
=========

The pre-requisites to bootstrap a development environment are:
- Perform a 7-pass erase on the drive.
- Sign up for an Apple developer account.
- Install the latest version of OS X.
- Install Xcode command line tools.

The Bootstrap process:
- Install Chef `sudo true && curl -L http://www.opscode.com/chef/install.sh | sudo bash`
  - `chown -R <name>:staff /opt/chef`
- Download the validation.pem, client.rb and knife.rb configuration files.
- Add node_name `<name>.local` in the client.rb and knife.rb configuration files.
- Configure Chef client. `cd /etc`
  - `mkdir chef`
  - `chown -R <name>:staff chef`
  - `mv validation.pem chef`
  - `mv client.rb chef`
  - `sudo mkdir /var/chef`
  - `chown -R <name>:staff /var/chef`
- Run Chef client.
  - `chef-client`
- Configure knife. `cd`
  - `mkdir .chef`
  - `mv knife.rb .chef`
  - `knife`

The configuration process:
- Switch your environment to Development `sudo knife node edit <name>.local`.

  ```
    {
      "name": "<name>.local",
      "chef_environment": "Development",
      "normal": {
        "tags": [

        ]
      },
      "run_list": [

      ]
    }
  ```
  
- Bootstrap the Homebrew directory `sudo chown -R `whoami`:staff /usr/local`.