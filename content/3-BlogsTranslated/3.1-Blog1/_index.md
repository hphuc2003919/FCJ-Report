---
title: "Blog 1"
date: 2025-09-09
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# Streaming Windows Games using Proton 9 on Amazon GameLift Streams

Players expect instant, click-to-play experiences across any device, and Amazon GameLift Streams helps customers build these experiences for games and streaming application use cases. While playing video games traditionally relies on the Windows operating system, Amazon GameLift Streams can run Windows-based games, or applications, on a Windows or Proton runtime.

**Proton** is a compatibility layer that enables Windows executables to run on Linux-based operating systems. Proton achieves this by translating Windows API calls, including graphics and input, to their Linux equivalents, allowing developers to leverage Linux servers for workloads previously limited to Windows.

With this approach, you can reduce your infrastructure costs by up to 63 percent when running a game at the same tenancy and maintaining a comparable performance as with a Windows runtime. Linux also enables you to use multi-tenancy and run two streams from a single GPU, which can reduce your cost further.

We are announcing the availability of **Proton 9** as a runtime option for Amazon GameLift Streams, improving compatibility with Windows builds further than ever before. We’ll dive deeper into how Proton 9 works, and how you can use it to reduce the cost of streaming Windows games or applications to your users.



## Amazon GameLift Streams concepts

**Amazon GameLift Streams** helps you stream games at up to 1080p resolution and 60 frames each second to any device with a browser. Using the AWS global footprint and GPU instances, you can deploy and stream your game content in minutes, without modifications, and players can start gaming in seconds without having to wait for installs. Amazon GameLift Streams uses key terminology and constructs to allow for quicker setup and stream management. Understanding these terms helps with configuring these options:

- **Runtime environment**: The underlying operating system and software running on Amazon Elastic Compute Cloud (Amazon EC2) instances behind the scenes that runs your application. Options include: Windows, Ubuntu, and Proton.
- **Stream class**: Defines the Amazon EC2 instance type and the number of streams running on one instance.
- **Stream group**: A construct consisting of your application, stream class, and stream capacity.
- **Stream capacity**: A numeric value representing how many stream sessions the stream group can run concurrently.


## Understanding Proton

Proton is an open-source compatibility layer developed by Valve in collaboration with CodeWeavers to enable Windows games to run on Linux systems. At its core, Proton relies on Wine Is Not an Emulator (Wine), which provides Windows API translation capabilities. However, Wine can struggle with modern 3D graphics making it difficult to reliably use it for modern 3D games.

Proton enhances the capabilities of Wine to deliver an advanced DirectX-to-Vulkan (DXVK) translation layer. It translates the Windows specific graphics API calls (DirectX), to the graphics APIs running on Linux (Vulkan). DXVK supports DirectX 9, 10 and 11 API translation. For DirectX 12, vkd3d-Proton is added as a further translation bridge. With these systems, Proton converts the latest Windows graphics and non-graphics API calls into the equivalent Linux and Vulkan operations.

![Figure 1](/images/Blog1-Image-1.png)
> *Figure 1. A diagram of which system calls which translation layer.*

Amazon GameLift Streams packages custom-built Proton versions: 8.0-2c, 8.0-5, and now 9.0-2, 2024 that have been specifically optimized for the underlying infrastructure and streaming technology.

## Technical and economical advantages

The benefits of using a Proton 9 runtime in Amazon GameLift Streams instead of a Windows runtime extends beyond saving licensing costs. Windows runtime stream classes, such as `gen5n_win2022`, carry the overhead of a Windows Server 2022 license fee, and operate in a single tenant mode. In single tenant mode each machine can only serve a single stream session.

Alternatively, a stream group using a Linux-based stream class can be multi-tenanted; for example, a `gen5n_high` serves two stream sessions from a single GPU, while also eliminating licensing costs. The underlying Amazon EC2 instance is exclusive to you even when running multiple stream sessions from a single instance. For less demanding games or applications, Proton 9 can be an important mechanism to optimize the overall infrastructure cost.

The chart (Figure 2) compares the cost for each stream hour across various stream classes in the Ohio AWS Region, with each bar labeled by class and tenancy ratio (1:1 or 2:1). It visually shows that Linux-based classes using Proton 9 support multi-tenancy (2:1), decreasing costs by enabling multiple streams for each machine and eliminating Windows licensing fees.

![Figure 2](/images/Blog1-Image-2.png)
> *Figure 2: Comparison of cost for each stream hour of stream classes in Ohio.*

## Testing game compatibility with Proton 9

However, the transition to Proton 9 is not without technical considerations. Some anti-cheat software requires either Linux compatibility configurations or a build without Anti-Cheat. Any operations at the kernel level may require specific configuration. Further, your game may use operations which are not able to be translated perfectly for use with the Vulkan graphics APIs.

If you run into compatibility issues with a Proton runtime, we encourage you to first test the latest Proton 9 runtime available in Amazon GameLift Streams. If you still encounter issues, we provide a guide on how to set up an Amazon EC2 equivalent for testing and debugging Proton compatibility issues.

## Further cost optimization methods

Using Proton 9 is a great way to share GPUs and eliminate the Windows license cost, so you can right-size the stream class for your game needs. Cost optimal features are key for consumer facing use cases, and Amazon GameLift Streams has further functionality to help customers manage costs for their streaming use cases.

It is important to know your stream capacity. Stream capacity is when customers can set the number of immediately available streams through an API call or through the AWS Management Console. Setting the stream capacity at or close to the number of streams you require means you’re not paying for capacity that you do not need. You can grow or shrink the amount of capacity manually, or automatically by calling the Amazon GameLift Streams API based on events (such as an increase in players, or based on a time period (for example, the same time every day)).

For use cases where users can wait for up to five minutes for a stream to load (typically for internal business use cases), customers can make use of on-demand stream capacity. This is where stream capacity is only initiated on a stream request, and then de-provisioned when a stream ends. This means customers pay only for stream capacity when it is requested by a user, and only for the duration of that stream session.

## Conclusion

The new Proton 9 runtime brings wider compatibility with DirectX 12 and fixes the issues identified in earlier versions. Paired with the latest stream classes on Amazon GameLift Streams, you can optimize the cost of streaming AAA titles and further reduce it with multi-tenancy options where the performance requirements of your games allow it.

Contact an AWS Representative to know how we can help accelerate your business.