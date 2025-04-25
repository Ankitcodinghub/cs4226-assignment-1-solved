# cs4226-assignment-1-solved



**<span style='color:red'>TO GET THIS SOLUTION VISIT:</span>** https://www.ankitcodinghub.com/product/cs4226/

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;122198&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS4226 Assignment 1 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">
            
<div class="kksr-stars">
    
<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
    
<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>
                

<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
Objectives

Welcome to the CS4226 Laboratory Project. In this project, you’ll complete a set of exercises designed to help you get more familiar to network switching and routing, and learn basic programming with ONOS, a state-of-the-art distributed network operating system.

You are free to discuss this assignment with your friends. However, you should not share your answers, screenshots or network logs. We highly recommend that you attempt this assignment on your own and figure things out along the way as many resources are available online and the troubleshooting skills you learn will be very useful.

Question &amp; Answer

If you have any doubts on this assignment, please post your questions on Piazza forum or consult the teaching team. However, the teaching team will NOT debug issues for students. The intention of Q&amp;A is to help clarify misconceptions or give you necessary directions.

Figure 1: An example of network topology with 8 hosts, 4 switches and 12 links.

Submission

ONOS VM Image for Programming Assignment

You can download the ONOS + Mininet VM image for Programming Assignment here.

In this section, your task is to build a virtual network in the Mininet network emulation environment. The network topology is given in an input file. Below is an example of a network topology, consisting of 8 hosts, 4 switches and 12 links that connect them together, as shown in Figure 1. In this network, the 8 hosts (with IP addresses from 10.0.0.1 to 10.0.0.8) are connected with 4 switches (with dpid from 1 to 4) by 8 links. The 4 switches are then connected together by 4 links.

Your program need to build a network with the topology and specifications described in the input file “.in”. The first line of the file has 3 integers indicating that there are N hosts, M switches and L links in the network. The following are L lines of tuples in the form of &lt; dev1,dev2 &gt; that describe the links, meaning that dev1 and dev2 are connected via a bi-directional link at both directions. A partial input file for the network in Figure 2 looks like follows:

8 5 12 h1,s1 h2,s1 h3,s1 h4,s2

…

In this section, you will need to implement a traditional learning switch on ONOS. With your “learningSwitch” application installed in ONOS, any two random hosts should be able to ping each other.

In order for the hosts to communicate with each other, the switches need to know how to correctly route a packet to its destination. In this part, your task is to implement the application of self-learning switches using the ONOS controller, which enables the switches to learn how to route packets without any prior knowledge of the network.

The key idea is to record the MAC address and the corresponding port number when receiving a packet that does not match any entry in the forwarding table. Thus, the switches can gradually learn the port number for reaching each host in the network. In the following part, we provide a simple example for illustration.

Initially, the switch has no knowledge of the three computers A, B and C that connect to it as is shown in Figure 2a. When Computer A sends a frame to Computer B, the switch does not know how to route the frame. It then floods this frame to all the ports, hoping that Computer B could receive it and reply.

Although now the switch still knows nothing about Computer B, it has learnt that Computer

A can be reached by port 1. It then adds this entry into its forwarding table as is shown in Figure 2b, so that a frame destined for Computer A will be routed to port 1 in the future. Similarly, when the reply from Computer B comes back, the switch can subsequently learn that port 2 corresponds to Computer B.

In this section, you will implement a layer-3 firewall application using the ONOS controller. The application needs to block traffic flows: the TCP traffic sent to a certain host on a certain port. You will be using the test case in the ONOS walkthrough document to S

(a) Initial state. (b) Learning MAC address of A.

Figure 2: Example of a self-learning switch.

verify it. In particular, the test case specifies a firewall rule to block the TCP traffic from h1 to h4 on port 4001.

The basic idea is that we need to implement a ONOS CLI called add-firewall-on-port to manually install the rules on the ONOS controller.

Directory tree

.

app # ONOS application folder learningSwitch # Learning switch framework src/main/java/org/onosproject/learningSwitch

AddFirewallOnPortCommand.java package-info.java

macTableEntry.java # Helper class for MAC table

LayerTwoManager.java # Main learning switch logic

pom.xml # Maven configuration file

topos # Mininet topology folder star.py # Load star topology into mininet star.in # Input topology file of star structure

Todos

3. Implement “AddFirewallOnPortCommand” command line in “learningSwitch/”. (3

In this section, you will need to implement a simple reactive forwarding app that uses intent service. With your “intentForward” application installed in ONOS, any two random hosts can be connected via high-level, user-defined “Intent”.

In this exercise, we are going to implement packet forwarding in ONOS way. ONOS, as a networking operating system, has two distinct advantage comparing to tradition network: high-level application intention and global network topology view. This exercise is designed to elaborate these two aspects.

The fault-tolerance functionality of learning switch can be hard to implement in other SDN controllers such as POX. However, it can be natively supported in ONOS controller. In POX, the controller need to attach a time-to-live or TTL value to entries in the routing tables. Any outdated entry, i.e., an entry for which the duration between the current time and the creation time exceeds the TTL value, will be removed from the routing tables. After that, the switch can broadcast to construct a new routing table entry even if the network topology has changed. In contrast, ONOS intent-based controller can actively handle the link down/up events, and will update forwarding tables automatically.

You are expected to write a 2 pages report to summarize your programming experiences on implementing SDN controllers on ONOS. In addition, you need to submit a demo video that showcases your output for the test cases.

The report name should be &lt;Student Number&gt;.pdf. The main content should cover:

• Compare “learningSwitch” and “intentForward”, state in your opinion, how are they different from each other? Do they behavior differently with varied topology? • Difficulties faced during learning/programming on ONOS and how do you solved them?

The demo video length should be within 10 minutes and cover all test cases listed in the ONOS walkthrough document. The video name should be &lt;Student Number&gt;.mp4, where the video type needs to be .mp4.

Directory tree

.

app # ONOS application folder

intentForward # Intented fowarding framework src/main/java/org/onosproject/intentForward package-info.java

IntentReactiveForwarding.java # Main intented forwarding logic pom.xml

pom.xml # Maven configuration file

topos # Mininet topology folder ring.py # Load ring topology into mininet ring.in # Input topology file of ring structure

Todos
