---
title: Maintain data security after an employee leaves
description: To prevent data leaks, revoke a user’s access to your organization’s data when they leave.
published: true
date: 2021-12-01T18:51:37.039Z
tags: bronze, bronze-controls
editor: markdown
dateCreated: 2021-12-01T18:51:37.038Z
---

# Header
As your organization's administrator,  keep your organization's data safe and secure when an user leaves by completing the following best practices:

1. - Wipe any mobile devices
-- Use the Admin console to remotely remove data from the user's device. You can remote wipe the entire device or only erase your organization's data.

1. - Revoke password recovery access 
-- Remove the user's recovery email address and phone number so they can't use the password recovery feature to access their old account.
1. - Change the user's password
-- This can greatly reduce the risk of unauthorized access to their old account. 

1. - Revoke all OAuth 2.0 application tokens
-- Changing a user's password also revokes OAuth 2.0 tokens issued for accessing certain products. Review all authorized access and revoke any other authorized applications. 

1. - Reset the user's sign-in cookies
-- This also reduces the risk of unauthorized access.

1. - Revoke security keys and app password access
-- Revoke any security keys or application-specific passwords that have been granted access to the user's account.

1. - Delete the user's account 
-- Move any of the user's data that you want to save to another account. Then delete their original account completely. This is the best way to ensure they can't access your organization's data.