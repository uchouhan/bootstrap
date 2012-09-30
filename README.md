Bootstrap
=========

The pre-requisites to bootstrap a development environment are:
- Perform a 7-pass erase on the drive.
- Sign up for an Apple developer account.
- Install the latest version of OS X.
- Install Xcode command line tools.

The Bootstrap process:
- Install Chef `sudo true && curl -L http://www.opscode.com/chef/install.sh | sudo bash`
- Download the validation.pem, client.rb and knife.rb configuration files.
- Add node_name `<name>.local` in the client.rb and knife.rb configuration files.
- Configure Chef client.
  - `sudo mkdir /etc/chef`
  - `sudo mv validation.pem /etc/chef`
  - `sudo mv client.rb /etc/chef`
  - `sudo mv knife.rb /etc/chef`
- Run Chef client.
  - `sudo chef-client -c /etc/chef/client.rb`

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