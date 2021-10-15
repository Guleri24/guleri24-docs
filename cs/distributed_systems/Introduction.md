# Distributed Systems
A set of coperating computer that are communicating each other over a network
to get some coherent task done.

## Why people want distributed systems?
Parallelism
Fault tolerance
Physical Reason e.g transactions b/w to banks located in different countries.
Security/isolated

## Challenges
Concurrency
Partial failure
Performance

## Infrastructure
Storage
Comminucation
Computation

## Implementations
Tools
    RPC - Remote Procedure Calls
    Threads
    Concurrency Control
    

### Performance
We want `Scalable Speed-up`.
Scalability - 2x computers -> 2x throughput


e.g

person - Px
web server - ws
database - db

P1 --- ws-----db
              |
P2 --- ws-----|
     /        | 
P3--/         |  
:             | 
:             |  
Pn --- ws-----|

* Scalability
Is not infinte bcz at some time when 20 - 30 webservers all 
taking to the same database. Now, suddenly the database starts to be the
bottlenek. So, adding more webserver no longer helps.


### Fault Tolerance
* Availability
Under certain set of failure, some device continue providing
service.
* Recoverability
Storages 
* Replication

### Consistency
e.g Key-Value Service
        Put(k, v)
        Get(k) -> v

Types of Consistent system:
* Strong - Expensive spec to implement as to make consistency even if the 
server crashes which updates the values in the replicated systems.
* Weak 

People would love to put the replicates as far apart as possible, in different cities
or on the opposite side of the continent if in case an earthquake destory one data center
is extremely unlikely destroy the other data center.
But this comes with a drawback of retriving the data bcz it make take 1ms - 10ms - 30ms to
get that data from one data center to another.

## MapReduce
Doing giant computations 
Map produces key-value pair data
Reduce

### Word Count

Word Files           Intermediate Key/Values                    
Input 1 ------>Map  |a,1| |b,1| |   |
                    |   | |   | |   |
Input 2 ------>Map  |   | |b,1| |   |
:                   |   | |   | |   |   
:                   |   | |   | |   |
Input n ------>Map  |a,1| |   | |c,1|
                    ----- ----- -----
                      |     |     |  
                      |     |     |---------> Reduce -> c,1 
                      |     |---------------> Reduce -> b,2
                      ----------------------> Reduce -> a,2

The whole computation is called a `job` and every map|reduce is called a `task`.

Map(k,v)
    split v into words
    for each word w
        emit(w, "1") // 1 is the value
        
Reduce(k, v) 
    emit(len(v))
    
                           
