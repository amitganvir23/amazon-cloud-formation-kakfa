# amazon-cloud-formation-couchbase

[generator](generator) is a template generator for advanced configurations for Kafka. For now this code can work with Ubuntu AMI.

# Update your information before execute generator.py (see below notes)
  1) Update your New Ubuntu AMI on your region.
  2) The command which need to apppend "command.append"
  3) To update your zone name and Record name to update on AWS Route53.
         "zone_name=glp-test3.com"
        "rec_name=kafka.${zone_name}"
  4) scripts/setup.sh: This script will upate EC2-Tag name and required packages on EC2.
  5) scripts/UpdateRoute53-yml.sh: This script will upate Route53.
  6) scripts/setup-kafka.yml: This script will configure kafak.
  7) scripts/setup-zookeepr.yml: This script will configure zookeeper for kafak.
  8) zookeeper-templates/log4j.properties: This is zookeeper config file and we can make our required changes here. This file is define as variable (log4j_properties_url:) in scripts/setup-zookeepr.yml file.
  9) kafka-templates/server.properties: This is kafka config file and we can make our required changes here. his file is define as variable (server_properties_url:) in scripts/setup-kafka.yml file.
  10) Update your AWS AutoScalling part
  

# How to executed generator.py
 1) $cd generator/
 2) $vim parameters/granular.yaml   (Update your nodeType, nodeCount and dataDiskSize)
 2) .$/deploy.sh [Your Stack Name]   (Specify your StackName, ex. ./deploy.sh glp-kafka-test)
 3) $ls -l generated.template    (Here it will genrate template file to upload in Cloud Formation)
 4) Please update below parameters while updating template
      - Stack name: [Your Stack Name]
      - CidrIpVPC: [CIDIR Value from the subnet]
      - KeyName: [Select Key Pair]
      - License: BYOL
      - Subnets: [Select Subnet]
      - VpcId: [Select VPC]
    Example:
      - Stack name: glp-kafka-test
      - CidrIpVPC: 172.168.0.0/16
      - KeyName: terraform-support-keys
      - License: BYOL
      - Subnets: subnet-da38e6a0
      - VpcId: vpc-e860a6180



