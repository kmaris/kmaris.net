---
title: CV for Kevin Maris
date: 2022-04-14T07:28:49-06:00
---

Software \& Infrastructure Developer in Boulder, CO

##### About

Looking for opportunities to automate-all-the-things, fix and enhance your slow
and fragile pipelines, and work on interesting problems. I have a diverse
development background and have worked several jobs spanning frontend web
development to site reliability engineering. Currently considering opportunities
in Boulder, CO or remote.

For a full, detailed CV please reach out at [hello@kmaris.net](mailto:hello@kmaris.net).

##### Education

B.S. Computer Science at [California State University - Sacramento](https://www.csus.edu), 2009

##### Skills

For coding I primarily work with Python but I read/tweak a number of others like
Go, Java, PHP, Javascript, and shell scripting. Proficient managing kubernetes
clusters in AWS and other services like EC2, RDS, etc. Deploying services with a
number of tools like atlantis, terraform, helm, ansible, argo cd.

## Recent Experience

### Site Reliability Engineer @ [Automox](https://www.automox.com) (Apr 2021 - Apr 2022)

Laid off (with 40+ others) after one year, but I feel like I got a lot done.
Some highlights include:

- Migrated testing infrastructure from on-prem to AWS and greatly improved
  parallel system test capabilities and work flows.
- Established using Packer, Terraform, and EC2 launch templates to provide
  consistently configured and reproducible test node environments.
- Assist developers integrate datadog metrics collection into their services to
  track app performance.

### Site Reliability Engineer @ [Chess.com](https://www.chess.com) (Nov 2020 - Apr 2021)

- Developed kubernetes infrastructure and development platform tooling to help
  migrate services from data centers into GCP.
- Performed lots of performance troubleshooting during chess.com's exponential
  growth during the pandemic.

### DevOps Engineer @ [NetApp/Solidfire](https://www.netapp.com/data-storage/solidfire/) (June 2019 - July 2020)

A one year contract that ended right at the start of COVID, I was primarily
a DevOps Engineer but had some SRE responsibilities as well. A typical day
could be anything from creating Jenkins pipelines, working on Python build
suite code, writing/executing ansible playbook configurations, managing VMWare
resources via Terraform, managing Kubernetes clusters with Ansible and
Terraform. While working here and seeing some of our frustrations it led me to
create and open source a [docker volume plugin][docker-volume-iso]
to mount ISO's into containers without the need for being root in the
container. I also managed our HA Artifactory cluster and helped devs with
access control, repo cleanup and maintenance, deploying to, etc.

### Web Operations Engineer @ [CU Laboratory for Atmospheric & Space Physics](https://lasp.colorado.edu/home/) (Jun 2018 - Mar 2019)

My work here was short due to unforeseen personal circumstances (aka house pipe
froze and flooded). During my time I wrote Ansible playbook configurations,
maintained and enhanced app and build infrastructure, and just generally helped
where I could with any questions from Docker to Jenkins to Linux, etc.

### DevOps Engineer @ [Vaisala](https://www.vaisala.com/en) (Sep 2017 - Jun 2018)

The timing to work at Vaisala, in some ways, couldn't have been better. The
company was vigorously migrating services to AWS and I got to help with much of
that transition. We (a team of primarily four) re-organized one large AWS
account into  multiple accounts with MFA for better security, billing, organization,
etc. We used Terraform, Ansible, Packer, Docker extensively to enhance
deployment speed for several services in the lightning detection network. Our
team also managed build system resources like Jenkins, Nexus, Sonar, etc as
well as trained developers on how to use these systems in their workflows.

### SCM Engineer @ [Gogoair Business Aviation](https://business.gogoair.com/) (Mar 2014 - Sep 2017)

At Gogo I was on a team that managed the build infrastructure and helped ensure
build reproducibility per FAA requirements. Along with that I also managed an
internal hardware test lab and fully automated test workstation deployment and
configuration utilizing a variety of technologies from PXE and remastered
Ubuntu images to Ansible pull configurations and deployments. Along with
being a systems administrator all of the CI linux-based hosts we also
maintained alerting services for the org based around Nagios.

## Open Source Contributions

- [docker-volume-iso](https://github.com/kmaris/docker-volume-iso) - A docker
  volume plugin to mount ISO’s as docker volumes.
- [Jenkins EC2 Plugin](https://github.com/jenkinsci/ec2-plugin/pull/262) - Submitted
  a documentation patch to specify proper security group delimiters.
- [Ansible](https://github.com/ansible/ansible-modules-extras/pull/3123) - Contributed
  a bug-fix to ensure the git-config module honors include directives.
- [wtf](https://gitlab.com/kmaris/wtf) - A terraform wrapper script to manage a
  profile and extend the life of MFA tokens during development.
- [futz](https://gitlab.com/kmaris/futz) - An experimental static website generator
  and proof of concept written in python using GNUmake for tracking content tree
  dependencies.

See more Github PR's here:
https://github.com/pulls?q=is%3Apr+author%3Akmaris+is%3Aclosed+

#### ... and more!

I have been active since 2009, and prior to Gogo I was a full
stack developer for [Lightstanza](https://lightstanza.com/),
[NOAA's Science on a Sphere](https://sos.noaa.gov/), and the
[California Department of Transportation](https://dot.ca.gov).

[Get in touch](mailto:hello@kmaris.net) to see my full CV...

