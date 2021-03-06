# Deleting a Public Hosted Zone<a name="DeleteHostedZone"></a>

The following procedure explains how to delete a hosted zone using the Amazon Route 53 console\. For information about how to delete a hosted zone using the Route 53 API, see [DeleteHostedZone](http://docs.aws.amazon.com/Route53/latest/APIReference/API_DeleteHostedZone.html) in the *Amazon Route 53 API Reference*\. 

**Important**  
If you want to keep your domain registration but you want to stop routing internet traffic to your website or web application, we recommend that you delete *records* in the hosted zone instead of deleting the hosted zone\.  
If you delete a hosted zone, you can't undelete it\. You must create a new hosted zone and update the name servers for your domain registration, which can require up to 48 hours to take effect\. \(If you delegated responsibility for a subdomain to a hosted zone and you delete the child hosted zone, you must update the name servers in the parent hosted zone\.\) In addition, if you delete a hosted zone, someone could hijack the domain and route traffic to their own resources using your domain name\.  
If you want to avoid the monthly charge for the hosted zone, you can transfer DNS service for the domain to a free DNS service\. When you transfer DNS service, you have to update the name servers for the domain registration\. If the domain is registered with Route 53, see [Adding or Changing Name Servers and Glue Records for a Domain](domain-name-servers-glue-records.md) for information about how to replace Route 53 name servers with name servers for the new DNS service\. If the domain is registered with another registrar, use the method provided by the registrar to update name servers for the domain registration\. For more information, perform an internet search on "free DNS service\."

You can delete a hosted zone only if there are no records other than the default SOA and NS records\. If your hosted zone contains other records, you must delete them before you can delete your hosted zone\. This prevents you from accidentally deleting a hosted zone that still contains records\.

**To delete a public hosted zone using the Route 53 console**

1. Sign in to the AWS Management Console and open the Route 53 console at [https://console\.aws\.amazon\.com/route53/](https://console.aws.amazon.com/route53/)\.

1. Confirm that the hosted zone that you want to delete contains only an NS and an SOA record\. If it contains additional records, delete them:

   1. Choose the name of the hosted zone that you want to delete\.

   1. On the Record Sets page, if the list of records includes any records for which the value of the **Type** column is something other than NS or SOA, choose the row, and choose **Delete Record Set**\.

      To select multiple, consecutive records, choose the first row, press and hold the **Shift** key, and choose the last row\. To select multiple, non\-consecutive records, choose the first row, press and hold the **Ctrl** key, and choose the remaining rows\. 
**Note**  
If you created any NS records for subdomains in the hosted zone, delete those records, too\.

   1. Choose **Back to Hosted Zones**\.

1. On the **Hosted Zones** page, choose the row for the hosted zone that you want to delete\.

1. Choose **Delete Hosted Zone**\.

1. Choose **OK** to confirm\.

1. If you want to make the domain unavailable on the internet, we recommend that you transfer DNS service to a free DNS service and then delete the Route 53 hosted zone\. This prevents future DNS queries from possibly being misrouted\. 

   If the domain is registered with Route 53, see [Adding or Changing Name Servers and Glue Records for a Domain](domain-name-servers-glue-records.md) for information about how to replace Route 53 name servers with name servers for the new DNS service\. If the domain is registered with another registrar, use the method provided by the registrar to change name servers for the domain\.
**Note**  
If you're deleting a hosted zone for a subdomain \(acme\.example\.com\), you don't need to change name servers for the domain \(example\.com\)\.