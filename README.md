# Monitor-Resources--AWS
<h1>Monitor Resources using AWS CloudWatch</h1>

<h2>Description</h2>
This lab demonstrates monitoring resources and deployed configurations using AWS CloudWatch and CloudTrail, along with setting alert metrics for resource management by creating SNS topics and using CloudWatch metric filtering. 
When the CloudWatch alarms breach, the alarm sends notifications based on trigger to your email. This is an example of an enterprise Web Application Database in AWS that leverages different resources across multiple EC2 instances. 
The EC2 instances used will spin up dynamic loads to create activity to monitor. The EC2 instances will be monitored via a custom made CloudWatch service dashboard.  
<br></br>


<h2>Languages and Utilities Used</h2>

- <b>JSON</b> 
- <b>AWS CloudWatch</b>
- <b>AWS CloudTrail</b>
- <b>EC2</b>

<h2>Environments Used </h2>

- <b>Windows 10</b>
- <b>Amazon Web Services (AWS console)</b>
- <b>PluralSight Labs VMs </b>

<h2>Program walk-through:</h2>

Step 1: Log into the AWS console, use the search bar to navigate to the CloudWatch service. Click Overview dropdown -> Service Dashboards -> select EC2
![step1](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/bc5b3194-5c82-4bcf-8ace-9dd2d4948732)

Step 2: Create a custom dashboard
Under Dashboard name -> type Globo_App_Monitor then click Create Dashboard.
![step2](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/827d88ff-80c8-4466-b6c0-dec0ca577737)
![globo](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/437665a1-d56b-4390-81b7-06568680c768)

Step3:  Add Disk specific Disk usage monitoring to the custom dashboard:

- Go to EC2 service - from list of current instances, click Instance ID for Database 1 (DB-01)
- Select the Storage tab and then the Volume ID to copy it. Next, this Volume ID will be used to track in CloudWatch.
- Go to CloudWatch Dashboards and click the link for the Globo_App_Monitor that was previously made.
- In the EC2 Resource Snapshot widget, select Edit from the dropdown.
- ![add_widget](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/e1d3be48-70a9-4c7e-b4c5-6a6a2d4d9b35)
![create_widget](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/cbd544bb-1e65-49d4-8db1-77f98ff67681)
- Click Browse, then select EBS > Per-Volume Metrics -> Paste in the Volume ID for DB-01 and DB-02. Giving each a Metric Name of VolumeWriteOps.

Create a metric graph of EC2 Resources for NetworkIn CPU Utilization metrics:
![step3](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/4947f982-386b-4885-87c2-64870b9bddd5)

Click Add Query -> EC2
![add_query_cpu](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/c6d96626-8fae-43b5-a94b-994ac10b9e4d)

Step 4:
![step4](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/c96a6d72-26d9-4e9b-9b76-6dcf9487004d)

Step 5:
![Step5](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/4cb545fe-f083-4483-a7b6-bd325ced697c)
Search the volume ID for D-01 to add in the volume wirte operation metric collection. Then repeat the same step for DB-02 to set a volume write operation metric for that database EC2 instance.
![step5_volume_metric](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/c9947e94-5247-4505-8231-4620a13d5ba1)

Here is the updated graphed metrics of monitoring all components of the application.
![step5_update](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/00b42653-fe4e-41a8-bc56-240a1335c272)

Step 6: Aggregate Specific Metrics for Your Application:
This will display the aggregation of all the resoures being used. This step demonstrates adding additional usability to your app monitoring dashboard, creating custom widgets to display aggregated resource usage information. 

- In EC2, select the Instance labeled as Monitoring -> Actions -> Monitor and Troubleshoot > Manage detailed monitoring. Enable and Save.
- ![step6_one](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/74c4c7fb-3810-48d1-9b4f-29bc51c8338d)

- Go to CloudWatch Metrics tab, click EC2 and then click Across ALL Instances. (this enables detailed monitoring).
- ![step6_two](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/b03a97ce-c426-4cf5-9d24-08df7f459794)
 ![step6_three](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/de528355-3f97-4f73-a1c6-48b3d7caccb7)
- Select the Check boxes:
- • CPUUtilization
- • Networkin
- • NetworkOut
- Click graphed metrics, then change the 5 minutes dropdown to 1 minute.
 ![step6_five](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/9690c6a9-5880-4832-94f3-3e6bdb37b8da)


- In the top left of the window, click the pencil icon beside untiled graph and enter Globo App Resources - Aggregated.
- Click the Actions drop-down in the top right and then click 'Add' to the dashboard.
  ![step6_six](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/3a22ae4f-9e2a-4133-8e63-68da3d79cb65)
  ![complete_step6](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/1384c7b3-0cf9-444a-bf05-7053e44d9f00)


Step 7: Create Custom Alerts
  ![step6_seven](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/1d654c65-42c8-4d82-bd74-043411f7db05)
![step6_eight](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/5d23fb17-5f52-4d0e-84ec-caeb965406ec)
Step 8: ![specify_metric_conditions](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/5aa6a542-253d-4940-9300-b430beb8e6e8)

Step9: Configure Conditions
![conditions](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/4c8ef6c7-8820-48a0-a7dd-2d06d6a0806f)

Configure Actions:
![config_actions](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/b6b152d0-b478-407f-b9a1-42feba630cf3)

![preview_step9](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/70cd2aa1-8a4c-4583-a026-93849341f8fe)
![step9_actions](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/4ac62e4a-3020-4412-bdca-bf6b6b4886ff)

Step 10. Monitor Alarms and Take action:
![step10](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/1bd44eb9-a452-46a3-8b87-aa283d721953)

![step10_one](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/8de2930e-5db0-4346-839a-5dc94083d347)
![step10_two](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/666dd3d6-c172-4ce7-a755-1c0e45a245ef)

Step 11:  Create an alarm for DB-02 that automatically reboots the EC2 instance when the CPU spikes to help solve the devs issue with an alarm condition:
- In the DB-02 row under Actions column, click bell icon.
- In the conditions section select Lower and tehn enter 20 in the THAN... input. Click next.
- In the Notification section, from the Send a noticification to.. drop-down, select Default_CloudWatch_Alarms_Topic.
- ![notification_alarm](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/c8696b69-726a-4d83-ace1-be3ba8a9366d)
- Under the EC2 action section, Add EC2 action adn select Reboot this instance. (So devs can patch the application).
- ![EC2_action](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/17135620-8d88-4045-a62a-8e7ee38f2ac0)
- Under Alarm name, type DB-02 Reboot on CPU Spike and click Next.
- ![reboot_cpu_spike](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/c334c6c4-d7ac-406a-a5f8-81c06bff8946)

- Create Alarm
- ![create_alarm1](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/d5064cc7-941f-465b-bcc9-59ec86d77cc9)

  This finds the problem DB and creates a self correcting action until the application can be updated. Here are the end results of alarm alert status.

![alarm_status](https://github.com/brireyn/Monitor-Resources--AWS/assets/96150916/7f530231-dc5b-476b-bc5e-190df438e1df)










  




