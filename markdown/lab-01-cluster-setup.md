<!-- .slide: data-state="section-break" id="lab-1" data-menu-title="Lab 1: cluster setup" -->
# Lab 1: setup Pacemaker cluster and remotes


<!-- .slide: data-state="normal" id="starting-point" data-menu-title="Starting Point" -->
## Starting Point

<img class="full-height" alt="starting point" data-src="images/hands-on/01-starting-point.png" />

Note:
We will consider all these barclamps already installed and nodes discovered and allocated


<!-- .slide: data-state="normal" id="pacemaker-proposal" data-menu-title="Pacemaker Proposal" -->
## Create pacemaker proposal

<img class="full-slide" alt="pacemaker-proposal" data-src="images/hands-on/02-create-pacemaker-proposal.png" />


<!-- .slide: data-state="normal" id="pacemaker-attributes" data-menu-title="Pacemaker attributes" -->
## Create pacemaker attributes

<img class="full-slide" alt="pacemaker-attributes" data-src="images/hands-on/03-pacemaker-attributes.png" />


<!-- .slide: data-state="normal" id="pacemaker-stonith" data-menu-title="Pacemaker STONITH" -->
## Pacemaker STONITH

<img class="full-slide" alt="pacemaker-stonith" data-src="images/hands-on/04-pacemaker-stonith.png" />


<!-- .slide: data-state="normal" id="pacemaker-mail" data-menu-title="Pacemaker Mail Notifications" -->
## Pacemaker Mail Notifications

<img class="full-slide" alt="pacemaker-mail" data-src="images/hands-on/05-pacemaker-mail-notifications.png" />


<!-- .slide: data-state="normal" id="pacemaker-drbd-1" data-menu-title="Pacemaker DRBD" -->
## Pacemaker DRBD

<img class="full-slide" alt="pacemaker-drbd-1" data-src="images/hands-on/06-pacemaker-drbd-1.png" />


<!-- .slide: data-state="normal" id="pacemaker-haproxy" data-menu-title="Pacemaker Haproxy" -->
## Pacemaker Haproxy

<img class="full-slide" alt="pacemaker-haproxy" data-src="images/hands-on/07-pacemaker-haproxy.png" />


<!-- .slide: data-state="normal" id="pacemaker-hawk" data-menu-title="Pacemaker Hawk" -->
## Pacemaker Hawk

<img class="full-slide" alt="pacemaker-hawk" data-src="images/hands-on/08-pacemaker-hawk.png" />


<!-- .slide: data-state="normal" id="pacemaker-deployment-1" data-menu-title="Pacemaker Deployment 1" -->
## Pacemaker Deployment 1

<img class="full-slide" alt="pacemaker-deployment-1" data-src="images/hands-on/09-pacemaker-deployment-1.png" />


<!-- .slide: data-state="normal" id="pacemaker-deployment-2" data-menu-title="Pacemaker Deployment 2" -->
## Pacemaker Deployment 2

<img class="full-slide" alt="pacemaker-deployment-2" data-src="images/hands-on/10-pacemaker-deployment-2.png" />


<!-- .slide: data-state="normal" id="pacemaker-drbd-2" data-menu-title="Pacemaker DRBD 2" -->
## Pacemaker DRBD 2

<img class="full-slide" alt="pacemaker-drbd-2" data-src="images/hands-on/11-pacemaker-drbd-2.png" />


<!-- .slide: data-state="normal" id="pacemaker-apply" data-menu-title="Pacemaker Apply" -->
## Pacemaker Apply

<img class="full-slide" alt="pacemaker-apply" data-src="images/hands-on/12-pacemaker-apply.png" />


<!-- .slide: data-state="normal" id="crm-nodes-status" data-menu-title="Check nodes status" -->
## Check status of cluster nodes and remotes

Login to one of the controller nodes, and do:

<img class="full-slide" alt="Screenshot of running crm status"
     data-src="images/hands-on/30-crm-status-1.png" />

<img class="full-slide" alt="Screenshot of stonith/remote resources"
     data-src="images/hands-on/31-crm-status-2.png" />