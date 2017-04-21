this is adapted from:
https://github.com/icereval/charts/tree/feature/fluentd-cloudwatch/incubator/fluentd-cloudwatch

To work with secrets from Helm, see:
https://github.com/kubernetes/charts/tree/6b20d270f48fd6f56001fbd657790664e1d18561/incubator/fluentd-logentries


Secrets decryptions:
From: https://random.ac/cess/2017/02/04/simple-aws-cli-kms-encrypt-decrypt-example/

aws kms encrypt --key-id 3c436c82-eabe-4b58-996f-6ca3f808f237 --plaintext fileb://my-secret-key.pem --query CiphertextBlob --output text | base64 -d | base64 -w 76 > encrypted.asc
aws kms decrypt --ciphertext-blob fileb://<(cat encrypted.asc | base64 -d) --output text --query Plaintext | base64 -d > decrypted.txt

Also possible:
Put the secret as env var in circleci, and write it to file. On the local machine, it wouldn't work though.

Maybe using the container is the best option. A go version of kmstool would be nice.

Checkout unicreds:
https://github.com/Versent/unicreds
(golang version of credstash)

Checkout https://github.com/mike-zenith/kmstool
encrypt decryp files with KMS



There is a problem to use this, for now:
https://github.com/fluent/fluentd-kubernetes-daemonset/issues/13
