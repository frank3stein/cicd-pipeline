

1.





2. ansible-playbook main-remote.yaml -i inventory --private-key ~/.ssh/udacity.pem

```bash
# writing instance ips into a file 
aws ec2 describe-instances \                                            
   --query 'Reservations[*].Instances[*].PublicIpAddress' \
   --output text >> inventory


# starting ssh agent
eval "$(ssh-agent -s)"

# so we have the key with limited permissions
chmod 700 ~/.ssh/udacity.pem

```