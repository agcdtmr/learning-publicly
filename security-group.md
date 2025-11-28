# Security Groups Good to know

• Can be attached to multiple instances
• Locked down to a region / VPC combination
• Does live "outside" the EC2 - if traffic is blocked the EC2 instance won't see it
• It's good to maintain one separate security group for SSH access
• If your application is not accessible (time out), then it's a security group issue
• If your application gives a "connection refused" error, then it's an application error or it's not launched
• All inbound traffic is blocked by default
• All outbound traffic is authorised by default
