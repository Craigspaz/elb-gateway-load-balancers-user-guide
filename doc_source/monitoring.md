# Monitor your Gateway Load Balancers<a name="monitoring"></a>

You can use the following features to monitor your Gateway Load Balancers, to analyze traffic patterns, and to troubleshoot issues\.

**CloudWatch metrics**  
You can use Amazon CloudWatch to retrieve statistics about data points for your Gateway Load Balancers and targets as an ordered set of time\-series data, known as *metrics*\. You can use these metrics to verify that your system is performing as expected\. For more information, see [CloudWatch metrics for your Gateway Load Balancer](cloudwatch-metrics.md)\.

**VPC Flow Logs**  
You can use VPC Flow Logs to capture detailed information about the traffic going to and from your Gateway Load Balancer\. For more information, see [VPC flow logs](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html) in the *Amazon VPC User Guide*\.  
Create a flow log for each network interface for your Gateway Load Balancer\. There is one network interface per subnet\. To identify the network interfaces for a Gateway Load Balancer, look for the name of the Gateway Load Balancer in the description field of the network interface\.  
There are two entries for each connection through your Gateway Load Balancer, one for the frontend connection between the client and the Gateway Load Balancer, and the other for the backend connection between the Gateway Load Balancer and the target\. If the target is registered by instance ID, the connection appears to the instance as a connection from the client\. If the security group of the instance doesn't allow connections from the client but the network ACLs for the subnet allow them, the logs for the network interface for the Gateway Load Balancer show "ACCEPT OK" for the frontend and backend connections, while the logs for the network interface for the instance show "REJECT OK" for the connection\.

**CloudTrail logs**  
You can use AWS CloudTrail to capture detailed information about the calls made to the Elastic Load Balancing API, and store them as log files in Amazon S3\. You can use these CloudTrail logs to determine which calls were made, the source IP address where the call came from, who made the call, when the call was made, and so on\. For more information, see [Logging API calls for your Gateway Load Balancer using AWS CloudTrail](cloudtrail-logs.md)\.