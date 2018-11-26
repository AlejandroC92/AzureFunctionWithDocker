# Azure Function With Docker
Azure Function with Docker

This article will focus on the basic understanding of Docker and Azure Functions, and how we can combine both to have an application deployed and ready to use in just a few minutes.

At the end of this reading, you would have a better understanding of Docker as a Container and Azure Function, and you should be able to follow along with the steps on how to install them in your local machine.

But before that, let's talk a little bit about history. Before Containers, we had Virtual Machines, and before that, well, just Servers.
[imagen]
Why Virtual Machines on top of the servers? Because we can have multiple environments for our applications using a single Hardware unit. If we have our virtual machines setup ready, and we need more environments for our applications, we just configure news virtual machine.
[imagen]
Now, the problem with that is not the functionality but the implementation. Having one virtual machine involve a lot of things; operative system (and their licenses of course), "virtual hardware" configuration, resources management and a lot of time for administration teams. Now multiply that for the amount of virtual machines that you want.

With Containers we can eliminate these inconveniences. We have one smaller unit with much more less configuration and we just need one SO for all of them, as you can see in the image below.
[imagen]
