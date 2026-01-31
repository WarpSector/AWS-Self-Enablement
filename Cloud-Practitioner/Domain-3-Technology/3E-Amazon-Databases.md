# Domain 3: Technology
# (3E: Amazon Database Services)

## Types of Databases
  * #### Relational Databases
    * Organized by tables and rows.
    * Has a rigid schema (MySQL).
      * SQL is used to define the structure of the data and its elements.
      * SQL provides the tools to insert, update, delete, and querying data within the database table.
    * Typically scaled vertically.
    * Supports complex queries and joins.
    * **Examples:** Amazon RDS, MySQL, PostgresSQL, Oracle, IBM DB2.
  * #### Non-Relational Databases
    * Varied data storage models.
    * Flexible schema (NoSQL).
      * Data is stored in **key-value pairs**, columns, documents, or graphs.
      * There is no rigid schema so attributes can be missing or have different data types.
    * Scales horizontally.
    * Unstructured, simple language that supports any kind of schema.
    * **Examples:** Amazon DynamoDB, MongoDB, Redis, Neo4j.
  * #### Graph Databases
    * Designed to store, manage, and navigate relationships in data (e.g., Facebook).
    * Graph databases use:
      * Nodes to represent entities.
      * Edges to represent relationships.
      * Properties to store information about nodes and edges.
    * **Example:** Amazon Neptune.  

## Use Cases for Databases
  * #### Operational/Transactional
    * Online Transactional Processing (OLTP).
    * Production databases that process transactions (e.g., adding customer records, checking stock availability, etc.).
    * Short transactions, simple queries.
    * **Relational Examples:** Amazon RDS, My SQL, Oracle, IBM DB2.
    * **Non-Relational Examples:** MongoDB, Cassandra, Neo4j.
  * #### Analytical
    * Online Analytics Processing (OLAP).
    * The source data for OLAPs comes from OLTPs.
    * Data warehouse - typically separated from customer facing databases - data is extracted for decision-making.
    * Long transactions, complex queries.
    * **Relational Examples:** Amazon Redshift, Teradata, HP Vertica.
    * **Non-Relational Examples:** Amazon Elastic Map Reduce (EMR).
  * #### Amazon RDS and Amazon Redshift
    * Amazon RDS is Amazon's relational database service that ingests OLTP data (re: takes in transactional data).
    * RDS OLTP data is then copied into Amazon Redshift (Amazon's data warehouse service).
    * OLAP can then be performed on the OLTP data from RDS when copied into Redshift (performs data analysis, e.g., looking for trends in the data, etc.).
  * #### Amazon Databases
    * **Database on EC2:** full control over the database and instance, can load third-party databases that are not available in Amazon RDS.
    * **Amazon RDS:** traditional relational database, data is well-formed and structured (includes MySQL, PostgreSQL, Oracle, etc.).
    * **Amazon DynamoDB:** NoSQL database, dynamic scaling, useful for high I/O needs and in-memory (RAM) performance.
    * **Amazon Redshift:** data warehouse for large volumes of aggregated data.
    * **Amazon ElastiCache:** fast temporary storage for small amounts of data, in-memory (RAM) database.    

 ## Amazon Relational Database (RDS)
   * #### Overview
     * **Managed** relational database.
     * Used for transactional data processing (OLTP).
     * Runs on Amazon EC2 instances and stored in EBS block volumes.
   * #### Choice of DB Engines with RDS
     * **Amazon Aurora:** Amazon's proprietary relational database, MySQL & PostgrSQL compatibility, scalable, and very cost-effective (this is the important one to remember!).
     * MySQL
     * PostgreSQL
     * Oracle
     * Microsoft SQL    
   * #### Scaling
     * RDs is typically **scaled up** - you must stop and restart the scaled up instance.
     * Vertical scaling is required for enhanced **write** performance.
     * RDS can be **scaled out** using **RDS Read Replica**, which is a read-only copy of the RDS database that handles **read** requests while the original DB handles write requests - these can be **scaled out.**
   * #### Availability
     * You can create a **RDS Standby** copy in another AZ so you have multi-AZ deployment, which is essential for disaster recovery.
     * **RDS Standbys** are not used for scalability like Read Replicas are - their sole purpose is for failover and disaster recovery.   
## Amazon Aurora
   * #### Overview
     * AWS database offering in the Amazon RDS family.
     * MySQL and PostgreSQL compatiblity only.
     * 5x faster than MySQL and 3x faster than PostgreSQL.
   * #### Architecture
     * Aurora is a **regional** service. 
     * Aurora Primary sits in an AZ and serves as the primary for writes, while Aurora Replicas are spread across multple AZs to serve reads (up to 15 Replicas in a Region!).
     * Fault tolerance: Aurora is spread across 3 AZs.
     * **Single Logical Volume:** Data store volume is spread across multiple AZs in the Region.
     * Aurora has a serverless on-demand auto-scaling configuration available.  

## Amazon DynamoDB
  * #### Overview
    * Fully managed NoSQL database service.
    * Fully serverless.
    * Flexible data schema, key/value and document store.
    * Low latency (within milliseconds) access to data.
    * Horizontally scalable at the push of a button.
    * On-demand back-up and restore available.
  * #### Architecture 
    * Data is stored in partitions, which are replicated across multiple AZs (fault tolerant).
    * Highly available 99.99%, 99.999% for Global Tables.
    * Global Tables are a fully managed, mutli-region, and mutli-master solution that writes and reads to both Regions and the data is replicated in both tables.
    
## Amazon Redshift
  * #### Overview
    * Fully managed SQL-based data warehouse that stores transactional data loaded from Amazon RDS (OLTP).
    * Data can be analyzed using business intelligence (BI) tools (OLAP).
    * Redshift uses EC2 instances (it is not serverless).
    * Redshift always keeps three (3) copies of your data.
    * Redshift provides continous incremental backups.
   
   

