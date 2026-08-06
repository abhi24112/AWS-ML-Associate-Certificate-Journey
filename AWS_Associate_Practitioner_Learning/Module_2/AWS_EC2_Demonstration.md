# AWS Elastic Computer Cloud (EC2)
All interactions with services are powered by APIs. 

You can access these APIs through three primary methods: the AWS Management Console, the AWS CLI, or the AWS SDK. Let's review these methods.

# Usage of the instance
1. After the instance creation
2. Look for Public IP (Public IPv4 address): e.g. 18.206.176.107
3. on browser search http://18.206.176.107
4. You will see the ngix page (as setup)

# Working Diagram
graph TD
    %% AWS Console EC2 Creation Path
    A[AWS Management Console] -->|Search 'EC2'| B[EC2 Dashboard]
    B -->|Click 'Launch instance'| C[Launch an instance Screen]

    subgraph Step 1: Name & OS
        C -->|Type Name: 'My-First-Server'|D[Name and tags]
        D -->|Select 'Amazon Linux' AMI| E[Application and OS Images]
    end

    subgraph Step 2: Instance Type & Keys
        E -->|Select 't3.micro' Free Tier| F[Instance type]
        F -->|Click 'Create new key pair'| G[Key pair section]
        G -->|Type: rsa , Save .pem file locally| G
    end

    subgraph Step 3: Network & Storage
        G -->|Allow HTTP traffic from the internet| H[Network settings]
        H -->|Leave default 8 GiB gp3| I
    end
    
    subgraph Step 4: Advance Options
			I[Advance Options]--> |User data| J[#!/bin/bash<br/><br/>yum install -y nginx<br/>systemctl start nginx<br/>systemctl enable nginx]
		end

    J -->|Click 'Launch instance'| K((EC2 Active))
