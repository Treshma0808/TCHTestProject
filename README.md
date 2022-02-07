# TCHTestProject
Overview on the project over all details
----------------------------------------
1. Required AWS S3 bucket and CSV file with required data created in AWS S3 bucket manually. 
2. Created Programatic IAM User credentials which will allows the application running on EC2 to interact with the CSV file available in AWS S3.
3. Created AWS EC2 instance to host the JAVA application and run the same JAVA application from AWS console from where user input the serach criteria and receive resulted rows.
4. Note that the above steps can also be created either using Terraform or Cloudformation templates.However, manually created for the time being in the interest of time.
5. Note that building the docker image , deploying the code on to EC2 instance using jenkins pipeline can also be done as a further improvement for this project.
6. All the required AWS infrastracture is created in default VPC. However, it can furter improve the security of the application by addding the Custom VPC, Fire Walls, Subnets and inpound/outbound rules of EC2 instances.

Overview on the project execution details
-----------------------------------------
1. Create the bucket with bucket URL as "s3://mg-filesearch-test/bank/"
2. Placed the CSV file with required data for the columns names Bank Name, Type, City, State and Zip Code in "Banks.csv" file
3. Install the Open JDK on the EC2 instance
4. Verify the JAVA version on the EC2 instance from EC2 console
5. Copy the final JAR file on to EC2 instance
6. Chnage the permissions of the JAR file on EC2 instance using commands "chmod 777 *"   or "chmod 755 *"
7. Execute the JAR using the command "java -jar filesearch-0.0.1-SNAPSHOT.jar"
	It will display the below options for the user to input
		Enter the column numbers for searching like 1,2,4 without any whitespace
			0 - All Data
			1 - Bank Name
			2 - Type
			3 - City
			4 - State
			5 - Zip Code
		Below example where the User input the column numbers and the ncorresponding column names as below
			1,5
			Enter Bank Name
				SBI
			Enter Zip Code
				400102
		The following resulted rows have been returned
			SBI,Government,Mumbai,Maharashtra,400102
			
8. The S3 SELECT QUERY language been used in the application with which serach is carried out on CSV file using the user supplied serach fields.
				

