start the project by running the following command

This creates a new vagrant box with centos/7 as its version
```bash
  vagrant init centos/7
```

To start the box
```bash
  vagrant up
```

To ssh into the box
```bash
  vagrant ssh
```


copying of files from a project can be done using a shell provisioner

```
Vagrant.configure("2") do |config|
  # ... other configuration

  config.vm.provision "file", source: "~/path/to/host/folder", destination: "$HOME/remote/newfolder"
end
```

running an install and update aswell as reboot can be done via the shell



need to copy over the files that are in a folder in the directory for the python project

need to install pipenv so that i can install flask using pip for the simple REST app

need to open up the port using port forwarding


need to install vagrant-reload before being able to run the box
