# Distributed computing

## Service Oriented Architecture (SOA)
- Stage in software development evolution and/or integration
- Defines a way of making components reusable, using interfaces
- Applications make use of services available in the network
- Services are provided through a network call to form applications
- Each service in SOA is a complete business function in itself

## Map - reduce
- Programming model
- Specialization of split-apply-combine strategy for data analysis
- Associated implementation for processing big data sets
- Done with a parallel and distributed algorithm on a cluster
- Contains:
    - *map* procedure: performs filtering and sorting
        - e.g.: sort students by first name into queues, one queue / name 
    - *reduce* method: summary operation
        - e.g.: counts no. of students in each queue, yields name freq.
- Where it performs best: on multithreaded implementations, multi-processor hardware

## Distributed cache
- Store data across multiple nodes instead of a single machine
- Scales easily and remains available even if a node fails
