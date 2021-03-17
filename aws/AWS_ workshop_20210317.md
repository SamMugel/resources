# AWS workshop 17/03/2021

## Our questions

1. Is it best practise to assign permissions to groups (of users) or accounts?
1. Can I assign permissions to organizations (of accounts)?
1. How do we monitor costs / security?
1. What permissions are we giving each group?
1. is it correct to:
	1. assign administrator rights (e.g: IAM management) to roles (e.g: SysAdmin)
	1. assign dev permissions to accounts (e.g: Data scientist permissions to Workloads ML account)


## User permissions

User / IAM role / groups of policies holds policies which give them access to certain rights.

Account then limits user permissions through SCP (service control policy).

To do anything in aws, user must go through account.

## Video

[AWS video for permission granting](https://www.youtube.com/watch?v=bXrsUEI1V38&t=126s)

## AWS plans

### AWS support program

Can put us in touch with a 3rd party which can control / validate our architecture.

AWS can cover this up to 5K. Can't guarantee this will be under 5K.

Watch out: they'll try to build a lasting relationship with us --> make it clear we only want to validate our architecture & learn from them.

### AWS plans

AWS for business --> 24h support and insurrance.

Support engineer will have access to our account --> can help us more in depth than Andres.

## Account permissions

### Sandbox

SystemAdministrator

### All developers

Power user access

### Rod

Sys admin

### me

Full admin

### Questions

- full access? For now yes
- tags? Used for policies keyword search
- recommended groups? Any project has its own group
- permissions for developers? for now: EC2 and S3 Full Access