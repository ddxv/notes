1.  Launch instance with security group: ‘SSH from everywhere’ or at least your IP open for SSH
    
2.  Setup Python: [Python Installation & Environments](404488222.html)
    
3.  Prep AWS Instance [https://docs.aws.amazon.com/codedeploy/latest/userguide/getting-started-codedeploy.html](https://docs.aws.amazon.com/codedeploy/latest/userguide/getting-started-codedeploy.html)
    
    1.  Prepare IAM Role and Permissions
        
    2.  Attach IAM Role to Instance (note this user’s keys should be used later)
        
    3.  Install AWS CLI [https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
        
    4.  Configure AWS CLI [https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html)
        
        1.  `aws configure` with keys from IAM Deploy User’s Secret keys or from \`~/.aws/credentials\` from another server
            
4.  Install Code Deploy
    
    1.  Official steps (note, check workarounds): [https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent-operations-install-ubuntu.html](https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent-operations-install-ubuntu.html)
        
        1.  If helpful: `wget https://aws-codedeploy-us-west-1.s3.us-west-1.amazonaws.com/latest/install`
            
        2.  **Workaround** for Ubuntu 20.04 [https://github.com/aws/aws-codedeploy-agent/issues/264](https://github.com/aws/aws-codedeploy-agent/issues/264)
            
        3.  **Workaround** for Ubuntu 22.04 (Ruby version 3 not supported error): [https://github.com/aws/aws-codedeploy-agent/issues/301](https://github.com/aws/aws-codedeploy-agent/issues/301) specifically the steps from moosthuizen42 commented on May 18
            
5.  Reboot
    
6.  `ssh-keygen` to generate new keypair and add id\_rsa.pub to any required repositories (ie py-dbcon)
    
7.  Install py-dbcon:
    
    1.  Add db\_config.yml to .config/bubbleye\_adops/
        
    2.  Add `export PROD="True"` and run `source ~/.bashrc`
