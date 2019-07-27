# On Shoulders of Cloud Giants

That "Cloud is the new normal" is already old news. Cloud adoption is increasing across every market segment, including enterprises. This pervasiveness of cloud is a double edged sword for software producers. On one side there are benefits like:

- Faster time to market (hardware, licensing, managed services and support)
- Build a software as a service business with global audience
- Ability to scale infrastructure as quickly as business needs
- Low cost of onboarding new customers
- Faster time to market

However, in order to fully realize these benefits, software companies have to make some changes to their software architecture and operations. In this article, I have proposed an architectural approach called **Skinny Stack** that is designed to maximize these benefits. Microservices architecture has a [number of advantages as compared to monoliths](insert link here), but in order to run microservices you need to setup a number of auxillary systems like orchestration, service discovery, centralized logging and so on. These are essential components, but they not add any differentiation to your company's product. **Skinny Stack** builds on top of the concept of microservices, but the idea here is to build only those components that are central to the intellectual property of your company. Your team should not be building anything that does not add to the intellectual property of your company. For everything else, maximize the use of existing open source or commercial solutions.

Benefits of this:
- focus your resources on building your IP
- get more value out of a lean team
- your IP remains portable

Examples of this:
- arch that uses cloud services for things like auth, api gateway, message queues, databases, container orchestration services etc
- similar but serverless

Objections:
- vendor lock in (commercial)
- deployment in a different environment requires engineering changes
- learning new skills
