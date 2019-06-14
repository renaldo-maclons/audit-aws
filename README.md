# Audit AWS
This deployment is intended for the following AWS use cases:

##Auditing your AWS for:

1.  Usage and Billing.

2.  User reports:
  * Service access lists.
  * Console Authentication history
  * API Authentication history

3.  Cataloging:
  * EC2 instances.
  * S3 Buckets.
  * Lambda Functions.

## Setup
### Prerequisites
What do you need?

Any operating system that supports:
* Git
* Ansible
* AWSCLI (Latest Version)

## Deployment
To run the playbook you are required to have an existing aws configured profile with at minimum, view permissions for the services you wish to audit, To setup your AWS profile simply run the following on the host machine and supply the information.

```bash
aws configure
```

### Getting started

If you have the prerequisites all setup simply follow the steps below:
Clone the git repo.

```bash
git clone https://github.com/rnjudas/audit-aws
```

Change directory to the local repo:
```bash
cd audit-aws
```

Run the Ansible playbook with any of your desired options set to true. Alternatively you are able to use this playbook as is with Jenkins or any other Ci/CD server that allows for the specification of booleans at runtime.

```bash
ansible-playbook -i 'localhost,' ./play.yml -e "ROLE=audit-aws" -e "TARGET=localhost" -e "USER=ubuntu" \
-e "USER_REPORT=true" -e "EC2_REPORT=false" -e "LAMBDA_REPORT=false" -e "S3_REPORT=false" \
-e "RDS_REPORT=false" -e "CLOUDFRONT_REPORT=false" \
-e "CLOUDFORMATION_REPORT=false" -e "COST_USAGE_REPORT=false" -e "DAYS=1" \
-e "USER_AUTH_REPORT=false"
```
The results of the audit can be found in `private/csv`

## Security
To make use of the billing module you will be required to use an AWS account with the needed policies to view billing information.

## Built With

* [Ansible](https://www.ansible.com/) - The automation tool used
* [Vagrant](https://www.vagrantup.com/) - Portable virtual software maintainer
* [Virtualbox](https://www.virtualbox.org/wiki/VirtualBox) -  General-purpose full virtualizer for x86 hardware

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/rnjudas/43b79c93e9622ace6ec6b2debc18fb63) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning
~~~
N/A
~~~

## Authors

* **Renaldo Maclons** - *Initial work* - [RNJudas](https://github.com/rnjudas)

See also the list of [contributors](https://github.com/rnjudas) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](https://gist.github.com/rnjudas/b8c1f9e9c8762a8885ec47461a0e3b32) file for details

## Acknowledgments

* **Henning Jacobs** - *AWS Cost Report* - [hjacobs](https://github.com/hjacobs)
