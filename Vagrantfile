require File.expand_path('~/.aws/aws_credentials.rb')

Vagrant.configure("2") do |config|

# AWS data #
access_key_id=@access_key_id # Dado al crear el usuario en Amazon IAM
secret_access_key=@secret_access_key # Dado al crear el usuario en Amazon IAM
box="dummy"
instance_type="t1.micro"
sec_groups = ["vagrant"]

# Ireland
ami = "ami-06ba5571" # LAMP: https://aws.amazon.com/marketplace/ordering/ref=dtl_psb_continue?ie=UTF8&productId=b9eca685-95fe-44c5-9474-ffb90661c396&region=us-east-1
ssh_username="bitnami"
priv_key=File.expand_path("~/.aws/vagrantEU.pem")
keypair_name="vagrantEU"
region = "eu-west-1"

# AWS data #

    config.vm.box = box

    config.ssh.private_key_path = priv_key

    config.vm.provider :aws do |aws, override|
      aws.access_key_id=access_key_id 
      aws.secret_access_key=secret_access_key
      aws.keypair_name = keypair_name
      aws.instance_type = instance_type
      aws.ami = ami
      aws.security_groups = sec_groups 
      aws.region = region
      override.ssh.username = ssh_username
#      aws.elastic_ip = true #?
      aws.tags = {
        'Deployer' => "vagrant"
      }
      aws.user_data = "#!/bin/bash\necho 'got user data' > /tmp/user_data.log\necho"
    end
end
