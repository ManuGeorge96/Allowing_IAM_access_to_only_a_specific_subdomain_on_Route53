# setting_sub-domain_on_Route53_with_IAM_user_access
About, how we can setup a subdomain in Route53, and giving access to a specific IAM user with policy for editing the subdomain records.

## Situation
 
A co-worker has come to us asking to to create a subdomain and to grant permission to edit the DNS records for the same.
Here, while granting access to the co-worker we should ensure that he is not able to edit other DNS records associated with other subdomian or the main domains on the Rote53.

## Methode

-  For this first we have to create a new Hosted Zone on Route53 with the sub-domain.
-  Copy the nameservers provided for the sub-domain and add these Nameservers as NS records for this subdomain on the main domain  Eg:, if the subdomain is <b>test.dnsrecords.tech</b>, then the nameserevrs of the subdomain should be listed as NS record on the DNS records of <b>dnsrecords.tech</b>.
-  Note down the <b>Hosted Zone ID</b> for the newely created Hosted Zone.
-  Create an IAM policy with the below JSON rules,
-  ```sh
     {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "route53:GetHostedZone",
                "route53:ChangeResourceRecordSets",
                "route53:ListResourceRecordSets"
            ],
            "Resource": "arn:aws:route53:::hostedzone/Z0064862302RH0WZLAWCL"
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": [
                "route53:ListHostedZones",
                "route53:GetHostedZoneCount",
                "route53:ListHostedZonesByName"
            ],
            "Resource": "*"
        }
       ]
      }
     ```
 - Replace the <b>"Resource":</b> section with the ARN of the new subdomain.
 - Now create the user.
 - Attach the above created IAM policy for that user.   
