Assignment 3:
Topics Covered:  (Configuring Agents, Various Methods, Distributing Loads, Executors, Assigning Nodes)
     Assignment on configuring Nodes
        Configure a Ubuntu node using execution of command on the master method. 
        - Make sure at any point of time maximum 5 jobs can be executed on this node.
        - Assign this node to Assignment 2: Part 1 


  <img width="357" alt="image" src="https://github.com/OT-MyGurukulam/Jenkins_Batch23/assets/98215406/5ddff156-4f7c-4b33-90ea-8cd7910fb9c8">

  Slave Configuration
Download the slave.jar file from the Jenkins master machine to the slave machine using the wget command and make it executable.
Run this command on the slave machine to download the slave.jar file from the master machine. Copy the public IP address of the master machine and replace the IP address in the command with it
- mkdir workspace
- cd workspace
- sudo wget http://18.179.28.182:8080/jnlpJars/slave.jar

  <img width="917" alt="image" src="https://github.com/OT-MyGurukulam/Jenkins_Batch23/assets/98215406/1472abc3-79d3-4016-beae-e5a60c86dde6">

  Log in to the Jenkins server and navigate to the main dashboard.
Click on “Manage Jenkins”.
Click on “Nodes”.
Click on “New Node”.
Enter a node name (e.g. “slave_01”).
Select “Permanent Agent”.
Enter the node description (optional).
Enter the remote root directory by typing “/home/ubuntu/workspace” in the “Remote root directory” field.
Enter the labels (tags) for the node by typing “slave_lab” in the “Labels” field (optional).
Select “Launch agent via execution of command on the controller” as the launch method.
In the “Launch command” field, enter the following command: (Replace public IP of your slave)
- ssh ubuntu@35.77.200.67 java -jar /home/ubuntu/workspace/slave.jar
Click on “Save” to save the configuration.
Approve script in Manage Jenkins -> In-process Script Approval
Start the slave node by clicking on the “Launch agent” button on the “Nodes” page. The node should now be connected to the master machine and ready to use.

<img width="695" alt="image" src="https://github.com/OT-MyGurukulam/Jenkins_Batch23/assets/98215406/c9ff5b16-93c6-4273-8230-266fcbd78c56">



        Configure a RHEL node using  Launch slave agents via SSH method. 
        - Make sure at any point of time maximum 2 jobs can be executed on this node.
        - Assign this node to Assignment 2: Part 2
        Configure a CentOS node using Launch slave agents via SSH method. 
        - Make sure at any point of time maximum 3 jobs can be executed on this node.
        - Assign this node to Assignment 3
        Configure a Windows node using method of your choice
        - Download one sample application of .NET and build it on Windows Node.
