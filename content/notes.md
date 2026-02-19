The Solid project [1] aims to create a decentralized personal data ecosystem based on open standards. Within this
ecosystem, each user retains control over their data. Users expose their data through a collection of HTTP resources
linked via the Linked Data Platform (LDP) [2] specification, forming what is known as a Solid pod. When querying data
within a Solid pod, data consumers—such as developers and data analysts—encounter challenges related to data access path
dependencies [3]. This means they must know which resources are exposed through which interfaces.

One approach to addressing this issue is to traverse the links of every exposed resource [4,5]. However, this method
does not scale well as the number of resources increases. To mitigate this, the specification introduces mechanisms to
describe the relationships between RDF resources and the interfaces that expose them. The type index [6] and shape
tree [7] specifications explicitly define such relationships, reducing the search space to a limited number of HTTP
resources, effectively functioning as indexes. Since the Solid project emphasizes keeping the server simple, the
responsibility for managing these indexes falls on the client.

However, when creating or updating RDF resources in a Solid pod, existing descriptions do not provide sufficient
guidance on where to store or modify resources. This is because an updated resource description may match multiple HTTP
resources, leading to several key questions:

Should the RDF resource be exposed in all matching HTTP resources, only some, or just one?

What should be done if no HTTP resource matches?

What happens if a resource is updated? Can it be modified in place? Should it be relocated? Does its description change?

To address these questions, we introduce the Storage Guidance Vocabulary (SGV). This vocabulary allows Solid pod
structures to be described using client-managed SGV descriptions.