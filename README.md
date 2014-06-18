# cirrus
Cloud Integration Reporting and Replication UtilitieS

## Installation
```javascript
npm install
```

## Usage
Cirrus supports a series of sub-commands related to key elements of the AWS cloud infrastructure.
For example, to get disk use by a bucket called "myBucket"

```javascript
cirrus s3 du myBucket
```

At each level, help can be provided with the -h flag. For example, to get help for cirrus, the command is:

```javascript
cirrus -h
```

To get help with the S3 commands:

```javascript
cirrus s3 -h
```

To get help with the S3 du command:

```javascript
cirrus s3 du -h
```


## Options
| Option             | Description                                              |
|--------------------|----------------------------------------------------------|
| -h, --help | output usage information |
| -v, --version | output version number |
| -c, --config &lt;path&gt; | path to config file relative to cirrus.js; defaults to config.json |
|   **S3 (Simple Storage Solution)**                              ||
| -h | help for S3 commands |
| ls | list all buckets |
| du &lt;bucket&gt; | disk usage for objects in a specified &lt;bucket&gt; |
| mkdir &lt;bucket&gt; | create &lt;bucket&gt; |
| rm &lt;bucket&gt; | remove &lt;bucket&gt;, prompts if not empty |
| scp &lt;path&gt; &lt;bucket&gt; | put items in &lt;path&gt; recursively (if dir) into destination &lt;bucket&gt; |
|   **EC2 (Elastic Cloud Compute)**                              ||
| -h | help for EC2 commands |
| ls &#91;-t, --types&#93; | list all instances &#91;lists instance types&#93; |
| stop &lt;instance&gt; | stop &lt;instance&gt; |
| start &lt;instance&gt; | start &lt;instance&gt; |
| terminate &lt;instance&gt; | terminate &lt;instance&gt; |
| setinstance &lt;instance&gt; &lt;type&gt; | sets &lt;instance&gt; to be specified &lt;type&gt; |
|   **EIP (Elastic IP)**                              ||
| -h | help for EIP commands |
| ls | list all Elastic IPs |
| allocate | request a new Elastic IP address |
| release &lt;allocation ID&gt; | releases an Elastic IP allocation &lt;allocation id&gt; |
| associate &lt;allocation ID&gt; &lt;instance&gt; | associates an Elastic IP allocation &lt;allocation id&gt; with an &lt;instance&gt; |
| disassociate &lt;association ID&gt; | disassociates an Elastic IP association &lt;association id&gt; between an EIP allocation and and instance |
|   **EBS (Elastic Block Store)**                              ||
| -h | help for EBS commands |
| ls | list all EBS volumes |

## Configuration
Cirrus takes a JSON configuration file. By default, the script will look for config.json (but can be overriden with the -c &lt;path&gt; flag, with a relative path from the location of cirrus.js).

```json
{
    "accessKeyId": "yourPublicKeyHere",
    "secretAccessKey": "yourPrivateKeyHere",
    "region": "yourRegionHere"
}
```

aws.json

aws.json.sample

## TODOs
### full cloud
- --cloud-list
- --cloud-compare &lt;path&gt; path to existing compare, will compare with provided config
- --cloud-deploy
- --cloud-snapshot &lt;path&gt; path to store config

### ec2
- create

### sg
- list sg?

### s3
- get contents
- rename
- copy bucket to another bucket

### ebs
- attach
- detach
- create snapshot
- create volume
- create volume from snapshot
- delete volume
- bundle steps to resize volume?

### eip
- work with entities by their IP addresses?

## Version 2
### sg
- setsg
- create sg?
- grant/revoke sg ingress/egress?
- delete sg?
- move sg ops into own subcommand?



##
--> tags column optional (if has more tags than name) always show name column)
ENFORCE NAME TAG - confirm uniqueness (EC2, EBS volumes)
	-> use name tag for instance reference (stop myInstance)
	-> have way to rename instance (still enforce uniqueness)

	then in args, can specify name
	-> check first if there is something with the name, if not, check if instance id equal to arg

--> make table lines optional (maybe -h flag?)

--> volumes