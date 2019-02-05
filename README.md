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

need to look into using nginx with uwsgi for hosting the python app


run a flask app using nginx and gunicorn
update all the repos
install pip and nginx
  - pip installed with ansible
  - nginx install epel-release
    - then you can install nginx
nginx:
  - start the server
    sudo service httpd stop
    sudo systemctl disable httpd
    sudo service nginx start
    <!-- sudo rm /etc/nginx/sites-enabled/default -->
    sudo mkdir /etc/nginx/sites-enabled
    sudo mkdir /etc/nginx/sites-available
    sudo touch /etc/nginx/sites-available/flask_settings
    sudo ln -s /etc/nginx/sites-available/flask_settings /etc/nginx/sites-enabled/flask_settings
    <!-- add the following the flask_settings file -->
    server {
      listen 80;
      server_name localhost;
      location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
      }
    }
  -restart nginx
    sudo service nginx restart
