# AWS Setup Workshop
	
29/01/2021
	
## Contacts
	
Joaquin Garralda --> orchestrator on business side
	
Andres Hernandez --> technical point of contact
	
Serhat Guelbetekin --> security specialist
	
## First steps
	
### need to set up governance (organizations)
	
Within master account
	
- Have a separate account --> create an organization (e.g: development, QA, staging, production, ...)
- workloads should be isolated
 
## Regions:

(Top right menu)

- can decide based on pricing
- can decide based on client constraints
- Usual choices
	- US: North Virginia or Oregon
	- EU: Ireland
	- there are options in CA too

Totally fine to have multiple region architectures.

## Organisation

Go to Accounts menu

- master account has a star
- can build different accounts here (e.g: development, QA, staging, production, ...)
- billing is shown separately per account
- can find more details of billing on EC2

Why have a separate security account?

- all logs are sent here
- only one person has access
- prevents hackers from covering their tracks

## User setup

### Users

- These give people the right to sign in
- Don't create individual IAM users per person
- These live in groups (e.g: departments)
- users should set up multi-factor authentification

### Access Keys

- stored on server
- need to be changed regularly
- every user has an access key
- avoid storing accss keys locally

### Single Sign On (SSO)

- this generates a new access key every time you want to access resources
- most secure way to give programatic access
- recommended unless you want to do really fancy stuff

### Groups

- these have credentials (rights to do stuff)
- typical groups are developers, admins, ...
- one user can belong to separate groups

### Account

- administrative thing to group resources
- expect admin account, root account, development account
- these set authorizations of each user
- one user or a full group can belong to separate accounts
- When building accounts
	- keep track of all CDR blocks
	- all CDR blocks should be different

### Request users set up multi-factor authentification

Configure this under "Users should ask for MFA"

## Cost

### Trusted Advisor

#### performance

- Gives details about resource usage
	- where calculations are run
	- if processors are idle
- gives tips related to how to reduce costs

#### security 

- security:
	- will show warnings if there are security issues (no MFA, no restrictions about pw, ...) 

#### Service limits

- will show if no backups are made
- will show if default limit of 20 servers is exceeded

### Cloud trail

- shows the history of whatever anyone did
- cannot be deleted
- if someone hacked in --> will appear here

## Other features

- can set up VPN
- VPC (Virtual private cloud)

## Take home

- Andres's job
	- can double check way system architecture
	- can help us with product decisions (e.g: K8s vs Beanstalk)
	- can setup workshop to understand e.g: Brackets, Beanstalk, ...
- Support center: can chat real time with support member
-  Service called secret manager: stores external API keys