<!-- .slide: data-state="section-break" id="SOC-solution" data-timing="5" data-menu-title="Compute HA in SOC" -->
# Compute HA in SUSE OpenStack Cloud


<!-- .slide: data-state="normal" id="ocf-architecture" data-menu-title="OCF RAs" class="architecture" data-timing="90" -->
## `NovaCompute` / `NovaEvacuate` OCF agents

<div class="architecture">
    <img alt="Standard architecture with pacemaker_remote"
         class="architecture fragment fade-out" data-fragment-index="1"
         data-src="images/standard-architecture.svg" />

    <span class="fragment" data-fragment-index="1">
        <img alt="OCF RA architecture"
             class="OCF-RA architecture fragment fade-out" data-fragment-index="2"
             data-src="images/OCF-RA-architecture.svg" />
    </span>

    <span class="fragment" data-fragment-index="2">
        <img alt="OCF RA failure domains"
             class="OCF-RA architecture"
             data-src="images/OCF-RA-failure-domains.svg" />
    </span>
</div>

Note:
*   Custom OCF Resource Agents (RAs)
    *   Pacemaker plugins to manage resources
*   Custom fencing agent (`fence_compute`) flags host for recovery
*   `NovaEvacuate` RA polls for flags, and initiates recovery
    *   Will keep retrying if recovery not possible
*   `NovaCompute` RA starts / stops `nova-compute`
    *   Start waits for recovery to complete


<!-- .slide: data-state="normal" id="RHEL-OSP-article" data-timing="30" -->
## RHEL OSP installation

<div class="row">
    <div class="col-md-6 article">
        <a href="https://access.redhat.com/documentation/en/red-hat-openstack-platform/8/high-availability-for-compute-instances/chapter-1-use-high-availability-to-protect-instances">
            <img alt="Article on setting up compute HA with RHEL OSP" class="full-slide"
                 data-src="images/RHEL-OSP-HA-article.png" />
        </a>
    </div>
    <div class="col-md-6 instructions">
        <a href="https://access.redhat.com/documentation/en/red-hat-openstack-platform/8/high-availability-for-compute-instances/chapter-1-use-high-availability-to-protect-instances">
            <img alt="Article on setting up compute HA with RHEL OSP" class="full-slide"
                 data-src="images/RHEL-OSP-HA-instructions.png" />
        </a>
    </div>
</div>

Note:
OCF RA approach is supported in RHEL OSP. Setup is manual;
here is a fragment of [the installation instructions](https://access.redhat.com/documentation/en/red-hat-openstack-platform/8/high-availability-for-compute-instances/chapter-1-use-high-availability-to-protect-instances).


<!-- .slide: data-state="normal" id="RHEL-OSP-article-2" data-timing="5" data-menu-title="          (page 2)" -->
## RHEL OSP installation (page 2)

<div class="row">
    <div class="col-md-6 article">
        <a href="https://access.redhat.com/documentation/en/red-hat-openstack-platform/8/high-availability-for-compute-instances/chapter-1-use-high-availability-to-protect-instances">
            <img alt="Article on setting up compute HA with RHEL OSP" class="full-slide"
                 data-src="images/RHEL-OSP-HA-instructions-2.png" />
        </a>
    </div>
    <div class="col-md-6 instructions">
        <a href="https://access.redhat.com/documentation/en/red-hat-openstack-platform/8/high-availability-for-compute-instances/chapter-1-use-high-availability-to-protect-instances">
            <img alt="Article on setting up compute HA with RHEL OSP" class="full-slide"
                 data-src="images/RHEL-OSP-HA-instructions-3.png" />
        </a>
    </div>
</div>


<!-- .slide: data-state="normal" id="RHEL-OSP-article-3" data-timing="5" data-menu-title="          (page 3)" -->
## RHEL OSP installation (page 3)

<div class="row">
    <div class="col-md-6 article">
        <a href="https://access.redhat.com/documentation/en/red-hat-openstack-platform/8/high-availability-for-compute-instances/chapter-1-use-high-availability-to-protect-instances">
            <img alt="Article on setting up compute HA with RHEL OSP" class="full-slide"
                 data-src="images/RHEL-OSP-HA-instructions-4.png" />
        </a>
    </div>
    <div class="col-md-6 instructions">
        <a href="https://access.redhat.com/documentation/en/red-hat-openstack-platform/8/high-availability-for-compute-instances/chapter-1-use-high-availability-to-protect-instances">
            <img alt="Article on setting up compute HA with RHEL OSP" class="full-slide"
                 data-src="images/RHEL-OSP-HA-instructions-5.png" />
        </a>
    </div>
</div>


<!-- .slide: data-state="normal" id="RHEL-OSP-article-4" data-timing="5" data-menu-title="          (page 4)" -->
## RHEL OSP installation (page 4)

<div class="row">
    <div class="col-md-6 article">
        <a href="https://access.redhat.com/documentation/en/red-hat-openstack-platform/8/high-availability-for-compute-instances/chapter-1-use-high-availability-to-protect-instances">
            <img alt="Article on setting up compute HA with RHEL OSP" class="full-slide"
                 data-src="images/RHEL-OSP-HA-instructions-6.png" />
        </a>
    </div>
    <div class="col-md-6 instructions">
        <a href="https://access.redhat.com/documentation/en/red-hat-openstack-platform/8/high-availability-for-compute-instances/chapter-1-use-high-availability-to-protect-instances">
            <img alt="Article on setting up compute HA with RHEL OSP" class="full-slide"
                 data-src="images/RHEL-OSP-HA-instructions-7.png" />
        </a>
    </div>
</div>


<!-- .slide: data-state="normal" id="RHEL-OSP-article-5" data-timing="5" data-menu-title="          (page 5)" -->
## RHEL OSP installation (page 175)

<div class="row">
    <div class="col-md-6 article">
        <a href="https://access.redhat.com/documentation/en/red-hat-openstack-platform/8/high-availability-for-compute-instances/chapter-1-use-high-availability-to-protect-instances">
            <img alt="Article on setting up compute HA with RHEL OSP" class="full-slide"
                 data-src="images/RHEL-OSP-HA-instructions-8.png" />
        </a>
    </div>
    <div class="col-md-6 instructions">
        <a href="https://access.redhat.com/documentation/en/red-hat-openstack-platform/8/high-availability-for-compute-instances/chapter-1-use-high-availability-to-protect-instances">
            <img alt="Article on setting up compute HA with RHEL OSP" class="full-slide"
                 data-src="images/RHEL-OSP-HA-instructions-9.png" />
        </a>
    </div>
</div>


<!-- .slide: data-state="normal" id="ocf-pros-cons" data-menu-title="OCF RA pros and cons" data-timing="30" -->
## `NovaCompute` / `NovaEvacuate` OCF agents

### Pros

*   Ready for production use *now*
*   Commercially supported by SUSE
*   RAs [upstream in `openstack-resource-agents` repo](https://github.com/openstack/openstack-resource-agents/tree/master/ocf)

### Cons

*   Known limitations (not bugs):
    *   Only handles failure of compute node, not of VMs, or `nova-compute`
    *   Some corner cases still problematic, e.g. if `nova` fails during recovery

Note:
SUSE's solution is incredibly easy to deploy, as we'll see next!
