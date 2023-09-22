# Establishing SRE Foundations - A Step-By-Step Guide to Introducing Site Reliability Engineering in Software Delivery Organizations

## Chapter 2 - The Challenge
Users touch the product in productions, therefore, that touch point needs to be centric with all activities in the product creation life cycle. 

#### Example from the book
> The consequence of not thinking about production throughout the product creation life cycle can beillustratedusinganexamplefromthegroceryindustry.Imaginethatagrocerystorechainhasawide variety of products displayed in beautifully designed stores throughout the country, but neglects the checkout counters at the point of sale. The entire supply chain is working flawlessly, but issues arise at the checkout where the customers are trying to purchase their groceries: for example, they might not be able to pay for their groceries quickly, and the checkout queues might be getting longer. The checkout staff might not be able to resolve the issues themselves. The point-of-sale devices are supported by the operations team, which receives an enormous number of support requests. It turns out that the issues are with the software on the devices; the support team cannot resolve the software issues themselves.

> While the crisis is unfolding, the developers are happily working on new features for the point- of-sale devices. The product owners are happily specifying additional new features to be handed over to the developers after they finish the current work. The operations engineers are reaching out to the developers, who are not sure whether to prioritize the requests by the operations engineers or the features in development. The developers reach out to the product owners for a prioritization decision. Finally, the operations engineers, developers, and product owners swarm over the problem and decide to fix the product issues with the highest priority.

### 2.1 Misalignment 
* See Figure 2.1 which illustrates the preceding example of how a product delivery organization misaligned on operationsal concerns works. 

If productions is where the customers use the product, how on earth can it be less important than anything else? 

This frustration relfects a core issue in product delivery organizations that do not excel at operations. In such organizations, being product and user centric means different things to different parties. From a product operations point of view, it means produciton isses are tackled with the highest priority. From a product development point of view, it means features reqeusted by product owners are develped as quickly as possilbe. From a product management point of view, it means user stories requested by customers are turned into features in production as quicly as possible. This fundamental misalignment of what it means to be product and user centric when approaching product creation is one of the core reasons for difficulties in operating the product in production to the customer's satisfaction. This is where SRE shines, aligning the parties (Chapter 1, SRE brings together the three parties)

The three parties operate under three different flags

1. Product Operations runs under the Ops flag - they man production
2. Product Development runs under the Dev flag - they develop products new features
3. Product Management runs under the Product flag - they are all about the product and shape it in a fundamental way: What is it? Who are the customers? What is the competition? What is the product’s competitive advantage? What are the most important user journeys? What are the features? What is on the backlog?

It turns out that in a setup like this, no one really owns production operations. Who is it, indeed? Is it product operations? Not really, because they lack the knowledge necessary to truly own production operations. There is no proper continuous knowledge transfer from product development and product management toward product operations, and vice versa.

Is it product development? Certainly not. Their focus is the feature backlog. The feature backlog is void of product operations. Shipping occasional necessary production hotfixes after escalations from product operations is not what owning production operations actually means.

Is it product management? For sure it is not. Their focus is the definition of the product. Their expectation is that product development implements the product and product operations operates it in production. Despite the word owner in their title, the product owners do not own the product all the way to and including production.

### 2.2 Collective Ownership
