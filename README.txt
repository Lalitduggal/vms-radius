Project Summary:

A visitor walks in at the office reception. There is an Ipad/Tablet/Phone/Laptop on which a URL is opened on a browser.



http://www.exihub.com/vms/radius/sydney/visitor
or
http://exihub.com/vms/radius/sydney/visitor

There is a login page in which the reception person will login so that visitors can checkin

Username: xxxxx
Password: xxxxx
login

Once successfully logged in. It will be logged in for 12 hours and log out button is presented on top right corner.

Visitor details: 
Name: xxxx
Email: xxxx
Mobile: +61 - 123456789
Organization: xxxx
Purpose: Meeting/Personal/Interview/Others
To Meet Employee: droplist of emp names
Check In

As soon as the person clicks on Check In button:
	An Email is sent to the Employee provinding information about the Visitor
	An SMS is sent to the Employee provinding information about the Visitor
	An Email is sent to the Visitor provinding information about the successful checkin
	An SMS is sent to the Visitor provinding information about the successful checkin
	





There is another login page which reception uses:

http://www.exihub.com/vms/radius/sydney/reception
or
http://exihub.com/vms/radius/sydney/reception


Username: xxxxx
Password: xxxxx
login

Once successfully logged in. It will be logged in for 12 hours and log out button is presented on top right corner.
This will display all the visitors which are visiting this premises today in a tabular manner with following details:
By default: The data is sorted based on the CheckInDateTime.
The data can also be sorted in ascending and descending order when clicked on column names.


VisitorName | VisitorEmail |  VisitorMobile | VisitorOrganization | VisitorPurpose | EmpEmail | CheckInDateTime | CheckOutDateTime


By default the CheckOutDateTime will show CheckOut button.

After the visitor has met the employee and going out.
The reception will checkout the visitor by clicking the CheckOut button.
As soon as the reception clicks on Check Out button for that visitor:
	An Email is sent to the Employee provinding information about the Visitor
	An SMS is sent to the Employee provinding information about the Visitor
	An Email is sent to the Visitor provinding information about the successful checkin
	An SMS is sent to the Visitor provinding information about the successful checkin








There is another login page which admin uses:

http://www.exihub.com/vms/radius/sydney/admin
or
http://exihub.com/vms/radius/sydney/admin


Username: xxxxx
Password: xxxxx
login

Once successfully logged in. It will be logged in for 12 hours and log out button is presented on top right corner.



It will have menus for:

Employee
	Add | Bulk Upload
	EmpFirstName | EmpLastName | EmpEmail | EmpMobile | EmpDepartment | EmpID | Modify | Delete

By default data is sorted based on the EmpFirstName.
However, you an click on any of the column names for ascending and decending order

When you click Add button, a pop up is displayed to enter the employee details for new employee.

Enter employee details for new employee:
EmpFirstName: 
EmpLastName: 
EmpEmail: 
EmpMobile: +61 - 123456789
EmpDepartment: 
EmpID: 
Submit

As soon as you submit and it is success: a successful message is presented.
As soon as you submit and it is error: an error messsage is presented.






When you click the Modify button.
The Data in the row is enabled for Edit and th Modify button is changed to Save | Cancel

As soon as you click on Save.
On success, row is disabled for edit and button is changed back to Modify
On error, error message prompt is made visible to user





When you click the Delete button.
A confirmation prompt appears.
On successful deletion an success message appears and then disappears
On error for deletion an error message appears prompt appears.






When you click Bulk Upload button

Choose a file to upload
Hint: file should be csv file in the following format with first line as header:
EmpFirstName,EmpLastName,EmpEmail,EmpMobile,EmpDepartment,EmpID

Submit

On success, a message appears: successfully uploaded
On error, a message appears displaying error message










Custom Report
	StartDate:
	EndDate:
	Submit

OnClick of Submit button: generating report is being displayed...

On successful report generation following message is displayed:
Link has been emailed to admin email id.








Technologies:
Browser: Chrome version xxx

SCM: Git version xxx

Cloud: AWS
Serverless:
	API Gateway: for API
	Lambda: for micro services using python 3.7
	Step functions: for orchestration of lambdas
	Dynamodb: for database
	S3: for hosting static website, storing daily/custom reports, cloudformation templates and lambda functions
	SES: for email
	SNS: for sms
	Cloudformation: for Infrastructure As Code
	SAM: as extension to Cloudformation for packaging and deploying API and Lambdas
	Serverless (sls): as extension to Cloudformation for packaging and deploying API and Lambdas
	IAM: for managing user, group, role, policy
	Route53: for hosting domain and providing dns for s3 website
	Cloudwatch: for creating dashboard to be used for monitoring and for debugging purpose
	Cloudtrail: for auditing purpose
	Cognito: for providing the signin page, forgot password, reset password functionality and passsord policy
	

CICD: Jenkins: As soon as you commit in Git the Git webhook gets trigged and new code is build, packaged and deployed instantly.


Configuration: Ansible







cloud: AWS
------

Account: larryduggal@gmail.com
--------

select region: North Virginia
--------------

login to console and select ec2 as service; then select key pair: vms-radius-north-virginia

IAM:
----
user: vms-radius-user
group: vms-radius-group
role: vms-radius-role
policy: vms-radius-policy


laptop:
-------
cd
cd .ssh
ssh-keygen		id_rsa_lalitduggal-vms-radius

chmod 400 id_rsa_lalitduggal-vms-radius
chmod 400 id_rsa_lalitduggal-vms-radius.pub

vi config



install git


install npm

install python3

install pip

install nodejs

install serverless

install aws cli





git: 	
----
organization: lalitduggal
repository: vms-radius
branch: master
public repository: yes


deploy keys: id_rsa_lalitduggal_vms_radius.pub




company name: radius
-------------

system manager parameter store:
--------------------------------
/vms/radius/timezone: MELBOURNE

/vms/radius/bucketname: vms-radius-sydney
/vms/radius/dailyreportfoldername: daily-report		eg: vms-radius-sydney/daily-report/yyyymmdd.csv
/vms/radius/customdatereportfoldername: custom-date-report	eg: vms-radius-sydney/custom-report/yyyymmdd_yyyymmdd.csv

/vms/radius/cloudformation/bucketname: vms-radius-sydney-cloudformation


/vms/radius/visitorpurpose: ['Meeting','Interview','Official','Personal','Others']
/vms/radius/adminemailids: ['larryduggal@gmail.com','divya.r.grover@gmail.com','lalit.duggal@gmail.com']

/vms/radius/fromsmssenderid: RADIUS

/vms/radius/employeetablename: vms-radius-emp-table
/vms/radius/visitortablename: vms-radius-visitor-table

/vms/radius/fromemailname: VMS Radius
/vms/radius/fromemailid: vmsradius@exihub.com
/vms/radius/fromemailsignature: VMS Admin



/vms/radius/checkin/emp/emailtemplatename: vms-radius-checkin-emp-email-template
/vms/radius/checkin/visitor/emailtemplatename: vms-radius-checkin-visitor-email-template

/vms/radius/checkout/emp/emailtemplatename: vms-radius-checkout-emp-email-template
/vms/radius/checkout/visitor/emailtemplatename: vms-radius-checkout-visitor-email-template



/vms/radius/checkin/emp/email: y
/vms/radius/checkin/visitor/email: y

/vms/radius/checkin/emp/sms: y
/vms/radius/checkin/visitor/sms: y



/vms/radius/checkout/emp/email: y
/vms/radius/checkout/visitor/email: y

/vms/radius/checkout/emp/sms: y
/vms/radius/checkout/visitor/sms: y

------------




api gateway -> lambda:
----------------------
api: /vms
stage: prod
method:
resource:
path:
lambda:
lambda-role:
cores-enabled:


/vms/radius/checkin/emp/email			vms-radius-checkin-emp-email
/vms/radius/checkin/visitor/email		vms-radius-checkin-visitor-email

/vms/radius/checkin/emp/sms				vms-radius-checkin-emp-sms
/vms/radius/checkin/visitor/sms			vms-radius-checkin-visitor-sms



/vms/radius/checkout/emp/email			vms-radius-checkout-emp-email
/vms/radius/checkout/visitor/email		vms-radius-checkout-visitor-email

/vms/radius/checkout/emp/sms			vms-radius-checkout-emp-sms
/vms/radius/checkout/visitor/sms		vms-radius-checkout-visitor-sms




vms-radius-daily-visitor-report
vms-radius-from-to-visitor-report


vms-radius-metadata-emp-insert
vms-radius-metadata-emp-update
vms-radius-metadata-emp-delete
vms-radius-metadata-emp-selectall
vms-radius-metadata-emp-find
vms-radius-metadata-emp-bulk-upload



step function:
--------------

//this gets triggered as part of the stream event as soon as a new item is inserted into visitor table
vms-radius-checkin-flow


{
	"empFirstName": "",
	"empLastName": "",
	"visitorName": "",
	"visitorEmail": "",
	"visitorMobile": "",
	"visitorOrganization": "",
	"visitorPurpose": "",
	"visitorCheckInDate": "",
	"visitorCheckInTime": ""
}




{
	"empFirstName": "",
	"empLastName": "",
	"empEmail": 
	"empMobile":
	
	"visitorName": "",
	"visitorEmail": "",
	"visitorMobile": "",
	"visitorOrganization": "",
	"visitorPurpose": "",
	"visitorCheckInDate": "",
	"visitorCheckInTime": "",
	
	"vms-radius-checkin-emp-email-check": "",
	"vms-radius-checkin-emp-sms-check": "",
	"vms-radius-checkin-visitor-email-check": "",
	"vms-radius-checkin-visitor-sms-check": "",

	"vms-radius-checkout-emp-email-check": "",
	"vms-radius-checkout-emp-sms-check": "",
	"vms-radius-checkout-visitor-email-check": "",
	"vms-radius-checkout-visitor-sms-check": "",
	
	"fromName": "",
	"fromEmail": "",
	"customerName": "",
	"signature": "",

	"senderID": ""
}






vms-radius-checkin-emp-email-check
return:
{
	"vms-radius-checkin-emp-email-check": "",
}


vms-radius-checkin-visitor-email-check
return:
{
	"vms-radius-checkin-visitor-email-check": "",
}


vms-radius-checkin-emp-sms-check
return:
{
	"vms-radius-checkin-emp-sms-check": "",
}


vms-radius-checkin-emp-sms-check
return:
{
	"vms-radius-checkin-emp-sms-check": "",
}


vms-radius-checkout-emp-email-check
return:
{
	"vms-radius-checkout-emp-email-check": "",
}


vms-radius-checkout-visitor-email-check
return:
{
	"vms-radius-checkout-visitor-email-check": "",
}


vms-radius-checkout-emp-sms-check
return:
{
	"vms-radius-checkout-emp-sms-check": "",
}


vms-radius-checkout-emp-sms-check
return:
{
	"vms-radius-checkout-emp-sms-check": "",
}




vms-radius-checkout-flow




cloudwatch:
-----------
daily report time and timezone for lambda function of daily report: 00:01



SES:
----


s3:
---
vms-radius-sydney-












ec2:
----

jenkin




vpc:
----


subnet:
--------



Internet Gateway:
-----------------


Security Group:
---------------


Ansible Tower:
---------------



security group:
---------------


Access Control List:
--------------------


Routing table:
--------------


======================================================
Details
======================================================


email template:
---------------
vms-radius-checkin-emp-email-template

{
	"fromName": "",
	"fromEmail": "",
	"signature": "",	
	"empFirstName": "",
	"empLastName": "",
	"empEmail": "", 
	"visitorName": "",
	"visitorEmail": "",
	"visitorMobile": "",
	"visitorOrganization": "",
	"visitorPurpose": "",
	"visitorCheckInDate": "",
	"visitorCheckInTime": ""
}


From: <fromName> <<fromEmail>>
To: <empFirstName> <empLastName> <<empEmail>>
Subject: Checked In - <visitorName> - <visitorCheckInDate> <visitorCheckInTime>
Body:

Dear <empFirstName> <empLastName>,

Visitor has checked in. Details as below:
Name: <visitorName>
Email: <visitorEmail>
Mobile: <visitorMobile
Organization: <visitorOrganization>
Purpose: <visitorPurpose>
CheckIn Date Time: <visitorCheckInDate> <visitorCheckInTime>

Please proceed to welcome the guest at the reception.

Regards,
<signature>










vms-radius-checkin-visitor-email-template

{
	"fromName": "",
	"fromEmail": "",
	"customerName": "",
	"signature": "",
	"empFirstName": "",
	"empLastName": "",
	"visitorName": "",
	"visitorEmail": "",
	"visitorCheckInDate": "",
	"visitorCheckInTime": ""
}


From: <fromName> <<fromEmail>>
To: <visitorName> <<visitorEmail>>
Subject: Checked In - <visitorName> - <visitorCheckInDate> <visitorCheckInTime>
Body:

Dear <visitorName>,

You have been successfully checked in at <customerName> premises.
Check in Date Time: <visitorCheckInDate> <visitorCheckInTime>

Employee <empFirstName> <empLastName> has been informed.

Please wait at the reception.

Thanks,
<signature>












vms-radius-checkout-emp-email-template

{
	"fromName": "",
	"fromEmail": "",
	"signature": "",	
	"empFirstName": "",
	"empLastName": "",	
	"empEmail": "", 
	"visitorName": "",
	"visitorEmail": "",
	"visitorMobile": "",
	"visitorOrganization": "",
	"visitorPurpose": "",
	"visitorCheckInDate": "",
	"visitorCheckInTime": "",	
	"visitorCheckOutDate": "",
	"visitorCheckOutTime": ""
}


From: <fromName> <<fromEmail>>
To: <empFirstName> <empLastName> <<empEmail>>
Subject: Checked Out - <visitorName> - <visitorCheckOutDate> <visitorCheckOutTime>
Body:

Dear <empFirstName> <empLastName>,

Visitor has been checked out. Details as below:
Name: <visitorName>
Email: <visitorEmail>
Mobile: <visitorMobile
Organization: <visitorOrganization>
Purpose: <visitorPurpose>
CheckIn Date Time: <visitorCheckInDate> <visitorCheckInTime>
CheckOut Date Time: <visitorCheckOutDate> <visitorCheckOutTime>

Regards,
<signature>








vms-radius-checkout-visitor-email-template

{
	"fromName": "",
	"fromEmail": "",
	"customerName": "",
	"signature": "",
	"empFirstName": "",
	"empLastName": "",
	"visitorName": "",
	"visitorEmail": "",
	"visitorMobile": "",
	"visitorOrganization": "",
	"visitorPurpose": "",
	"visitorCheckInDate": "",
	"visitorCheckInTime": "",	
	"visitorCheckOutDate": "",
	"visitorCheckOutTime": ""
}


From: <fromName> <<fromEmail>>
To: <visitorName> <visitorEmail>>
Subject: Checked Out - <visitorName> - <visitorCheckOutDate> <visitorCheckOutTime>
Body:

Dear <visitorName>,

You had come to meet employee: <empFirstName> <empLastName> at <customerName> for <visitorPurpose>

You have now been successfully checked out.

CheckIn Date Time: <visitorCheckInDate> <visitorCheckInTime>
CheckOut Date Time: <visitorCheckOutDate> <visitorCheckOutTime>

Along-with the above, your following details are also stored in our visitor management system for reporting purpose:

Name: <visitorName>
Email: <visitorEmail>
Mobile: <visitorMobile>
Organization: <visitorOrganization>

Regards,
<signature>















sms template:
---------------
vms-radius-checkin-emp-sms-template

{
	"senderID": "",
	"empFirstName": "",
	"visitorName": "",
	"visitorCheckInDate": "",
	"visitorCheckInTime": "",
}

<senderID>
Dear <empFirstName>, Visitor <visitorName> is waiting at reception and has checked in at <visitorCheckInDate> <visitorCheckInTime>






vms-radius-checkin-visitor-sms-template

{
	"senderID": "",
	"signature": "",
	"empFirstName": "",
	"visitorName": ""
}


<senderID>
Welcome <visitorName>. You have been successfully checked in and <empFirstName> has been informed. Please wait at the reception. Thanks, <signature>







vms-radius-checkout-emp-sms-template

{
	"senderID": "",
	"empFirstName": "",
	"visitorName": "",
	"visitorCheckOutDate": "",
	"visitorCheckOutTime": "",
}

<senderID>
Dear <empFirstName>, Visitor <visitorName> has been successfully checked out at <visitorCheckOutDate> <visitorCheckOutTime>







vms-radius-checkout-visitor-sms-template
{
	"senderID": "",
	"customerName": "",
	"signature": "",
	"visitorName": ""
}

<senderID>
Welcome <visitorName>. You have been successfully checked out. Thanks for visiting <customerName> premises. Regards, <signature>





Lambda:
--------

vms-radius-checkin-emp-email-check
// if it is enabled then pass y and email template name
// else pass n and no email template name






vms-radius-checkin-emp-email
{
	"templateName":"vms-radius-checkin-emp-email-template",

	"fromName": "",
	"fromEmail": "",
	"signature": "",	
	"empFirstName": "",
	"empLastName": "",
	"empEmail": "", 
	"visitorName": "",
	"visitorEmail": "",
	"visitorMobile": "",
	"visitorOrganization": "",
	"visitorPurpose": "",
	"visitorCheckInDate": "",
	"visitorCheckInTime": ""
}




vms-radius-checkin-visitor-email
{

}




vms-radius-checkin-emp-sms
{


}


vms-radius-checkin-visitor-sms
{


}




vms-radius-checkout-emp-email
{

}




vms-radius-checkout-visitor-email
{

}





vms-radius-checkout-emp-sms
{

}



vms-radius-checkout-visitor-sms
{

}




vms-radius-daily-visitor-report
{

}



vms-radius-from-to-visitor-report
{

}




vms-radius-metadata-emp-insert
vms-radius-metadata-emp-update
vms-radius-metadata-emp-delete
vms-radius-metadata-emp-selectall
vms-radius-metadata-emp-find
vms-radius-metadata-emp-bulk-upload



checkin-flow:

{
  "Comment": "CheckIn Flow",
  "StartAt": "CheckIn",
  "States": {
    "CheckIn": {
      "Type": "Parallel",
      "End": true,
      "Branches": [
        {
         "StartAt": "CheckInEmployeeEmail",
         "States": {
           "LookupAddress": {
             "Type": "Task",
             "Resource":
               "arn:aws:lambda:us-east-1:123456789012:function:AddressFinder",
             "End": true
           }
         }
       },
        {
         "StartAt": "CheckInEmployeeSMS",
         "States": {
           "LookupAddress": {
             "Type": "Task",
             "Resource":
               "arn:aws:lambda:us-east-1:123456789012:function:AddressFinder",
             "End": true
           }
         }
       },
        {
         "StartAt": "CheckInVisitorEmail",
         "States": {
           "LookupAddress": {
             "Type": "Task",
             "Resource":
               "arn:aws:lambda:us-east-1:123456789012:function:AddressFinder",
             "End": true
           }
         }
       },
       {
         "StartAt": "CheckInVisitorSMS",
         "States": {
           "LookupPhone": {
             "Type": "Task",
             "Resource":
               "arn:aws:lambda:us-east-1:123456789012:function:PhoneFinder",
             "End": true
           }
         }
       }
      ]
    }
  }
}

