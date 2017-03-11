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
        - name: ansible-dockerswarm-01
          ansible_groups:
            - docker_engine
            - docker_swarm_manager
          image: sergk/docker-travis-ci
          image_version: ubuntu16.04-latest
          privileged: True
        - name: ansible-dockerswarm-02
          ansible_groups:
            - docker_engine
            - docker_swarm_manager
          image: sergk/docker-travis-ci
          image_version: centos7-latest
          privileged: True
          volume_mounts:
            - '/sys/fs/cgroup:/sys/fs/cgroup:ro'
          command: '/usr/sbin/init'
        - name: ansible-dockerswarm-03
          ansible_groups:
            - docker_engine
            - docker_swarm_worker
          image: sergk/docker-travis-ci
          image_version: centos7-latest
          privileged: True
          volume_mounts:
            - '/sys/fs/cgroup:/sys/fs/cgroup:ro'
          command: '/usr/sbin/init'
