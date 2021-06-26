Step 1:
**Download the stable release of zookeeper from here**
[Zookeeper](https://zookeeper.apache.org/releases.html "Zookeeper Download")

Step 2:
Extract the zookeeper in local directory

Step 3:
Go to `/zookeeper/bin/` directory and start the zookeeper server using below command

`bin/zkServer.sh start`

Step 4:
Connecting to zookeeper.
Use below command

`bin/zkCli.sh -server 127.0.0.1:2181`

Commands available under zookeeper cli
* get path [watch]
* ls path [watch]
* set path data [version]
* delquota [-n|-b] path
* quit
* printwatches on|off
* createpath data acl
* stat path [watch]
* listquota path
* history
* setAcl path acl
* getAcl path
* sync path
* redo cmdno
* addauth scheme auth
* delete path [version]
* setquota -n|-b val path


************************
1. Start with listing down znodes
    * `ls /`

2. Create a znode
    * `create /zk_sample sample_data` - This creates a new znode and associates the string "sample_data" with the node
   
3. Verify that the data was associated with the znode
    * `get /zk_sample`
    
4. Delete a znode
    * `delete /zk_sample`
    
5. Running Replicated ZooKeeper
Running ZooKeeper in standalone mode is convenient for evaluation, some development, and testing. 
ZooKeeper in replicated mode in prod env.<br/>
A replicated group of servers in the same application is called a quorum, and in replicated mode, all servers in the quorum have copies of the same configuration file. 
<br/>The file is similar to the one used in standalone mode, but with a few differences. 

    Here is an example:

    * tickTime=2000
    * dataDir=/var/zookeeper
    * clientPort=2181
    * initLimit=5
    * syncLimit=2
    * server.1=zoo1:2888:3888
    * server.2=zoo2:2888:3888
    * server.3=zoo3:2888:3888

6. Run a service in a particular zookeeper cluster.
For example:<br/>
**Running a SOLR service**
    * `./solr start -c -z localhost:2181/zk_sample`