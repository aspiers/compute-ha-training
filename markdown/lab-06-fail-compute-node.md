<!-- .slide: data-state="section-break" id="lab-6" data-menu-title="Lab 6: fail compute node" -->
# Lab 6: test compute node failover
## (the exciting bit!)


<!-- .slide: data-state="normal" id="simulate-failure" -->
## Simulate compute node failure

Login to compute node where VM runs, and type:

```
pkill -9 -f pacemaker_remoted
```

This will cause fencing!  (Why?)

Note:
Pacemaker cluster will now lose connectivity to the
compute node, so has no way of knowing whether it's
dead or not.  So the only way to safely recover resources
to another remote is by first fencing the node.


<!-- .slide: data-state="normal" id="verify-recovery" -->
## Verify recovery

* Ping to the VM is interrupted, then resumed
* Ping to the compute node is interrupted (then resumed)
* Log messages show:
  ```
  NovaEvacuate [...] Initiating evacuation
  NovaEvacuate [...] Completed evacuation
  ```
* `crm status` shows compute node offline (then back online)
* Verify compute node was fenced
  * Check `/var/log/messages` on DC
* Verify VM moved to another compute node
  ```sh
  nova list --fields host,name
  ```
