- `Amazon`的`AWS`提供相當完整的雲端產品，供個人、企業組織或其它團體依自身環境的條件與需求彈性使用。
- 亞馬遜雲端服務主要提供超過 40 多種不同的服務，例如運算、儲存、內容傳輸、資料庫、 分析作業、應用服務、管理和部署、網路等，讓使用者能輕鬆建立其應用程式或服務， 並在AWS雲端實際執行。
- AWS的管理介面：AWS Management Console讓使用者可以方便管理其運算、儲存與其它雲端資源。
- `EC2`為雲端裡的虛擬伺服器，稱之為`instance`，是一項可供使用者在雲端上彈性調整計算效能的伺服器服務。除了`Windows`外，`AWS`亦提供多項主流`Linux`分支套件可取用，像是`Red Hat Enterprise`、`SUSE`與`Ubuntu`等。
- 亞馬遜的簡易儲存服務（Simple Storage Service，Amazon S3）
- 亞馬遜CloudFront為CDN服務，讓企業可透過該服務加速內容遞送、降低延遲。

亞馬遜雲端服務（AWS, Amazon Web Services）
虛擬私人雲（virtual private cloud，簡稱VPC）

---

```console
shell> export AWS_ACCESS_KEY=your-aws-access-key-id
shell> export AWS_SECRET_KEY=your-aws-secret-key
```

```console
shell> file /etc/alternatives/java
shell> export JAVA_HOME=/usr/lib/jvm/java-6-openjdk-amd64/jre
shell> $JAVA_HOME/bin/java -version
```
```console
shell> export EC2_HOME=/usr/local/ec2/ec2-api-tools-1.7.0.0
shell> export PATH=$PATH:$EC2_HOME/bin
```
```console
shell> ec2-describe-regions

REGION	eu-west-1	ec2.eu-west-1.amazonaws.com
REGION	sa-east-1	ec2.sa-east-1.amazonaws.com
REGION	us-east-1	ec2.us-east-1.amazonaws.com
REGION	ap-northeast-1	ec2.ap-northeast-1.amazonaws.com
REGION	us-west-2	ec2.us-west-2.amazonaws.com
REGION	us-west-1	ec2.us-west-1.amazonaws.com
REGION	ap-southeast-1	ec2.ap-southeast-1.amazonaws.com
REGION	ap-southeast-2	ec2.ap-southeast-2.amazonaws.com
```
```console
shell> export EC2_URL=https://<service_endpoint>  
shell> export EC2_URL=https://ec2.us-west-1.amazonaws.com
```

```console
shell> ec2-create-keypair my-key-pair

KEYPAIR	my-key-pair	1f:51:ae:28:bf:89:e9:d8:1f:25:5d:37:2d:7d:b8:ca:9f:f5:f1:6f
---- BEGIN RSA PRIVATE KEY ----
MIICiTCCAfICCQD6m7oRw0uXOjANBgkqhkiG9w0BAQUFADCBiDELMAkGA1UEBhMC
VVMxCzAJBgNVBAgTAldBMRAwDgYDVQQHEwdTZWF0dGxlMQ8wDQYDVQQKEwZBbWF6
b24xFDASBgNVBAsTC0lBTSBDb25zb2xlMRIwEAYDVQQDEwlUZXN0Q2lsYWMxHzAd
BgkqhkiG9w0BCQEWEG5vb25lQGFtYXpvbi5jb20wHhcNMTEwNDI1MjA0NTIxWhcN
MTIwNDI0MjA0NTIxWjCBiDELMAkGA1UEBhMCVVMxCzAJBgNVBAgTAldBMRAwDgYD
VQQHEwdTZWF0dGxlMQ8wDQYDVQQKEwZBbWF6b24xFDASBgNVBAsTC0lBTSBDb25z
b2xlMRIwEAYDVQQDEwlUZXN0Q2lsYWMxHzAdBgkqhkiG9w0BCQEWEG5vb25lQGFt
YXpvbi5jb20wgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBAMaK0dn+a4GmWIWJ
21uUSfwfEvySWtC2XADZ4nB+BLYgVIk60CpiwsZ3G93vUEIO3IyNoH/f0wYK8m9T
rDHudUZg3qX4waLG5M43q7Wgc/MbQITxOUSQv7c7ugFFDzQGBzZswY6786m86gpE
Ibb3OhjZnzcvQAaRHhdlQWIMm2nrAgMBAAEwDQYJKoZIhvcNAQEFBQADgYEAtCu4
nUhVVxYUntneD9+h8Mg9q6q+auNKyExzyLwaxlAoo7TJHidbtS4J5iNmZgXL0Fkb
FFBjvSfpJIlJ00zbhNYS5f6GuoEDmFJl0ZxBHjJnyp378OD8uTs7fLvjx79LjSTb
NYiytVbZPQUQ5Yaxu2jXnimvw3rrszlaEXAMPLE
-----END RSA PRIVATE KEY-----
```

my-key-pair.pem
"----BEGIN RSA PRIVATE KEY----"
"-----END RSA PRIVATE KEY-----" 
```console
shell> chmod 400 my-key-pair.pem
```
```console
shell> ec2-create-group my-security-group -d "My security group"
shell> ec2-authorize my-security-group -p 3389 -s 203.0.113.25/32
shell> ec2-authorize my-security-group -p 22 -s 203.0.113.25/32
```
```console
shell> ec2-create-group websrv -d "Web Servers"
shell> ec2-authorize websrv -P tcp -p 80 -s 192.0.2.0/24
shell> ec2-authorize websrv -P tcp -p 80 -s 0.0.0.0/0
```
```console
shell> ec2-run-instances ami-xxxxxxxx -t t1.micro -k my-key-pair -g my-security-group
```

Ubuntu Server 14.04 LTS (HVM), SSD Volume Type
```console
shell> ec2-run-instances ami-a7fdfee2 -t t2.micro -k my-key-pair -g my-security-group
```
```console
shell> ec2-describe-instances
```
```console
shell> ssh -i my-key-pair.pem ec2-user@ec2-198-51-100-1.compute-1.amazonaws.com
shell> ssh -i my-key-pair.pem ubuntu@ec2-54-183-170-94.us-west-1.compute.amazonaws.com
```
```console
shell> ec2-stop-instances i-afb4bcf1
shell> ec2-start-instances i-afb4bcf1
shell> ec2-terminate-instances i-afb4bcf1
```

---


/usr/local/share/awscli/examples

```console
shell> aws help
```

```console
shell> aws configure
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: ap-northeast-1
Default output format [None]: ENTER
```

~/.aws/credentials
```
[default]
aws_access_key_id=AKIAIOSFODNN7EXAMPLE
aws_secret_access_key=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY

[user2]
aws_access_key_id=AKIAI44QH8DHBEXAMPLE
aws_secret_access_key=je7MtGbClwBF/2Zp9Utk/h3yCo8nvbEXAMPLEKEY
```

~/.aws/config
```
[default]
region=us-west-2
output=json

[profile user2]
region=us-east-1
output=text

```

```console
shell> aws ec2 describe-instances
shell> aws ec2 describe-instances --profile user2
shell> aws ec2 describe-instances --instance-ids 

shell> aws ec2 run-instances --image-id ami-29ebb519 --security-group-ids sg-0cd9dd68 --count 1 --instance-type t2.micro --key-name devenv-key --query 'Instances[0].InstanceId'

shell> aws ec2 terminate-instances --instance-ids i-1234567890abcdef0
```

```console
shell> aws ec2 create-security-group --group-name my-sg --description "My security group"
{
    "GroupId": "sg-903004f8"
}

shell> aws ec2 delete-security-group --group-name MySecurityGroup
shell> aws ec2 delete-security-group --group-id sg-903004f8

```



**Amazon S3 的檔案命令**
```console
shell> aws s3 ls
shell> aws s3 cp myfolder s3://mybucket/myfolder --recursive
shell> aws s3 sync myfolder s3://mybucket/myfolder --exclude *.tmp

````

run-instances
start-instances
stop-instances
terminate-instances
delete-security-group

- [terminate-instances](http://docs.aws.amazon.com/cli/latest/reference/ec2/terminate-instances.html)
- [delete-security-group](http://docs.aws.amazon.com/cli/latest/reference/ec2/delete-security-group.html)
- [create-vpc](http://docs.aws.amazon.com/cli/latest/reference/ec2/create-vpc.html)
- [cli-aws](http://docs.aws.amazon.com/cli/latest/reference/index.html#cli-aws)
- [aws](https://aws.amazon.com/tw/cli/)

#### :books: 參考網站：
- [AccessingInstancesLinux](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)
- [ec2-cli-launch-instance](http://docs.aws.amazon.com/AWSEC2/latest/CommandLineReference/ec2-cli-launch-instance.html)
- [http://www.bnext.com.tw/article/view/id/26928](http://www.bnext.com.tw/article/view/id/26928)
- [http://www.runpc.com.tw/content/content.aspx?id=109436](http://www.runpc.com.tw/content/content.aspx?id=109436)
