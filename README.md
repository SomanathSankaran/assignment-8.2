# assignment-8.2
1.Explain the core changes made in Hadoop 2.x
In Hadoop 1.x there is a main disadvantage related to NameNode (ie) Single point of Failure(if name node fails there will  be some loss of data despite having a secondary node as the updation from name node to secondary name node is done on  hourly basis)
So we come with the solution of HIGH AVAILABILITY OF NODE 
In Hadoop 2.x we have two name node (other than secondary name)namely
1.Active NameNode
2.Standby NameNode
Now  the Data node will send block reports to both Active NameNode and Standby NameNode
So if active NameNode fails or crashes Stand By Name node becomes active NameNode
Then how do we know how Active NameNode fails  .So for that we have Journal Node 
This works on the Basis of polling so if there are 3 journal nodes formula for calculated quorom is
(no of journal node + 2)/2(suppose 3 journal node (3+2)/2 =2)) while the expected QUOROM here is 2.
If active name node fails the journal count quorom will be less than 2 and the journal node automatically changes the 
Stand by name node as active name node and and when the failed name node gets up it will now be a standby and the process goes on 
HADOOP  FEDERATION 
In Hadoop 1.x  version there is only one name node which has a memory of 64 gB which could maintain  a cluster of 4000  data nodes.With increase in Data generation we are now running towards a scenario where say 10,000 data nodes may be required.SO  MORE MEMORY in NAMENODE is required and the SCALE UP OF A SINGLE NAME NODE ABOVE 64 GB but these results in overhead cost.So in Hadoop 2.x we have a feature called FEDERATION where instead of a single name node set(i.e active name node,passive name node and secondary name node ) there are Multiple name node set(say 3) such that each name node maintains the METADATA of each department separately(say one name node takes care of marketing data alone and other name node takes care of finance  data alone) but all the name nodes can access all DATA NODES but they will only look at related information(ie MARKETING NAME NODE TAKES METADATA ABOUT ONLY MARKEETING  AND FINANCE NAME NODE TAKES METADATA ABOUT ONLY FINANCE) 
3.Dynamic Node Allocation
Here Node is not fixed for Mapping and reducing instead any Data Node can act as Mapper and Reducer  
4.YARN(Yet Another Resource Negotiator)
In order to reduce the load of 
