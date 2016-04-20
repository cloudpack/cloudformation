aws cloudformation create-stack \
--capabilities CAPABILITY_IAM \
--stack-name CloudpackEnv \
--template-body file://./env.json

aws cloudformation create-stack \
--capabilities CAPABILITY_IAM \
--stack-name CloudpackTest \
--template-body file://./test.json \
--parameters '[{"ParameterKey":"NatGatewayEipAllocationId","ParameterValue":"eipalloc-xxxxxxxx"},{"ParameterKey":"CommonEc2Role","ParameterValue":"CloudpackEnv-CommonEc2Role-XXXXXXXXXXXXX"}]'

aws cloudformation create-stack \
--capabilities CAPABILITY_IAM \
--stack-name SuzlabEc2 \
--template-body file://./ec2.json \
--parameters '[{"ParameterKey":"CommonEc2Role","ParameterValue":"SuzlabEnv-CommonEc2Role-1MRT4ZRP8F43B"},{"ParameterKey":"Subnet","ParameterValue":"subnet-e59fa492"}]'
