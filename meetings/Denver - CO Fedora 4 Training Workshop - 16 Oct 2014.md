# Denver, CO Fedora 4 Training Workshop - 16 Oct 2014

## Links

* [Denver, CO Fedora 4 Training Workshop - 16 Oct 2014](https://wiki.duraspace.org/display/Events/Denver%2C+CO+Fedora+4+Training+Workshop+-+16+Oct+2014)
* [Training - Administrator Introduction](https://wiki.duraspace.org/display/FF/Training+-+Administrator+Introduction)

## Notes

### Introduction and Feature Tour

* Core Preservation Components
  * Fixity
    * basically same setup at 3.x
    * but it is only SHA1
    * the SHA1 determines where the object is on the disk
  * Backup and Restore
  * Export and Import
    * a specific Fedora object
    * exported objects are serialized (JCR xml)
    * an exported object or hierarchy of objects can be imported at anytime
  * Versioning
    * version can be created via API
    * previous versions can be restored via the API
* Data Modeling
  * Resources
    * both objects and datastreams are represented as resources
    * object resources can have both objects and datastreams
    * tree structure allows for inheritance of things like security policies
  * Properties
    * resources have a number of properties (expressed as RDF triples)
    * properties can be RDF literals or URIs
    * any number of RDF namespaces can be defined and used
  * Content Models
    * content can be modeled using Compact Node Definitions (CNDs)
    * Mixins can be used to define any number of properties
    * objects can inherit properties from any number of mixins
  * Linked Data
    * F4 is compliant with the LDP 1.0 spec
    * metadata can be represented as RDF triples that point to objects outside the repository
* External Components
  * Indexing
    * index repository content for external applications with the JMS Message Consumer
    * the consumer replays repository objects to one more external applications
    * repository content needs to be assigned the rdf:type property "indexible"
    * no GSearch
  * Role-based Authorization
    * Role-based authorization compares the user's role(s) with an Access Control List defined on a Fedora resource
    * ACLs can be inherited; if a given resource does not have an associated ACL, Fedora will examine parent resources until it finds one
  * XACML Authorization
    * a default policy must be defined for the repository, and each resource can override the default with another policy
    * a XACML policy reference by a resource will also apply to all the resource's children, unless they define their own xacml policies
  * Transactions
    * multiple actions can be bundled together into a single repository event
    * transactions offer performance benefits by cutting down on the number of times data is written to the repository filesystem (usually the slowest action)
  * Clustering
    * two or more fedora instances can be configured to work together in a cluster
    * fedora currently supports clustering for high-availability use cases
    * a load balance can be setup in front of two or more fedora instances to evenly distribute read requests across each instance

### Migrating From Fedora 3 to Fedora 4

* XML Objects vs. Resources
  * Fedora 3
    * FOXML objects
    * Inline XML and XML datastreams
  * Fedora 4
    * Web resources (Objects & datastreams)
    * RDF properties
* Flat vs. Hierarchy
  * Fedora 3
    * Objects and datastreams at the top level
    * no inheritance tree structure
  * Fedora 4
    * objects and datastreams in a hierarchy
    * all resources descend from a root node
  * File system
    * Fedora 3
      * objects directory and datastreams directory
      * both objects and datastreams are in a PairTree
    * Fedora 4
      * objects directory and datastreams directory
      * datastreams in a PairTree
      * objects in a database (e.g. LevelDB)
  * PID vs. Path
    * Fedora 3
      * object have a PID
      * PID can never be altered
    * Fedora 4
      * objects have an internal ModeShape UUID
      * objects have a repository path
        * this can user-defined or generated via a PID-minter
  * Ingest or Projection?
    * Fedora 4 supports projection over content in an external system
    * project over Fedora 3 REST-API is possible
  * Security
    * what kind of security does your Fedora 3 repository use?
    * many Fedora 3 repositories use XACML
  * Versions
    * does your Fedora 3 repository use versioning
    * Fedora 3 versions must be iterated through to create new version in Fedora 4
    * How should version dates be handled? Will you use the system modified date, or a special date property
  * Content Models
    * How are content models used in your Fedora 3 repository
    * Do they have any logic built into them, or is that handled at a higher application level? (Hydra/Islandora)
  * Disseminators
    * Does your Fedora 3 repository make use of disseminators?
    * What are they used for? XSL transforms? Derivatives?
    * How can we support the existing disseminator use cases in Fedora 4 without recreating disseminators?
* Enhancements
  * Taking advantage of properties
    * lightweight and granular compared to XML
    * inline xml is no longer supported
    * converting inline xml and/or xml datastreams (RELS-EXT/RELS-INT) to RDF properties
  * Enhancing your metadata
    * XML metadata datastreams are still supported, but there are new opportunities to explore
    * XML metadata can be converted into RDF metadata using an RDF-based schema
    * RDF metadata is easier to query and share
    * take advantage of linked data by pointing to authority URIs
