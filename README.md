## Situation
 
A co-worker has come to us asking to to create a subdomain and to grant him permission to edit the DNS records for the same.
Here, while granting access to the co-worker we should ensure that he is not able to edit other DNS records associated with other subdomian or the main domains on the Rote53.

## Methode

-  For this, first we have to create a new Hosted Zone on Route53 for the sub-domain.

   [<img align="center" alt="Unix" width="900" src="https://raw.githubusercontent.com/ManuGeorge96/ManuGeorge96/master/Tools/1.PNG" />][ln]
   
-  Once created, note down the nameservers provided for the sub-domain, and add these Nameservers as NS records on the main domain  Eg:, if the subdomain is <b>test.dnsrecords.tech</b>, then the nameserevrs of the subdomain should be listed as NS record on the DNS records of <b>dnsrecords.tech</b>.

   [<img align="center" alt="Unix" width="900" src="https://raw.githubusercontent.com/ManuGeorge96/ManuGeorge96/master/Tools/3.PNG" />][ln]


-  Note down the <b>Hosted Zone ID</b> for the newely created Hosted Zone for the subdomian.

   [<img align="center" alt="Unix" width="900" src="https://raw.githubusercontent.com/ManuGeorge96/ManuGeorge96/master/Tools/2.PNG" />][ln]


-  Create an IAM policy for the user. Click on create policy

   [<img align="center" alt="Unix" width="900" src="https://raw.githubusercontent.com/ManuGeorge96/ManuGeorge96/master/Tools/4.PNG" />][ln]
   
-  On the <b>Create policy</b> section go for JSON tab and add the JSON code, replace <b>HOSTED_ZONE_ID</b> with the ID found on step 3. Refer image below, 
   
   [<img align="center" alt="Unix" width="900" src="https://raw.githubusercontent.com/ManuGeorge96/ManuGeorge96/master/Tools/5.PNG" />][ln]
   
 - Now create the user.

    [<img align="center" alt="Unix" width="900" src="https://raw.githubusercontent.com/ManuGeorge96/ManuGeorge96/master/Tools/6.PNG" />][ln]

 - Attach the above created IAM policy for that user. Filter the result by choosing <b>customer managed</b>, and then proceed.

    [<img align="center" alt="Unix" width="900" src="https://raw.githubusercontent.com/ManuGeorge96/ManuGeorge96/master/Tools/7.PNG" />][ln] 
    
 - You are dne with the setup now testing.

## Result

-  On accessing the main domain on Route53 as the newely craeted user.

   [<img align="center" alt="Unix" width="900" src="https://raw.githubusercontent.com/ManuGeorge96/ManuGeorge96/master/Tools/8.PNG" />][ln]
   
- On accessing the subdomain using the same user,

   [<img align="center" alt="Unix" width="900" src="https://raw.githubusercontent.com/ManuGeorge96/ManuGeorge96/master/Tools/9.PNG" />][ln]







[ln]: https://www.linkedin.com/in/manu-george-03453613a
