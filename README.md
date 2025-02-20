
<!-- markdownlint-disable -->
# terraform-provider-awsutils [![Latest Release](https://img.shields.io/github/release/cloudposse/terraform-provider-awsutils.svg)](https://github.com/cloudposse/terraform-provider-awsutils/releases/latest) [![Slack Community](https://slack.cloudposse.com/badge.svg)](https://slack.cloudposse.com) [![Discourse Forum](https://img.shields.io/discourse/https/ask.sweetops.com/posts.svg)](https://ask.sweetops.com/)
<!-- markdownlint-restore -->

[![README Header][readme_header_img]][readme_header_link]

[![Cloud Posse][logo]](https://cpco.io/homepage)

<!--




  ** DO NOT EDIT THIS FILE
  **
  ** This file was automatically generated by the `build-harness`.
  ** 1) Make all changes to `README.yaml`
  ** 2) Run `make init` (you only need to do this once)
  ** 3) Run`make readme` to rebuild this file.
  **
  ** (We maintain HUNDREDS of open source projects. This is how we maintain our sanity.)
  **





-->

Terraform provider for performing various tasks that cannot be performed with the official 
[AWS Terraform Provider](https://github.com/hashicorp/terraform-provider-aws) from Hashicorp.  

This provider is derived in large parts from the official HashiCorp AWS provider. We copied all the boilerplate 
functionality so that it follows the `terraform-provider-aws` conventions, but then removed all the standard 
resources and added in our own. This module is intended to be used as an escape hatch to accomplish all the hard 
things that will never be supported by the official provider due to strong (and valid) opinions of how providers 
should manage the lifecycle of a resource. Unfortunately, in the real-world we have to make tradeoffs to get stuff 
done. That's this provider in a nutshell.

---

This project is part of our comprehensive ["SweetOps"](https://cpco.io/sweetops) approach towards DevOps.
[<img align="right" title="Share via Email" src="https://docs.cloudposse.com/images/ionicons/ios-email-outline-2.0.1-16x16-999999.svg"/>][share_email]
[<img align="right" title="Share on Google+" src="https://docs.cloudposse.com/images/ionicons/social-googleplus-outline-2.0.1-16x16-999999.svg" />][share_googleplus]
[<img align="right" title="Share on Facebook" src="https://docs.cloudposse.com/images/ionicons/social-facebook-outline-2.0.1-16x16-999999.svg" />][share_facebook]
[<img align="right" title="Share on Reddit" src="https://docs.cloudposse.com/images/ionicons/social-reddit-outline-2.0.1-16x16-999999.svg" />][share_reddit]
[<img align="right" title="Share on LinkedIn" src="https://docs.cloudposse.com/images/ionicons/social-linkedin-outline-2.0.1-16x16-999999.svg" />][share_linkedin]
[<img align="right" title="Share on Twitter" src="https://docs.cloudposse.com/images/ionicons/social-twitter-outline-2.0.1-16x16-999999.svg" />][share_twitter]



















## Usage



Here is how to use this provider in your own Terraform code:

```hcl
terraform {
  required_providers {
    awsutils = {
      source = "cloudposse/awsutils"
      version = ">= 0.1.0"
    }
  }
}

provdier "awsutils" {
  region = "us-east-2"
}
```
See the [Docs](./docs) for additional information.




## Examples

Here is an example of using this provider:

```hcl
terraform {
  required_providers {
    awsutils = {
      source = "cloudposse/awsutils"
    }
  }
}
```

Here are some additional examples:

- [`examples/resources/awsutils_default_vpc_deletion`](/examples/resources/awsutils_default_vpc_deletion/)



## Developing the Provider

If you wish to work on the provider, you'll first need [Go](http://www.golang.org) installed on your machine (see [Requirements](#requirements) above).

To compile the provider, run `go install`. This will build the provider and put the provider binary in the `$GOPATH/bin` directory.

To generate or update documentation, run `go generate`.

In order to run the full suite of Acceptance tests, run `make testacc`.

_Note:_ Acceptance tests create real resources, and often cost money to run.

```sh
$ make testacc
```

### Testing Locally

You can test the provider locally by using the [provider_installation](https://www.terraform.io/docs/cli/config/config-file.html#provider-installation) functionality.

For testing this provider, you can edit your `~/.terraformrc` file with the following:

```hcl
provider_installation {
  dev_overrides  {
    "cloudposse/awsutils" = "/path/to/your/code/github.com/cloudposse/terraform-provider-awsutils/"
  }

  # For all other providers, install them directly from their origin provider
  # registries as normal. If you omit this, Terraform will _only_ use
  # the dev_overrides block, and so no other providers will be available.
  direct {}
}
```

With that in place, you can build the provider (see above) and add a provider block:

```hcl
required_providers {
    awsutils = {
      source = "cloudposse/awsutils"
    }
  }
```

Then run `terraform init`, `terraform plan` and `terraform apply` as normal.

```sh
$ terraform init
Initializing the backend...

Initializing provider plugins...
- Finding latest version of cloudposse/awsutils...

Warning: Provider development overrides are in effect

The following provider development overrides are set in the CLI configuration:
 - cloudposse/awsutils in /path/to/your/code/github.com/cloudposse/terraform-provider-awsutils

The behavior may therefore not match any released version of the provider and
applying changes may cause the state to become incompatible with published
releases.
```

```sh
terraform apply

Warning: Provider development overrides are in effect

The following provider development overrides are set in the CLI configuration:
 - cloudposse/awsutils in /Users/matt/code/src/github.com/cloudposse/terraform-provider-awsutils

The behavior may therefore not match any released version of the provider and
applying changes may cause the state to become incompatible with published
releases.


An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:

Terraform will perform the following actions:

Plan: 1 to add, 0 to change, 0 to destroy.
```



## Share the Love

Like this project? Please give it a ★ on [our GitHub](https://github.com/cloudposse/terraform-provider-awsutils)! (it helps us **a lot**)

Are you using this project or any of our other projects? Consider [leaving a testimonial][testimonial]. =)



## Related Projects

Check out these related projects.

- [Cloud Posse Terraform Utils Provider](https://github.com/cloudposse/terraform-provider-awsutils) - Terraform provider for various utilities (deep merging, stack configuration management), and to add additional 
missing functionality to Terraform


## References

For additional context, refer to some of these links.

- [Terraform Plugins](https://www.terraform.io/docs/extend/plugin-types.html#providers) - Terraform is logically split into two main parts: Terraform Core and Terraform Plugins. Each plugin exposes an implementation for a specific service, such as the AWS provider or the cloud-init provider.


## Help

**Got a question?** We got answers.

File a GitHub [issue](https://github.com/cloudposse/terraform-provider-awsutils/issues), send us an [email][email] or join our [Slack Community][slack].

[![README Commercial Support][readme_commercial_support_img]][readme_commercial_support_link]

## DevOps Accelerator for Startups


We are a [**DevOps Accelerator**][commercial_support]. We'll help you build your cloud infrastructure from the ground up so you can own it. Then we'll show you how to operate it and stick around for as long as you need us.

[![Learn More](https://img.shields.io/badge/learn%20more-success.svg?style=for-the-badge)][commercial_support]

Work directly with our team of DevOps experts via email, slack, and video conferencing.

We deliver 10x the value for a fraction of the cost of a full-time engineer. Our track record is not even funny. If you want things done right and you need it done FAST, then we're your best bet.

- **Reference Architecture.** You'll get everything you need from the ground up built using 100% infrastructure as code.
- **Release Engineering.** You'll have end-to-end CI/CD with unlimited staging environments.
- **Site Reliability Engineering.** You'll have total visibility into your apps and microservices.
- **Security Baseline.** You'll have built-in governance with accountability and audit logs for all changes.
- **GitOps.** You'll be able to operate your infrastructure via Pull Requests.
- **Training.** You'll receive hands-on training so your team can operate what we build.
- **Questions.** You'll have a direct line of communication between our teams via a Shared Slack channel.
- **Troubleshooting.** You'll get help to triage when things aren't working.
- **Code Reviews.** You'll receive constructive feedback on Pull Requests.
- **Bug Fixes.** We'll rapidly work with you to fix any bugs in our projects.

## Slack Community

Join our [Open Source Community][slack] on Slack. It's **FREE** for everyone! Our "SweetOps" community is where you get to talk with others who share a similar vision for how to rollout and manage infrastructure. This is the best place to talk shop, ask questions, solicit feedback, and work together as a community to build totally *sweet* infrastructure.

## Discourse Forums

Participate in our [Discourse Forums][discourse]. Here you'll find answers to commonly asked questions. Most questions will be related to the enormous number of projects we support on our GitHub. Come here to collaborate on answers, find solutions, and get ideas about the products and services we value. It only takes a minute to get started! Just sign in with SSO using your GitHub account.

## Newsletter

Sign up for [our newsletter][newsletter] that covers everything on our technology radar.  Receive updates on what we're up to on GitHub as well as awesome new projects we discover.

## Office Hours

[Join us every Wednesday via Zoom][office_hours] for our weekly "Lunch & Learn" sessions. It's **FREE** for everyone!

[![zoom](https://img.cloudposse.com/fit-in/200x200/https://cloudposse.com/wp-content/uploads/2019/08/Powered-by-Zoom.png")][office_hours]

## Contributing

### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/cloudposse/terraform-provider-awsutils/issues) to report any bugs or file feature requests.

### Developing

If you are interested in being a contributor and want to get involved in developing this project or [help out](https://cpco.io/help-out) with our other projects, we would love to hear from you! Shoot us an [email][email].

In general, PRs are welcome. We follow the typical "fork-and-pull" Git workflow.

 1. **Fork** the repo on GitHub
 2. **Clone** the project to your own machine
 3. **Commit** changes to your own branch
 4. **Push** your work back up to your fork
 5. Submit a **Pull Request** so that we can review your changes

**NOTE:** Be sure to merge the latest changes from "upstream" before making a pull request!



## Copyrights

Copyright © 2021-2022 [Cloud Posse, LLC](https://cloudposse.com)













## Trademarks

All other trademarks referenced herein are the property of their respective owners.

## About

This project is maintained and funded by [Cloud Posse, LLC][website]. Like it? Please let us know by [leaving a testimonial][testimonial]!

[![Cloud Posse][logo]][website]

We're a [DevOps Professional Services][hire] company based in Los Angeles, CA. We ❤️  [Open Source Software][we_love_open_source].

We offer [paid support][commercial_support] on all of our projects.

Check out [our other projects][github], [follow us on twitter][twitter], [apply for a job][jobs], or [hire us][hire] to help with your cloud strategy and implementation.



### Contributors

<!-- markdownlint-disable -->
|  [![Matt Calhoun][mcalhoun_avatar]][mcalhoun_homepage]<br/>[Matt Calhoun][mcalhoun_homepage] | [![RB][nitrocode_avatar]][nitrocode_homepage]<br/>[RB][nitrocode_homepage] |
|---|---|
<!-- markdownlint-restore -->

  [mcalhoun_homepage]: https://github.com/mcalhoun
  [mcalhoun_avatar]: https://img.cloudposse.com/150x150/https://github.com/mcalhoun.png
  [nitrocode_homepage]: https://github.com/nitrocode
  [nitrocode_avatar]: https://img.cloudposse.com/150x150/https://github.com/nitrocode.png

[![README Footer][readme_footer_img]][readme_footer_link]
[![Beacon][beacon]][website]

  [logo]: https://cloudposse.com/logo-300x69.svg
  [docs]: https://cpco.io/docs?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=docs
  [website]: https://cpco.io/homepage?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=website
  [github]: https://cpco.io/github?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=github
  [jobs]: https://cpco.io/jobs?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=jobs
  [hire]: https://cpco.io/hire?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=hire
  [slack]: https://cpco.io/slack?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=slack
  [linkedin]: https://cpco.io/linkedin?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=linkedin
  [twitter]: https://cpco.io/twitter?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=twitter
  [testimonial]: https://cpco.io/leave-testimonial?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=testimonial
  [office_hours]: https://cloudposse.com/office-hours?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=office_hours
  [newsletter]: https://cpco.io/newsletter?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=newsletter
  [discourse]: https://ask.sweetops.com/?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=discourse
  [email]: https://cpco.io/email?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=email
  [commercial_support]: https://cpco.io/commercial-support?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=commercial_support
  [we_love_open_source]: https://cpco.io/we-love-open-source?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=we_love_open_source
  [terraform_modules]: https://cpco.io/terraform-modules?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=terraform_modules
  [readme_header_img]: https://cloudposse.com/readme/header/img
  [readme_header_link]: https://cloudposse.com/readme/header/link?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=readme_header_link
  [readme_footer_img]: https://cloudposse.com/readme/footer/img
  [readme_footer_link]: https://cloudposse.com/readme/footer/link?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=readme_footer_link
  [readme_commercial_support_img]: https://cloudposse.com/readme/commercial-support/img
  [readme_commercial_support_link]: https://cloudposse.com/readme/commercial-support/link?utm_source=github&utm_medium=readme&utm_campaign=cloudposse/terraform-provider-awsutils&utm_content=readme_commercial_support_link
  [share_twitter]: https://twitter.com/intent/tweet/?text=terraform-provider-awsutils&url=https://github.com/cloudposse/terraform-provider-awsutils
  [share_linkedin]: https://www.linkedin.com/shareArticle?mini=true&title=terraform-provider-awsutils&url=https://github.com/cloudposse/terraform-provider-awsutils
  [share_reddit]: https://reddit.com/submit/?url=https://github.com/cloudposse/terraform-provider-awsutils
  [share_facebook]: https://facebook.com/sharer/sharer.php?u=https://github.com/cloudposse/terraform-provider-awsutils
  [share_googleplus]: https://plus.google.com/share?url=https://github.com/cloudposse/terraform-provider-awsutils
  [share_email]: mailto:?subject=terraform-provider-awsutils&body=https://github.com/cloudposse/terraform-provider-awsutils
  [beacon]: https://ga-beacon.cloudposse.com/UA-76589703-4/cloudposse/terraform-provider-awsutils?pixel&cs=github&cm=readme&an=terraform-provider-awsutils
