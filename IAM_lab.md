# IAM Lab

Signin link to console. Users can use this link to log in.

All IAM changes are at **Global level**.

**Root account** has complete admin access. Associated with personal email.
Use MFA for root account. Can use Google authenticator for codes.

## Creating groups

## Creating users

New users have **no permissions** when created.

New users are assigned a **Key ID and Secret Access Key** when created (equivalent to username/password for programmatic access).

New users can access console with name and password.

Add user to group. Apply policy to group e.g. Administrator access

A password policy is a set of rules that define the type of password an IAM user can set.

## Roles

A way for an AWS service to use another AWS service.

Roles are global.

Easier to manage.

## Policies

JSON. Effect, action, resource. To define what users, groups or roles can do/access.

Password policies can be setup for rotation and password rules.
