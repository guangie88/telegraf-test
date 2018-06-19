# `telegraf-test`

Run example Telegraf service in Docker container and captures `cloudwatch`
logs with given encrypted AWS credentials.

First decrypt the secrets with the known passphrase:

```bash
ansible-playbook -i "localhost," -c local --ask-vault-pass main.yml
```

Next spin up the service:

```bash
docker-compose up -d
```

To check the logs, run:

```bash
docker-compose logs
```

Since `cloudwatch` has an interval of 5 mins for each type of logs, you might
have to wait a while before the logs start to appear.

A log example:

```txt
telegraf    | cloudwatch_aws_ebs,host=b0893f330c74,region=ap-southeast-1,unit=seconds,volume_id=vol-06a7485f9db071ce5 volume_idle_time_sum=299.84,volume_idle_time_average=299.84,volume_idle_time_maximum=299.84,volume_idle_time_minimum=299.84,volume_idle_time_sample_count=1 1529369700000000000
```
