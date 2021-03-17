# AWS workshop -- security

03/03/2021

## Ideally: 3 different people (roles within the company)

_Role_: thing with different priviledges (policies). Roles live in organisations (same as accounts).	

### CTO

- does not have full power
- only root user is all powerfull --> should be destroyed
- appoint CISO

### CISO (Chief information security officer)

- put in place all mechanisms which ensure people cannot delete trails
- responsible for security and cyber risk
- define what every member of the organization can do
- controls which policies go with which account & which person can do what in which account

### Sys admin

Can do most of the job, but does not have access to locks, and can't access security accounts which monitor processes

## When login in to AWS

- specify account and user
- any physical person has one account and one user (at any one time), these are specified at login

## Link people to AWS

### Users

- Should have one user for each person
- register employees in corporate directory
- this for us is AWS SSO
- entering a person into SSO creates a user for them

### Roles
- each person has a job title --> this is the _role_
- roles are, e.g: admins and developers listed in SSO
- SSO is the service which links
	- physical people (users) to roles
	- attaches accounts to roles
- controls what a person can do within an account

### recommended role structure

- no definite answer
- every time we create a job --> need to create a role
- roles are created to give applications the right to interact with other applications
- everyone should have the right to build some roles

## Steps

1. Setup SSO
	2. setup physical people (build AIM users)
	3. map them to accounts
	4. role allows them to do stuff in the account

## Users -- best to have one admin user?

## How do I link a user to an account?

## How do I set up SSO?

## How do I enforce mandatory MFA?

# Next steps

1. Link users to accounts
2. Add permissions to accounts
3. Generate roles