# amazon-cloud-formation-couchbase

[generator](generator) is a template generator for advanced configurations for Kafka. For now this code can work with Ubuntu AMI.

# Update your information before execute generator.py (see below notes)
  1) The NEW AMI
  2) The command which need to apppend "command.append"
  3) To update your zone name and Record name to update on AWS Route53.
         "zone_name=glp-test3.com"
        "rec_name=kafka.${zone_name}"
  4) scripts/server.sh: This script will upate EC2-Tag name
  5) scripts/UpdateRoute53-yml.sh: This script will upate Route53
  6) scripts/setup-kafka.yml: This script will configure kafak
  7) scripts/setup-zookeepr.yml: This script will configure zookeeper for kafak
    

# How to executed generator.py
 1) cd generator/
 2) ./deploy.sh '<StackName>'   (Specify your StackName, ex. ./deploy.sh glp-kafka-test)
 3) ls -l generated.template    (Here it will genrate template file to upload in Cloud Formation)




