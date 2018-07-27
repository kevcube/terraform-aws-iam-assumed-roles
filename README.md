<!-- This file was automatically generated by the `build-harness`. Make all changes to `README.yaml` and run `make readme` to rebuild this file. -->

[![Cloud Posse](https://cloudposse.com/logo-300x69.svg)](https://cloudposse.com)

# terraform-aws-iam-assumed-roles [![Build Status](https://travis-ci.org/cloudposse/terraform-aws-iam-assumed-roles.svg?branch=master)](https://travis-ci.org/cloudposse/terraform-aws-iam-assumed-roles) [![Latest Release](https://img.shields.io/github/release/cloudposse/terraform-aws-iam-assumed-roles.svg)](https://github.com/cloudposse/terraform-aws-iam-assumed-roles/releases/latest) [![Slack Community](https://slack.cloudposse.com/badge.svg)](https://slack.cloudposse.com)


Terraform module to provision two IAM roles and two IAM groups for assuming the roles provided MFA is present,
and add IAM users to the groups.

- Role and group with Administrator (full) access to AWS resources
- Role and group with Readonly access to AWS resources

To give a user administrator's access, add the user to the admin group.

To give a user readonly access, add the user to the readonly group.


---

This project is part of our comprehensive ["SweetOps"](https://docs.cloudposse.com) approach towards DevOps. 


It's 100% Open Source and licensed under the [APACHE2](LICENSE).










## Usage

```hcl
module "assumed_roles" {
  source              = "git::https://github.com/cloudposse/terraform-aws-iam-assumed-roles.git?ref=master"
  namespace           = "cp"
  stage               = "prod"
  admin_name          = "admin"
  readonly_name       = "readonly"
  admin_user_names    = ["User1","User2"] # Add these IAM users to the admin group
  readonly_user_names = ["User3","User4"] # Add these IAM users to the readonly group
}
```






## Makefile Targets
```
Available targets:

  help                                This help screen
  help/all                            Display help for all targets
  lint                                Lint terraform code

```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| admin_name | Name for the admin group and role (e.g. `admin`) | string | `admin` | no |
| admin_user_names | Optional list of IAM user names to add to the admin group | list | `<list>` | no |
| attributes | Additional attributes (e.g. `policy` or `role`) | list | `<list>` | no |
| delimiter | Delimiter to be used between `namespace`, `stage`, `name`, and `attributes` | string | `-` | no |
| namespace | Namespace (e.g. `cp` or `cloudposse`) | string | - | yes |
| readonly_name | Name for the readonly group and role (e.g. `readonly`) | string | `readonly` | no |
| readonly_user_names | Optional list of IAM user names to add to the readonly group | list | `<list>` | no |
| stage | Stage (e.g. `prod`, `dev`, `staging`) | string | - | yes |
| tags | Additional tags (e.g. map(`BusinessUnit`,`XYZ`) | map | `<map>` | no |

## Outputs

| Name | Description |
|------|-------------|
| group_admin_arn | Admin group ARN |
| group_admin_id | Group outputs |
| group_admin_name | Admin group name |
| group_readonly_arn | Readonly group ARN |
| group_readonly_id | Readonly group ID |
| group_readonly_name | Readonly group name |
| role_admin_arn | Role outputs |
| role_admin_name | Admin role name |
| role_readonly_arn | Readonly role ARN |
| role_readonly_name | Readonly role name |




## Related Projects

Check out these related projects.

- [terraform-aws-iam-system-user](https://github.com/cloudposse/terraform-aws-iam-system-user) - Terraform Module to Provision a Basic IAM System User Suitable for CI/CD Systems (E.g. TravisCI, CircleCI)
- [terraform-aws-iam-chamber-user](https://github.com/cloudposse/terraform-aws-iam-chamber-user) - Terraform module to provision a basic IAM chamber user with access to SSM parameters and KMS key to decrypt secrets, suitable for CI/CD systems (e.g. TravisCI, CircleCI, CodeFresh) or systems which are external to AWS that cannot leverage AWS IAM Instance Profiles
- [terraform-aws-ssm-iam-role](https://github.com/cloudposse/terraform-aws-ssm-iam-role) - Terraform module to provision an IAM role with configurable permissions to access SSM Parameter Store
- [terraform-aws-iam-s3-user](https://github.com/cloudposse/terraform-aws-iam-s3-user) - Terraform module to provision a basic IAM user with permissions to access S3 resources, e.g. to give the user read/write/delete access to the objects in an S3 bucket
- [terraform-aws-lb-s3-bucket](https://github.com/cloudposse/terraform-aws-lb-s3-bucket) - Terraform module to provision an S3 bucket with built in IAM policy to allow AWS Load Balancers to ship access logs
- [terraform-aws-organization-access-group](https://github.com/cloudposse/terraform-aws-organization-access-group) - Terraform module to create an IAM Group and Policy to grant permissions to delegated IAM users in the Organization's master account to access a member account



## Help

**Got a question?**

File a GitHub [issue](https://github.com/cloudposse/terraform-aws-iam-assumed-roles/issues), send us an [email][email] or join our [Slack Community][slack].

## Commercial Support

Work directly with our team of DevOps experts via email, slack, and video conferencing. 

We provide [*commercial support*][commercial_support] for all of our [Open Source][github] projects. As a *Dedicated Support* customer, you have access to our team of subject matter experts at a fraction of the cost of a full-time engineer. 

[![E-Mail](https://img.shields.io/badge/email-hello@cloudposse.com-blue.svg)](mailto:hello@cloudposse.com)

- **Questions.** We'll use a Shared Slack channel between your team and ours.
- **Troubleshooting.** We'll help you triage why things aren't working.
- **Code Reviews.** We'll review your Pull Requests and provide constructive feedback.
- **Bug Fixes.** We'll rapidly work to fix any bugs in our projects.
- **Build New Terraform Modules.** We'll develop original modules to provision infrastructure.
- **Cloud Architecture.** We'll assist with your cloud strategy and design.
- **Implementation.** We'll provide hands-on support to implement our reference architectures. 


## Community Forum

Get access to our [Open Source Community Forum][slack] on Slack. It's **FREE** to join for everyone! Our "SweetOps" community is where you get to talk with others who share a similar vision for how to rollout and manage infrastructure. This is the best place to talk shop, ask questions, solicit feedback, and work together as a community to build *sweet* infrastructure.

## Contributing

### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/cloudposse/terraform-aws-iam-assumed-roles/issues) to report any bugs or file feature requests.

### Developing

If you are interested in being a contributor and want to get involved in developing this project or [help out](https://github.com/orgs/cloudposse/projects/3) with our other projects, we would love to hear from you! Shoot us an [email](mailto:hello@cloudposse.com).

In general, PRs are welcome. We follow the typical "fork-and-pull" Git workflow.

 1. **Fork** the repo on GitHub
 2. **Clone** the project to your own machine
 3. **Commit** changes to your own branch
 4. **Push** your work back up to your fork
 5. Submit a **Pull Request** so that we can review your changes

**NOTE:** Be sure to merge the latest changes from "upstream" before making a pull request!


## Copyright

Copyright © 2017-2018 [Cloud Posse, LLC](https://cloudposse.com)



## License 

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) 

See [LICENSE](LICENSE) for full details.

    Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

      https://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
    KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.









## Trademarks

All other trademarks referenced herein are the property of their respective owners.

## About

This project is maintained and funded by [Cloud Posse, LLC][website]. Like it? Please let us know at <hello@cloudposse.com>

[![Cloud Posse](https://cloudposse.com/logo-300x69.svg)](https://cloudposse.com)

We're a [DevOps Professional Services][hire] company based in Los Angeles, CA. We love [Open Source Software](https://github.com/cloudposse/)!

We offer paid support on all of our projects.  

Check out [our other projects][github], [apply for a job][jobs], or [hire us][hire] to help with your cloud strategy and implementation.

  [docs]: https://docs.cloudposse.com/
  [website]: https://cloudposse.com/
  [github]: https://github.com/cloudposse/
  [commercial_support]: https://github.com/orgs/cloudposse/projects
  [jobs]: https://cloudposse.com/jobs/
  [hire]: https://cloudposse.com/contact/
  [slack]: https://slack.cloudposse.com/
  [linkedin]: https://www.linkedin.com/company/cloudposse
  [twitter]: https://twitter.com/cloudposse/
  [email]: mailto:hello@cloudposse.com


### Contributors

|  [![Erik Osterman][osterman_avatar]][osterman_homepage]<br/>[Erik Osterman][osterman_homepage] | [![Andriy Knysh][aknysh_avatar]][aknysh_homepage]<br/>[Andriy Knysh][aknysh_homepage] |
|---|---|

  [osterman_homepage]: https://github.com/osterman
  [osterman_avatar]: https://github.com/osterman.png?size=150
  [aknysh_homepage]: https://github.com/aknysh
  [aknysh_avatar]: https://github.com/aknysh.png?size=150


