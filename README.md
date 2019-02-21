# Saltstack Test Lab

An easy to run lab to learn [Saltstack](https://www.saltstack.com/) or test your formulas and states.

It will start one Saltstack master and two minions.

## Dependencies

To run this lab you'll need Docker(17.12.0+) and Docker compose.

## Basic lab management

### Running the lab

To start the lab use the following command at the root of the repository.

```
docker-compose up --detach --build
```

Use the `salt-key` command on the master until you see the two minions in the `Unaccepted Keys` list:

```
docker exec -t saltstack-master salt-key
```

Then accept the minion's keys:

```
docker exec -t saltstack-master salt-key -A -y
```

To test everything's went right run:

```
docker exec -t saltstack-master salt "*" test.ping
```

Note: the `-t` option is useful to get colors from Saltstack output.

### Stopping the lab

```
docker-compose stop
```

### Removing the lab

After stopping the lab, if you want to destroy it, run:

```
docker-compose down --rmi all
```

## Using Saltstack

### Adding your Saltstack files to the lab

Store your states in the `salt` directory and your pillars in the `pillar` directory.

## Advanced configuration

To override Docker settings, create a file named `docker-compose.override.yml` at the root of the repository.

The following example shows how to customize the lab's network IP range:

```YAML
version: "3.5"

networks:
  saltstack:
    name: saltstack
    ipam:
      driver: default
      config:
        - subnet: 192.168.0.0/24
```
