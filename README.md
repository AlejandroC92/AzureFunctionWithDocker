# Azure Function With Docker

This article will focus on the basic understanding of Docker and Azure Functions, and how we can combine both to have an application deployed and ready to be used in just a few minutes.

At the end of this reading, you would have a better understanding of Docker as a Container and Azure Function, and you should be able to follow along with the steps on how to install them in your local machine.

## Azure Functions
![Azure Function](https://s3-us-west-2.amazonaws.com/assets.site.serverless.com/blog/azure-functions-thumbnail.png)

Azure Function is Microsoft implementation of the concept Function as a service. It supports C#, Javascript, F#, Python, and some more are beeing added.

They are started off by [triggers](https://docs.microsoft.com/en-us/azure/azure-functions/functions-triggers-bindings), and you can have several types of triggers such as Timers, Messages, Http Requests, Blobs, or Database Triggers.

It's benefit is that you can focus your effort on developing your application without worring about the infraestructure behind.
To use Azure Function with Docker you need to download Azure Function Core Tool from [this link](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local) (I hightly recommend you npm for this task), the installation guide is quite simple.

Azure Function allows you to implement a Serverless Architecture, you can find out more about this topic in [Azure webpage](https://azure.microsoft.com/en-us/solutions/serverless/).

## Now Docker, but before that, let's talk a little bit about history.
Before [Containers](https://www.docker.com/resources/what-container), we had Virtual Machines, and before that, well, just Servers.

Why Virtual Machines on top of the servers? Because we can have multiple environments for our applications using a single Hardware unit. If we need more environments, we just configure new virtual machines.

<img src="/img/VirtualMachine.png" alt="drawing" width="520"/>

Now, the problem with that is not the functionality but the implementation. Having one virtual machine involve a lot of things; operative system for each one of them (and their licenses of course), "virtual hardware" configuration, resources management and a lot of time for administration teams. Now multiply that by the amount of virtual machines that you want.

With Containers we can eliminate these inconveniences. We have one smaller unit with much more less configuration and we just need one OS for all of them. They are also much more quicker to configure and start.

<img src="/img/Container.png" alt="drawing" width="520"/>

## What is Docker and how to install it.
<img src="https://www.docker.com/sites/default/files/vertical.png" alt="docker" width="180"/>

Docker is one implementation of a Container, the way VMWare is one implementation of Virtual Machines.
With Docker we can have all we need to run our application. 

You can download the installer after registration from [this link](https://store.docker.com/editions/community/docker-ce-desktop-windows) for Windows, follow the wizard steps and check if everything went right by typing "docker version" in the console.

<img src="/img/DockerVersion.png" alt="cmd" width="520"/>

## Putting all together
Now that we have the basic understanding of both technologies, let's build our HelloWorld application with Azure Function hosted in a Docker Container.

To do so, create a folder called Docker and enter there from the console.
Now, type the following command

```
funct init . --docker
```

Now select the worker runtime, in our case this would be dotnet and press enter.
<img src="/img/WorkerRuntime.png" alt="drawing" width="320"/>

Basically what we did was setting up the configuration for the container.

Now we can type the next command to create our function and choose a template, in our case the HttpTrigger

```
funct new
```
<img src="/img/CmdFuncName.png" alt="drawing" width="520"/>

And the last two steps we need to have our function up and running into a Docker Container is to build the container and run it.
```
docker build -t helloworldimage .
```

```
docker run -p 8080:80 helloworldimage
```


This second command would map the container port 80 to our localhost port 8080

Now you can enter http://localhost:8080/api/HelloWorld?name=ale 
and we finish our first application !

<img src="/img/HelloWorldHttp.png" alt="drawing" width="520"/>


## Where to start and what's next
For more information you can visit the following links and also check Pluralsight where you can find tons of courses about this topic.
- https://docs.microsoft.com/en-us/azure/azure-functions/
- https://training.play-with-docker.com/
- https://runnable.com/docker/advanced-docker-compose-configuration


Also, I have to mention some of the sources wich help me put this article together
- https://blog.leitwolf.io/azure-functions-docker-getting-started/
- https://markheath.net/post/azure-functions-docker

Thanks for your time and have a nice coding day!
