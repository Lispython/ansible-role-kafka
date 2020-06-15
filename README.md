[![Build Status](https://travis-ci.com/nl2go/ansible-role-kafka.svg?branch=master)](https://travis-ci.com/nl2go/ansible-role-kafka)
[![Ansible Galaxy](https://img.shields.io/badge/role-nl2go.kafka-blue.svg)](https://galaxy.ansible.com/nl2go/kafka/)
[![Ansible Galaxy Quality Score](https://img.shields.io/ansible/quality/49219)](https://galaxy.ansible.com/nl2go/kafka/)
[![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/nl2go/ansible-role-kafka)](https://github.com/nl2go/ansible-role-kafka/releases)
[![Ansible Galaxy Downloads](https://img.shields.io/ansible/role/d/49219.svg?color=blue)](https://galaxy.ansible.com/nl2go/kafka/)

# Ansible Role: Apache Kafka

An Ansible Role that manages installation and configuration of [Apache Kafka](https://kafka.apache.org/).

Kafka heavily depends on zookeeper which is not part of this role. To install zoopeeper we recommend the nl2go [zookeeper role](https://github.com/nl2go/ansible-role-zookeeper): 

## Role Variables

Available variables listed and described along with default values in [defaults/main.yml](defaults/main.yml).

## Dependencies

- [nl2go.openjdk](https://galaxy.ansible.com/nl2go/openjdk)

## Example Playbook

    - hosts: all
      roles:
        - nl2go.kafka
      vars:
        kafka_zookeeper_connection_hosts:
          - my.zookeeper.host:2181

## Set up monitoring for Kafka

For enabling monitoring via JMX you use the `kafka_environment_variables` variable to adjust the respective Kafka settings.

An overview of the variables used by Kafka can be found in the [Kafka startup script](https://github.com/apache/kafka/blob/trunk/bin/kafka-run-class.sh).

Here is an example playbook:

    - hosts: all
      roles:
        - nl2go.kafka
      vars:
        kafka_environment_variables:
          JMX_PORT: 1099
          KAFKA_JMX_OPTS: "-Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false"

## Development

Use [docker-molecule](https://github.com/nl2go/docker-molecule) following the instructions to run [Molecule](https://molecule.readthedocs.io/en/stable/)
or install [Molecule](https://molecule.readthedocs.io/en/stable/) locally (not recommended, version conflicts might appear).

Use following to run tests:

    molecule test --all

## Maintainers

- [dirkaholic](https://github.com/dirkaholic)

## License

See the [LICENSE.md](LICENSE.md) file for details.

## Author Information

This role was created in 2020 by [Newsletter2Go GmbH](https://www.newsletter2go.com/).
