# Building On The Shoulders Of Giants

Independent Software Vendors (ISV) - situation & trends of modernization

## A legacy of vendor lock-in

Independent Software Vendors (ISVs) are becoming increasingly wary of vendor lock-in, and rightly so. For several years, they've been struggling to break free from the lock-in effects of databases, application servers and other proprietary middleware technologies that they have inherited from the previous era. As many of these ISVs embark on the journey of application modernisation and innovation, it is important for them to avoid the pitfalls of the dreaded lock-in again.

Adoption of open source technologies is crucial for ISVs. By leveraging standards based open source building blocks, ISVs stand to retain full control of their intellectual property. Open source databases like PostgreSQL and MongoDB, and application stacks like Spring Boot are great examples of such building blocks.


## Impact of Cloud Computing

Cloud computing is seen by customers as an empowering platform that enables them to consume applications on demand, and pay only for what they use. Over a long term, this translates to reduced technical debt for customers.

For ISVs, cloud computing is a key enabler for application modernization. Established ISVs are increasingly facing stiff competition from new born-in-the-cloud challengers who, being free from the shackles of technology debt and legacy vendor lock-in, have been able to innovate rapidly. What has enabled these challengers to become a disruptive force is the agility offered by the cloud. Adoption of managed services lets them focus on the things that make their products unique instead of investing time and money on undifferentiated IT tasks like procuring and managing infrastructure. By letting cloud service providers take care of common IT tasks, these born-in-the-cloud businesses are able to invest considerably more on innovation and product differentiation. For example, Grab - the leading ride hailing business in Southeast Asia, [saved 30%-40% cost in resourcing and manpower which it was able to invest in serving their customers better](https://youtu.be/z_ezu1C8CLM).

Cloud offers unprecedented opportunities for experimentation, which is the essence of product development. Product teams gain agility put ideas into action, measure customer feedback and then adapt quickly. This tight feedback loop fuels increased pace of innovation. This is made possible by the on-demand availability and consumption based billing model of many of the managed services offered by cloud service providers. It translates to lower cost of experimentation, faster product development cycles and higher returns on investment. It’s a flywheel of innovation like below:

![Illustration of flywheel of innovation](http://kapilpen.s3-website-ap-southeast-1.amazonaws.com/img/on_shoulders_of_cloud_giants/flywheel_of_innovation.png)


## The question of cloud lock-in

While this sounds great, it does come with a trade off. Cloud Service Providers (CSPs) themselves are innovating at a very fast clip. They are developing based on their own customer feedback loops, and as a result most of the managed services from CSPs have there own unique interfaces. These interfaces are not consistent across CSPs. This means if an ISV is to develop their product using a managed non-relational database service from a CSP, deploying that product on-premise would require the ISV to implement the functionality of that managed service by itself. This could be a non-trivial task, and it gives the notion of vendor lock-in, this time the vendor being the CSP.

This can be avoided by steering clear of managed services, however that’d mean trading the substantial benefits of agility for retaining cloud freedom. Not an easy choice considering what the customers want and what the competition is doing.

A reality check is truly warranted here. How real is the need to support on-premise deployments? And is that an immediate need or a vague distant possibility? For most ISVs, the answer will be the latter. Very few customers truly require on-premise deployments, and those customer opportunities are typically very long sales cycles. Often times, such customers are willing to explore cloud deployment as long as their security and compliance requirements are addressed.

If that is the case, does it make sense to sacrifice agility **today** for the sake of a presumptive opportunity that is merely a vague distant possibility?

Let’s compare how the journeys along these 2 paths would play out.

![Illustration of flywheel of innovation](http://kapilpen.s3-website-ap-southeast-1.amazonaws.com/img/on_shoulders_of_cloud_giants/cloud_vendor_lock_in.png)

In this approach, innovation is given priority which enables rapid development of new product features for customers who consume the product on the cloud. However, when there is a need to deploy the product on-premise, it is difficult to estimate the change effort, and many often require re-implementation of significant portions of the product.

![Illustration of flywheel of innovation](http://kapilpen.s3-website-ap-southeast-1.amazonaws.com/img/on_shoulders_of_cloud_giants/solo_safari.png)

In the second approach you spend valuable investment on building basic undifferentiated functionality in order to keep the application architecture ready for the eventual possibility of on-premise deployment. Note that there is often no clear customer project to which this investment can be attributed to. Fast forward a few years and look back - this will appear to be fairly chunky technical debt.

## Staying cloud agnostic seems logical, but at what cost?

### Pace of innovation 

### Developer productivity

### Opportunity cost

## You can have the cake and eat it too

Protecting your intellectual property is important. But so are innovation, developer productivity and being able to seize opportunities.

1. Define what your intellectual property really is
2. Set guardrails to protect it
3. Build a layer of encapsulation (example implementation for Lambda and S3)
4. Adopt a Data Access Layer pattern (example implementation for DynamoDB and MongoDB)
5. Adopt Microservices architecture (example implementation of users, products & orders micro services with each handling its own data store via a DAL)
6. Implement CI/CD (example implementation using Serverless Framework & CodePipeline)
7. If your application is single tenant, and if there is a business need to be able to run on-premise

Clearly, it is important to be able to innovate at a fast clip. It is equally important to be able to deploy the product on-premise when the need arises - for example for customers who operate in highly regulated industries that are yet to embrace the cloud.

I propose an architectural pattern that lets you get the best of both worlds. An adaptor pattern.

I need order to innovate rapidly, empower your product developers to use managed services, but mandate that every such use of a managed service is through a layer of encapsulation. At first this layer doesn’t do much more than simply relay the API calls to managed services and their responses. It’ll be a very thin layer, but it forces your developers to keep your application core logic separated from cloud dependencies. It’s a clear line of separation which makes it easier to port the application to on-premise environment when the need arises.

When it’s time to deploy on-premise, it’s now easy to scope the effort and attribute it to the specific customer project. For the components that don’t have any on-premise equivalents, adaptors can be implemented without touching the core of the application.

![Illustration of flywheel of innovation](http://kapilpen.s3-website-ap-southeast-1.amazonaws.com/img/on_shoulders_of_cloud_giants/adaptor_pattern_ftw.png)

This is not just an architectural pattern, but also it’s an alignment of standard software development best practices with specific business goals - increased agility without sacrificing full control over intellectual property.


 Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc3Nzc3MDA5OCwtMjA5NjA4NTEwMiwyMT
M3OTUwNDk0LDEzNDI5NDcxOV19
-->