#Islandora 7.x-2.0 General Design Doc

Islandora is lightweight, scalable middleware that connects a Fedora Commons JCR with a Drupal CMS and offers a pipeline of RESTful services for the common tasks such as thumbnail generation and metadata extraction.

### Design Summary
In the end, Islandora is built on the premise of using the right tool for the right job, and there's plenty of different jobs that all have to get connected together.   That's why it's middleware.  Shoehorning all tasks through a single solution is inappropriate, and leads to unsatisfactory results.  A JCR is not a relational database, which in turn is not a triple store.  A preservation system shouldn't be serving thumbnails, they should reside on a CDN.  A web server shouldn't be converting video files, it should be serving web pages.

In order to achieve this, Islandora adheres to the following design principles:

##### Decoupled
Although Islandora connects two popular pieces of software, it references neither unless absolutely neccessary.

##### Asynchronous
Islandora makes extensive use of messaging and queues, so that data can be processed when and where appropriate.

##### Distributed
The all-in-one setup is fine for small organizations with small amounts of data, but heavy usage and content will quickly crush even the beefiest of servers.  All of the important components that Islandora glues together are capable of running on individual hardware.  This includes but is not limited to:
- Fedora
- Drupal (Both web server and db)
- Services pipeline
- Activemq
- Logging

##### Invisible
Fedora content are Nodes, and therefore first-class Drupal citizens.  This opens up the whole Drupal ecosystem to the Islandora community.  The end user feels like they are using Drupal, with changes automatically making their way to Fedora.  Conversely, content manipulation directly in Fedora is reflected in Drupal.

##### Installable
With a stack this big, installation is too complicated to be manually left up to the user.  Each component has installation scripts, which can be combined to construct any type of infrastructure that fits the need of your organization.

##### Flexible
Each organization has different needs, utilizing different metadata standards with different types of data.  If options for manipulating, displaying, and processing a particular type of content are not out-of-the-box with Islandora, adding it is straight forward.
