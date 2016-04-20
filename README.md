aws cloudformation create-stacka \
--capabilities CAPABILITY_IAM \
--stack-name SuzlabEnv \
--template-body file://./env.json \

aws cloudformation create-stack \
--capabilities CAPABILITY_IAM \
--stack-name SuzlabVpc \
--template-body file://./vpc.json \
--parameters '[{"ParameterKey":"NatGatewayEipAllocationId"},{"ParameterValue":"eipalloc-380aa45d"}]'

aws cloudformation create-stack \
--capabilities CAPABILITY_IAM \
--stack-name SuzlabEc2 \
--template-body file://./ec2.json \
--parameters '[{"ParameterKey":"CommonEc2Role","ParameterValue":"SuzlabEnv-CommonEc2Role-1MRT4ZRP8F43B"},{"ParameterKey":"Subnet","ParameterValue":"subnet-e59fa492"}]'
