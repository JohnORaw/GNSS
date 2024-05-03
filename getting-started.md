# Getting Started

People get really confused when they try to distinguish development and production. The term _“shrink-wrapped software”_ existed for products that were tested and deployed to such an extent that they worked, probably with many undiscovered bugs and vulnerabilities, but they basically worked. If I had to commit to having working accounts package for a company, I could buy this off-the-shelf, and easily understand its limitations by talking to current users. That is **production**.

If someone asks me to develop a custom telemetry system, which will communicate with a cloud repo via 5G modem, that is **development**.

If I have done projects like this before, I can estimate with some accuracy how long the project will take, what it will cost, and what its limitations will be. But until I have it working and deployed, I do not really know the answers to these things. If its a new discipline for me, any scope could be wildly wrong!

Always

* Do the initial reading before asking any questions or buying any hardware.
* Built and test a full prototype before committing to produce a result.

In this repo, I'm mostly using chips from UBlox, they have good manuals available online. Download the Interface Description and Integration Manuals and have them available for reference. You need UBlox U-Center software for configuration.

Rather than soldering wires to SMCs, I buy development boards and the best source I've found is Ardusimple. Bizarrely, they still have real people at the end of an e-mail query, who are knowledgeable and friendly. They have good wiring guides on their website, and they are scoring 100% with me on commercial activity. Buy you development boards from wherever but find the associated technical resources and limitations.

To learn the basis of GNSS, some folks from Stanford published a course on You Tube. Its GPS only and a little out-of-date, but it is the best starting place I've found.

The best blog I have found on RTK is [https://rtkexplorer.com/](https://rtkexplorer.com/), but don't bother accessing until you know the basics, this blog assumes some background knowledge.
