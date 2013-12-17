### install
- vagrant
    - http://www.vagrantup.com/downloads.html
- virtualbox
    - https://www.virtualbox.org/wiki/Downloads


### vagrantがインストールされているPCで実行

```
$ git clone git@github.com:bluerabbit/docker-example.git
$ cd docker-example
$ cp Dockerfile share/
$ vagrant up --provision
$ vagrant ssh
```

### VirtualBox(vagrant)で動作してるubuntuで実行

```
$ cd share
$ docker build -t docker-example .
$ sudo docker run -d -p 2022:22 -p 8080:8080 -v /home/vagrant/share:/home/ubuntu:rw docker-example
$ cd ~/.ssh
$ ssh-keygen -t rsa -C "your_email@example.com"
$ mkdir ~/share/.ssh
$ cat ~/.ssh/id_rsa.pub >> ~/share/.ssh/authorized_keys
$ ssh ubuntu@localhost -p 2022
```

- vagrantがインストールされているPCでhttp://localhost:8080を実行するとdockerコンテナで動作するhostに対しても8080でリクエストされる
- shareディレクトリは全てのホストで共有される
