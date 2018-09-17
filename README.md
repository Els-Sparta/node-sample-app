# Ealilan M

# Sparta Node Sample App

## Instructions to setting up a VirtualBox

1. <h3> Software</h3>
  * Before a virtualbox can be initiated you need to install the latest versions of:
    * VirtualBox: https://www.virtualbox.org/wiki/Downloads
    * Vagrant: https://www.vagrantup.com/downloads.html
    * Atom: https://atom.io/
2. <h3>Setting up the virtual environment on terminal</h3>
  * To check if vagrant has been successfully installed run
    `vagrant`
    in the terminal, if it has been it successfully install the terminal should print out a list of commands you can run with `vagrant`.
  * The first command is to create a vagrant file, `vagrant init`. Once your file has been initialised open it in **atom**
  * The next step is to edit this file, delete everything currently in the file and replace it with,
  ```
  Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.network("private_network", ip: "192.168.10.100")
    config.hostsupdater.aliases = ["development.local"]
  end
  ```
  * Save the file and run `vagrant up` in the terminal, this sets up the virtual machine
  * To check if that has worked run `vagrant ssh`, this allows the user access to the virtual machine
  * Exit the machine, `exit`, and run `vagrant plugin install vagrant-hostsupdater`. This is a Vagrant plugin that manages hosts files within a multi-machine environment.
  * After the plugin has install access the virtual machine, `vagrant ssh`, and first run the command `sudo apt-get update`. This updates the package lists for upgrades and new packages.
  * Finally run the command `sudo apt-get install nginx`. Nginx is a web server that will run on your local machine allowing you to run a web-application.


## Description

This app is intended for use with the Sparta Global Devops Stream as a sample app. You can clone the repo and use it as is but no changes will be accepted on this branch.

To use the repo within your course you should fork it.

The app is a node app with three pages.

### Homepage

``localhost:3000``

Displays a simple homepage displaying a Sparta logo and message. This page should return a 200 response.

### Blog

``localhost:3000/posts``

This page displays a logo and 100 randomly generated blog posts. The posts are generated during the seeding step.

This page and the seeding is only accessible when a database is available and the DB_HOST environment variable has been set with it's location.

### A fibonacci number generator

``localhost:3000/fibonacci/{index}``

This page has be implemented poorly on purpose to produce a slow running function. This can be used for performance testing and crash recovery testing.

The higher the fibonacci number requested the longer the request will take. A very large number can crash or block the process.


### Hackable code

``localhost:3000/hack/{code}``

There is a commented route that opens a serious security vulnerability. This should only be enabled when looking at user security and then disabled immediately afterwards

## Usage

Clone the app

```
npm install
npm start
```

You can then access the app on port 3000 at one of the urls given above.

## Tests

There is a basic test framework available that uses the Mocha/Chai framework

```
npm test
```

The test for posts will fail ( as expected ) if the database has not been correctly setup.
