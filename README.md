# docker-travis-ci
Images used for travis ci

# How to build

    $ cd centos
    $ docker build -t DOCKER_IMAGE_NAME .

# How to use
Originaly idea is to use them for ansible role testing, e.g. using [molecule](https://github.com/metacloud/molecule):

    $ cat molecule.yml
    docker:
      containers:
        ...
        - name: ansible-dockerswarm-02
          ansible_groups:
            - docker_engine
            - docker_swarm_manager
          image: sergk/centos7-systemd
          image_version: latest
          privileged: True
          volume_mounts:
            - '/sys/fs/cgroup:/sys/fs/cgroup:ro'
          command: '/usr/sbin/init'
        - name: ansible-dockerswarm-03
          ansible_groups:
            - docker_engine
            - docker_swarm_worker
          image: sergk/centos7-systemd
          image_version: latest
          privileged: True
          volume_mounts:
            - '/sys/fs/cgroup:/sys/fs/cgroup:ro'
          command: '/usr/sbin/init'
