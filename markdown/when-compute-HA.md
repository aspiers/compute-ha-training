<!-- .slide: data-state="section-break" id="when" data-menu-title="Why compute HA?" data-timing="10" -->
# When is compute HA important?

Note:
The previous slide suggests there is a problem which needs
solving, but does it *always* need solving?


<!-- .slide: data-state="normal" id="white-elephant" data-timing="40" data-menu-title="White elephant" -->
## Addressing the white elephant in the room

<div>
    <img alt="The white elephant in the room"
         class="fragment"
         style="height: 90%; margin: -40px 0 0 50;"
         data-src="images/white-elephant.svg" />
</div>

Note:

Compute node HA is a controversial feature, because
some people think it's an anti-pattern which does not belong,
in clouds, whereas other people feel a strong need for it.
To understand when it's needed, first we have to understand
the different types of workload which people want to run in
the cloud.

But what are pets?


<!-- .slide: data-state="normal" id="pets-vs-cattle" class="pets-vs-cattle" data-timing="50" -->
## Pets vs. cattle

<div class="row pets">
    <div class="col-md-5">
        <img data-src="images/begging-cat-c2.jpg" alt="cute pleading cat"
             class="pull-right" />
    </div>
    <div class="col-md-7">
        <ul>
            <li class="fragment" data-fragment-index="2">
                Pets are given names like <tt>mittens.mycompany.com</tt>
            <li class="fragment" data-fragment-index="3">
                Each one is unique, lovingly hand-raised and cared for
            <li class="fragment" data-fragment-index="4">
                When they get ill, you nurse them back to health
        </ul>
    </div>
</div>

<div class="row cattle">
    <div class="col-md-5">
        <img data-src="images/cattle-c.jpg" alt="cattle" class="pull-right" />
    </div>
    <div class="col-md-7">
        <ul>
            <li class="fragment" data-fragment-index="2">
                Cattle are given names like <tt>vm0213.cloud.mycompany.com</tt>
            <li class="fragment" data-fragment-index="3">
                They are almost identical to other cattle
            <li class="fragment" data-fragment-index="4">
                When one gets ill, you get another one
        </ul>
    </div>
</div>

Note:
- Pets are typically given unique names, whereas cattle aren't.
- This reflects that pets take a lot of work to create and look after,
  whereas cattle don't.
- Similarly, when something goes wrong with a pet, you need to
  invest a lot of effort to fix it, whereas with cattle you just get another one.
- thanks to CERN for this slide, and Bill Baker for the original terminology


<!-- .slide: data-state="normal" id="pets-vs-cattle-2" class="pets-vs-cattle" data-menu-title="Dead VMs" data-timing="50" -->
## What does that mean in practice?

<div class="row pets">
    <div class="col-md-5">
        <img data-src="images/begging-cat-c2.jpg" alt="cute pleading cat"
             class="pull-right" />
    </div>
    <div class="col-md-7 vcenter">
        <ul>
            <li class="fragment" data-fragment-index="1">
                Service downtime when a pet dies
            <li class="fragment" data-fragment-index="2">
                VM instances often stateful, with mission-critical data
            <li class="fragment" data-fragment-index="3">
                <span class="fg-bright-orange bold">Needs automated recovery
                with data protection</span>
        </ul>
    </div>
</div>

<div class="row cattle">
    <div class="col-md-5">
        <img data-src="images/cattle-c.jpg" alt="cattle" class="pull-right" />
    </div>
    <div class="col-md-7 vcenter">
        <ul>
            <li class="fragment" data-fragment-index="1">
                Service resilient to instances dying
            <li class="fragment" data-fragment-index="2">
                Stateless, or ephemeral (disposable) storage
            <li class="fragment" data-fragment-index="3">
                <span class="fg-medium-green bold">Already ideal for cloud</span>
                <span class="fg-bright-orange bold">… but automated
                recovery still needed!</span>
        </ul>
    </div>
</div>


<!-- .slide: data-state="normal" id="cattle-dead" data-menu-title="Dead cattle" data-timing="40" -->
## If compute node is hosting cattle …

<img class="cattle" data-src="images/cattle-c.jpg" alt="cattle" />
<img class="fragment bang" alt="cow explosion!" data-src="images/explosion.svg"
     data-fragment-index="1" />

… to <!-- .element: class="fragment" data-fragment-index="1" -->
handle failures at scale, we need to automatically restart VMs somehow.

Note:

... otherwise over time, our service becomes more and more degraded,
and manually restarting is a waste of time and unreliable due to the human
element.

Heat used to support this, but
[HARestarter deprecated since Kilo](http://docs.openstack.org/developer/heat/template_guide/unsupported.html)
[Heat is gaining convergence / self-healing capabilities](http://specs.openstack.org/openstack/heat-specs/
)
but nothing concrete currently planned for instance auto-restarting.

 http://docs.openstack.org/developer/heat/ says "templates […]
allow some more advanced functionality such as instance high
availability […]" but according to Thomas Herve
([current Heat PTL](https://wiki.openstack.org/wiki/PTL_Elections_March_2016#Results))
this is no longer supported.

[Heat/HA wiki](https://wiki.openstack.org/wiki/Heat/HA) out of date



<!-- .slide: data-state="normal" id="kittehs-dead" data-menu-title="Dead pets" data-timing="30" -->
## If compute node is hosting pets …

<img class="pets" data-src="images/cats.jpg" alt="pets" />
<img class="fragment bang" alt="kitty explosion!" data-src="images/explosion.svg"
     data-fragment-index="1" />

… we <!-- .element: class="fragment" data-fragment-index="1" -->
have to resurrect <span class="fg-bright-red">very carefully in order to
avoid any zombie pets!</span>

Note:
This case is more complex than resurrecting cattle, due to the risk
of zombie pets.

A zombie is a VM which appeared dead but didn't actually die properly -
it could conflict with its resurrected twin.


<!-- .slide: data-state="normal" id="justification" data-menu-title="Justification" data-timing="60" -->
## Do we really need compute HA in OpenStack?

<span class="fragment" data-fragment-index="1">
    <img class="fragment fade-out" data-fragment-index="2"
         data-src="images/yes-or-no.svg" alt="Yes!" />
</span>

### Why?  <!-- .element: class="fragment" data-fragment-index="2" style="margin-top: 80px" -->

*   Compute <!-- .element: class="fragment" data-fragment-index="2" -->
    HA needed for cattle as well as pets
*   Valid <!-- .element: class="fragment" data-fragment-index="3" -->
    reasons for running pets in OpenStack
    *   Manageability benefits
    *   Want to avoid multiple virtual estates
    *   Too expensive to cloudify legacy workloads

Note:

So to sum up, my vote is yes, because even cattle need compute node HA.

Also, rather than painful "big bang" migrations to cloud-aware
workloads, it's easier to deprecate legacy workloads, let them reach
EOL whilst gradually migrating over to next-generation architectures.

This is a controversial topic, but naysayers tend to favour idealism
over real world pragmatism.
