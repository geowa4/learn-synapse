Synapse bug
===========

Prerequisites
-------------

To run this, you'll need

  - Vagrant and Ansible installed,
  - an AWS account with two tagged nodes in it, optionally running elasticsearch,
  - and an AWS key for querying the API.

Update bug.json with that AWS key.

Reproduction
------------

    vagrant up
    vagrant ssh
    cd /vagrant
    java -jar synapse.jar --config bug.json
    # quit
    cat /etc/haproxy/haproxy.cfg

Synapse clearly indicates via standard out that it has identified the two EC2 instances.
It does not modify /etc/haproxy/haproxy.cfg as configured though it reports that it has regenerated the config.

`synapse.jar` was built with the source at e012cd3a518098545a0ba73958d3c17bd5ab40d9 in airbnb/synapse.
