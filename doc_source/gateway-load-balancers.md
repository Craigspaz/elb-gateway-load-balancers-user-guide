# Gateway Load Balancers<a name="gateway-load-balancers"></a>

Use a Gateway Load Balancer to deploy and manage a fleet of virtual appliances that support the GENEVE protocol\.

A Gateway Load Balancer operates at the third layer of the Open Systems Interconnection \(OSI\) model\. It listens for all IP packets across all ports and forwards traffic to the target group that's specified in the listener rule, using the GENEVE protocol on port 6081\.

You can add or remove targets from your load balancer as your needs change, without disrupting the overall flow of requests\. Elastic Load Balancing scales your load balancer as traffic to your application changes over time\. Elastic Load Balancing can scale to the vast majority of workloads automatically\.

**Topics**
+ [Load balancer state](#load-balancer-state)
+ [Load balancer attributes](#load-balancer-attributes)
+ [Availability Zones](#availability-zones)
+ [Deletion protection](#deletion-protection)
+ [Cross\-zone load balancing](#cross-zone-load-balancing)
+ [Create a load balancer](create-load-balancer.md)
+ [Update tags](tag-load-balancer.md)
+ [Delete a load balancer](delete-load-balancer.md)

## Load balancer state<a name="load-balancer-state"></a>

A Gateway Load Balancer can be in one of the following states:

`provisioning`  
The Gateway Load Balancer is being set up\.

`active`  
The Gateway Load Balancer is fully set up and ready to route traffic\.

`failed`  
The Gateway Load Balancer could not be set up\.

## Load balancer attributes<a name="load-balancer-attributes"></a>

The following are the load balancer attributes for Gateway Load Balancers:

`deletion_protection.enabled`  
Indicates whether [deletion protection](#deletion-protection) is enabled\. The default is `false`\.

`load_balancing.cross_zone.enabled`  
Indicates whether [cross\-zone load balancing](#cross-zone-load-balancing) is enabled\. The default is `false`\.

## Availability Zones<a name="availability-zones"></a>

When you create a Gateway Load Balancer, you enable one or more Availability Zones, and specify the subnet that corresponds to each zone\. When you enable multiple Availability Zones, it ensures that the load balancer can continue to route traffic even if an Availability Zone becomes unavailable\. The subnets that you specify must each have at least 8 available IP addresses\. Subnets cannot be added or removed after the load balancer is created\. To add or remove a subnet, you must create a new load balancer\.

## Deletion protection<a name="deletion-protection"></a>

To prevent your Gateway Load Balancer from being deleted accidentally, you can enable deletion protection\. By default, deletion protection is disabled\.

If you enable deletion protection for your Gateway Load Balancer, you must disable it before you can delete the Gateway Load Balancer\.

**To enable deletion protection using the console**

1. Open the Amazon EC2 console at [https://console\.aws\.amazon\.com/ec2/](https://console.aws.amazon.com/ec2/)\.

1. In the navigation pane, under **LOAD BALANCING**, choose **Load Balancers**\.

1. Select the Gateway Load Balancer\.

1. Choose **Actions**, **Edit attributes**\.

1. On the **Edit load balancer attributes** page, select **Enable** for **Delete Protection**, and then choose **Save**\.

**To disable deletion protection using the console**

1. Open the Amazon EC2 console at [https://console\.aws\.amazon\.com/ec2/](https://console.aws.amazon.com/ec2/)\.

1. In the navigation pane, under **LOAD BALANCING**, choose **Load Balancers**\.

1. Select the Gateway Load Balancer\.

1. Choose **Actions**, **Edit attributes**\.

1. On the **Edit load balancer attributes** page, clear **Enable** for **Delete Protection**, and then choose **Save**\.

**To enable or disable deletion protection using the AWS CLI**  
Use the [modify\-load\-balancer\-attributes](https://docs.aws.amazon.com/cli/latest/reference/elbv2/modify-load-balancer-attributes.html) command with the `deletion_protection.enabled` attribute\.

## Cross\-zone load balancing<a name="cross-zone-load-balancing"></a>

By default, each load balancer node distributes traffic across the registered targets in its Availability Zone only\. If you enable cross\-zone load balancing, each Gateway Load Balancer node distributes traffic across the registered targets in all enabled Availability Zones\. For more information, see [Cross\-zone load balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html#cross-zone-load-balancing) in the *Elastic Load Balancing User Guide*\.

**To enable cross\-zone load balancing using the console**

1. Open the Amazon EC2 console at [https://console\.aws\.amazon\.com/ec2/](https://console.aws.amazon.com/ec2/)\.

1. In the navigation pane, under **LOAD BALANCING**, choose **Load Balancers**\.

1. Select the Gateway Load Balancer\.

1. Choose **Actions**, **Edit attributes**\.

1. On the **Edit load balancer attributes** page, select **Enable** for **Cross\-Zone Load Balancing**, and then choose **Save**\.

**To enable cross\-zone load balancing using the AWS CLI**  
Use the [modify\-load\-balancer\-attributes](https://docs.aws.amazon.com/cli/latest/reference/elbv2/modify-load-balancer-attributes.html) command with the `load_balancing.cross_zone.enabled` attribute\.