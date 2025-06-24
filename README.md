# ntu-sctp-assignment-2.15

1. What is needed to authorize your EC2 to retrieve secrets from the AWS Secrets Manager?

    An IAM role attached to the EC2 instance, granting it permission to access the specific secret in Secrets Manager.

    This role must have a policy that allows the secretsmanager:GetSecretValue action on the target secret resource.

   2. Derive the IAM policy (i.e., JSON)

Assuming the secret is named prod/cart-service/credentials and located in region us-east-1 under account 123456789012, the policy would look like:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "secretsmanager:GetSecretValue",
      "Resource": "arn:aws:secretsmanager:us-east-1:123456789012:secret:prod/cart-service/credentials-*"
    }
  ]
}
