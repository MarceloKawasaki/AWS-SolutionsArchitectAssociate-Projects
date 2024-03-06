# Connect to EC2 Instance via SSH 

1. Login into AWS Account
2. Go to EC2 console and click Launch Instance button
3. Create Key Pair
    - Enter name
    - Key pair type: RSA
    - Private key format: .pem (SSH)
    - Store Private Key in local directory
4. Creating Security Group
    - Enter name and description
    - Allow Inbound Rules
      - SSH, TCP, Port 22, Custom, 0.0.0.0/0 (IPv4)
      - SSH, TCP, Port 22, Custom, ::/0 (IPv6)
5. Creating EC2 Instance
    - Enter name
    - Choose OS
    - Choose any Free-Tier AMI and Instance Type
    - Select Key Pair created
    - Select existing Security Group
    - Launch Instance (wait until status is Running)
6. Select Instance and click Connect
7. Then, select SSH client tab and copy the example ```ssh -i ....``` command
8. Start Shell in the directory where the Private Key is located
9. Paste the command in the Shell
10. If says the permission for the key are to open
    - UNIX: just copy from the EC2 instance connect the command ```chmod 400 <key name>```
    - Windows: right click private key locally > properties > security > advanced > remove all but own User
