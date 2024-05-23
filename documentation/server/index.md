---
redirect_from:
  - "/server/"
  - "/server/guides/"
  - "/server/guides/deployment/"
  - "/server-apis/"
  - "/documentation/server/guides/"
  - "/documentation/server/guides/deployment"
layout: page
title: Swift on Server
---

Swift is a general-purpose programming language originally developed by Apple for building iOS, macOS, watchOS, and tvOS applications. Swift also has unique characteristics that make it specifically suitable for server applications. Swift provides developers with a modern, safe, and efficient option for writing server-side code. Swift combines the simplicity and readability of a high-level language with the performance and safety features of a compiled language, allowing developers to leverage their existing Swift skills to build complete end-to-end solutions using a single programming language.

The [Swift Server Workgroup (SSWG)](/sswg/) is a steering team dedicated to advancing Swift for server applications. They define and prioritize initiatives that meet the needs of the Swift server community and run an incubation process to enhance compatibility and promote best practices. 


## Overview

Swift’s performance is comparable to languages like C and C++, making it well-suited for building high-performance server applications. Thanks to the progressive and efficient design of the language, Swift server-side applications can handle large-scale workloads with high performance and low resource consumption.

Cloud services built with Swift have a small memory footprint (measured in MB), especially compared to other popular server languages with automatic memory management. Services built with Swift are also CPU-efficient, given the language’s focus on performance.

Swift-based applications quickly start since there are almost no warm-up operations, making Swift an ideal fit for cloud services, which are often rescheduled onto new virtual machines (VMs) or containers to address platform formation changes. 

Swift enforces both type-safety and memory safety features, such as optionals, [Automatic Reference Counting (ARC)](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/automaticreferencecounting/) and ownership features, that help prevent common programming errors and improve code reliability. Backend applications written in Swift benefit from these robust language features, making them less prone to crashes, memory issues and security vulnerabilities.

Swift provides [built-in support for concurrency](https://developer.apple.com/documentation/swift/concurrency/), allowing developers to write scalable and responsive server applications. Swift’s concurrency model makes it suitable for developing highly concurrent server applications.

### Why use Swift as a backend language?

The benefits of using Swift on Server:

- Performance (quick startup-time)
- Efficiency (low memory and CPU footprint)
- Multi-threading (built-in concurrency support)
- Safety (type, memory and thread safety)
- C/C++ interoperability

TODO: benchmarks, statistics...

Overall, Swift on Server opens up new opportunities for developers to build fast, scalable, and secure backend services. Swift's combination of performance, readability, interoperability, safety, and modern language features make it a compelling choice for many developers.


## How to get started?

To build and run Swift applications on the server, developers can make use of web frameworks such as [Vapor](https://vapor.codes/) and [Hummingbird](https://swiftpackageindex.com/hummingbird-project/hummingbird) which provide a variety of tools and libraries to streamline the development process. These frameworks handle important aspects like routing, database integration, and request handling, allowing developers to focus on building the business logic of their applications.

### Development guides

- [Hello, World! - Vapor](/documentation/server/guides/basics/hello-world-vapor/)
- [Hello, World! - Hummingbird](/documentation/server/guides/basics/hello-world-hummingbird/)

### Technical guides

The Swift Server Workgroup and Swift on Server community have developed several guides for using Swift on the server.
They are designed to help teams and individuals running server-side Swift applications on Linux, including orientation for those who want to start developing with Swift.

The following guides focus on how to compile, test, deploy, and debug applications and provide tips in those areas:

- [Setup and code editing](/documentation/server/guides/setup-and-ide-alternatives.html).
- [Building](/documentation/server/guides/building.html).
- [Testing](/documentation/server/guides/testing.html).
- [Debugging Memory leaks](/documentation/server/guides/memory-leaks-and-usage.html).
- [Performance troubleshooting and analysis](/documentation/server/guides/performance.html).
- [Optimizing allocations](/documentation/server/guides/allocations.html).
- [Debugging multithreading issues and memory checks](/documentation/server/guides/llvm-sanitizers.html).
- [Packaging](/documentation/server/guides/packaging.html).

Additionally, specific guides exist for library developers:

* [Log Levels](/documentation/server/guides/libraries/log-levels.html).
* [Adopting Swift Concurrency](/documentation/server/guides/libraries/concurrency-adoption-guidelines.html).

_These guides are a community effort. Anyone is invited to share their tips and know-how by submitting pull requests to the [Swift.org site](https://github.com/apple/swift-org-website)_.

### Deployment guides

The following guides can help with the deployment to public cloud providers:

* [AWS Lambda using the Serverless Application Model (SAM)](/documentation/server/guides/deploying/aws-sam-lambda.html)
* [AWS Fargate with Vapor and MongoDB Atlas](/documentation/server/guides/deploying/aws-copilot-fargate-vapor-mongo.html)
* [AWS EC2](/documentation/server/guides/deploying/aws.html)
* [DigitalOcean](/documentation/server/guides/deploying/digital-ocean.html)
* [Heroku](/documentation/server/guides/deploying/heroku.html)
* [Kubernetes & Docker](/documentation/server/guides/packaging.html#docker)
* [GCP](/documentation/server/guides/deploying/gcp.html)

If you are deploying to your own servers (e.g. bare metal, VMs or Docker) there are several strategies for packaging Swift applications for deployment, see the [Packaging Guide](/server/guides/packaging.html) for more information.


### Other websites and tutorials

- [Swift on Server](https://swiftonserver.com/)
- [Articles, tools & resources for Vapor devs](https://blog.vapor.codes/)
- [The.Swift.Dev](https://theswiftdev.com/)


## Recommended packages 

The Swift ecosystem contains many useful libraries and tools specifically designed for server-side development. 

The Swift Server Workgroup has a process which allows a project to go through incubation stages until it graduates and becomes a recommended project.

The Swift Server Workgroup defines and implements an incubation process for server-side Swift packages to minimize duplicated efforts, enhance compatibility, and promote best practices. You can learn more about the details on the [SSWG Incubation Process](/sswg/incubation-process/) page. The current status and a more detailed overview of the incubated packages are available on the [SSWG Incubated Packages](/sswg/incubated-packages) page.

The SSWG publishes a [package collection](/blog/package-collections/) that contains the projects incubated by the workgroup. The collection is available at `https://swiftserver.group/collection/sswg.json`.

TODO: mention swift package index...

Here is a list of recommended server-side Swift libraries that have been incubated by the SSWG.

{% for group in site.data.server-workgroup.package_groups %}
<h3>{{ group.name }}</h3>
<ul>
  {% for package in group.packages %}
  <li>
    <h4>
      <strong>{{ package.name }}</strong>
    </h4>
    <section class="description">
      <p>{{ package.description }}</p>
      <p>
        <ul>
          {% for link in package.links %}
          <li><a href="{{ link.url }}" target="_blank"><small>{{ link.name }}</small></a></li>
          {% endfor %}
        </ul>
      </p>
    </section>
  </li>
  {% endfor %}
</ul>
<br>
{% endfor %}
