# Auto-Scaling Docker Swarm Cluster On Container Load

This samlpe automation pack contains sensors actions and rules
for auto-scaling Docker Swarm cluster based on container load.


* Watch this video to see it in action: https://youtu.be/2tQlfxRrtXo
* Read a blog for details: (To Be Published)


#### Install and Configure

```
# Install this pack
st2 pack install https://github.com/dzimine/swarm_scaling

# You will also need AWS pack, too
st2 pack install aws

```

Give StackStorm system users - `stanley` and `st2` - access to the Docker group `usermod -a -G docker st2`.

Create a count key in the data store:

```
st2 key set asg.workers 2
```

> TODO: update a rule once [this st2 bug fixed](https://github.com/StackStorm/st2/issues/3407),
to increment/decrement workers count.


### Unit tests

To run the pack's unit tests:

```
# Activate existing pack's virtual environmet
source /opt/stackstorm/virtualenvs/swarm/bin/activate
# Run the tests first time - it will install test dependencies
st2-run-pack-tests -x /opt/stackstorm/swarm
# Skip installing dependencies on subsequent runs
st2-run-pack-tests -x -j /opt/stackstorm/swarm
```
