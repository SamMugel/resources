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

## More questions

#### What is a recommended user group structure? For the moment I have one group per project

Since you are setting different accounts for each project, the leaner way could be creating the groups based on job description of the people in the group. Remember you can have 1 person belonging to multiple groups, that’s not a problem. For example you could have a group for developers, but that doesn’t prevent you from having another group for developers that will work on the optimization project only. When you develop a bit more experience, you can instead leverage attributes-based access control, which is a more efficient way on the long-term, but introduces extra complexity to set it up, as you need to define the policies to automate.

#### What is the recommended way of giving Rodrigo SysAdmin permissions (and myself Full Admin permissions)? Should this go through a dedicated account?

With AWS SSO, when you grant a specific user the access to one account, or multiple accounts, you need to select a permission set for that specific combination of user(s) / account(s). That means for you and Rodrigo to have FullAdmin and SysAdmin permission in all accounts, all you need to do is granting yourself access to all accounts selecting FullAdmin permission set in AWS SSO, and doing the same for Rodrigo, but for him, you would select the SysAdmin permission set instead. To iterate on yesterday’s message, with SSO, you decide who access which account(s), but not only this, you can have a single person holding a different permission set for each account if you wanted to. Example: Rodrigo can have SysAdmin permissions for his sandbox account, but DeveloperPowerUser in the Optimization project account. By the way, here is a document that might help you decide which managed policy to apply to your team members based on their job function.

#### need to configure boto3 with access key and secret access key --> how to get this information?

Hopefully you have logged in with AWS SSO (per our discussions), you can find access key / secret access key in the AWS SSO Sign-in page (there are 2 links one for management console, and another for programmatic access, if you click there, you will find temporary credentials). For more details, see this [instructions](https://aws.amazon.com/blogs/security/aws-single-sign-on-now-enables-command-line-interface-access-for-aws-accounts-using-corporate-credentials/) .


#### need global s3 bucket (accessible to all users) --> how do we do this?

See [this document](https://docs.aws.amazon.com/AmazonS3/latest/userguide/example-walkthroughs-managing-access-example1.html) which shows how to leverage identity based policies and resource based policies for S3 permissions granting. Also take a look here, to understand what polices can be assigned to users directly in [AWS SSO](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-overview.html#accesscontrolmanagingaccess),


#### need to give credentials to an application to initiate processes. In this case: authorising a local process to create / read / write s3 buckets --> what object (user, role, account, ...) does the app get its permissions from?

You do this by creating a role with a policy to allow s3 operations, then assign that role to the instance where the application is running, the application will inherit permissions from the instance where its hosted see [here](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html).