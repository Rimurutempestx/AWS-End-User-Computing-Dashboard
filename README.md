# AWS-End-User-Computing-Dashboard
Built a dashboard that enables your help desk staff to view details for Amazon AppStream 2.0 fleets and Amazon WorkSpaces directories and instances.

## Overview
A dashboard that enables your help desk staff to view details for Amazon AppStream 2.0 fleets and Amazon WorkSpaces directories and instances. For both AppStream 2.0 and WorkSpaces, your staff can also use the dashboard to perform basic administrative tasks. For AppStream 2.0, they can monitor autoscaling activities and manage users’ streaming sessions. For WorkSpaces, they can send the registration code email to a user, or stop, start, restart, and restore a user’s WorkSpace. With this workflow, your teams don’t require access to the AppStream 2.0 console or WorkSpaces console, or cloud-based computing experience.



![image](https://user-images.githubusercontent.com/106786020/213949555-ebc030a6-5585-40f7-9814-0e2bb87504d6.jpeg)



## Static website and Clodfront configuration
Started off by creating a S3 bucket to store my objects, then made sure that my bucket name was a globally unique DNS-compliant name. Also verified that the region is supported for the project. 
