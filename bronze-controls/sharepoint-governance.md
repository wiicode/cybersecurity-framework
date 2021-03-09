---
title: Example: SharePoint and OneDrive Governance
description: Using SharePoint for storing critical business info. 
published: true
date: 2021-03-09T02:28:58.713Z
tags: governance, policy, bronze, bronze-controls
editor: markdown
dateCreated: 2020-11-25T02:53:46.802Z
---

# About
Your company has elected to use OneDrive & SharePoint to store company data, great!  The hard part is establishing policies and procedures and we have you covered.  This guide is directly linked from BCSF v1.0 (Bento Cyber Security Framework 1.0) and details our model for using SharePoint in Small Business.  Governance over your data is necessary and making assumptions or failing to develop understanding of how these systems work will leave you vulnerable.  In BCSF we condensed the SharePoint operating requirements to a simple model that works. 

# Briefing
1. Scope.
Yes. Save your files to your OneDrive. Anything work-related should be stored in OneDrive moving forward to help us preserve data.
1. Install OneDrive	
Go to https://portal.office.com and login. Click OneDrive. Install the software on your device. 
1. Visit this page to brief yourself about OneDrive	https://support.office.com/en-us/article/what-is-onedrive-for-business-187f90af-056f-47c0-9656-cc0ddca7fdc2
1. Watch the OneDrive OnDemand Info	Learn about OnDemand as it it will help you save space. It's available in Windows 10 and also becoming available with macOS through a very recent software update.
1. Move personal folders.	All of your files should be moved to your OneDrive. This will vary on Windows, macOS, and remote systems. 
1. Find the folders you care about.	
1. Sync them when it's time.	Visit the Team Site and sync.
1. Read the rest of this document eventually.	In the end, you'll need be familiar with all of this.

# OneDrive Business Personal

## What are they?	
OneDrive Business, Personal Folders, are your data. Company data should be stored in those folders at all times. The primary function of this folder is to act as a cloud copy of your work files. They work similarly to the non-shared AeroFS folders but are stored in a location that is mutually exclusive of the shared Team Folders.

## How will they be migrated?	
Personal folders must be migrated manually by you - the end user. After all, they are your personal files. Although the company can acquire access to these folders, they are private and we make no efforts to do so under normal circumstances.

After installing and configuring your OneDrive application, the recommendation is that you move your personal folders to your "OneDrive - <COMPANY>" folder. Copying can result in disk exhaustion or induce confusion.

## What can I expect?	
After you move your personal folders it may take a while for OneDrive to catchup. 

## What do I need to know about sharing?	
You can share files from your OneDrive Business, Personal Folders, with team members. We locked down sharing to prevent external sharing as a security measure, thus you cannot send files to people outside. For that, we offer a special site described further down in this article. In practice, however, strongly advise against sharing personal folders and leveraging Team Sites as much as possible. The use of personal sharing can become confusing and difficult to manage.

  
# SharePoint Site Permissions

## Members / Group Members	
This is an effectively useless permission set. It controls communications from the SharePoint site into a distribution group that is Exchange Online only.

## Site Permissions	
This is what we rely on. It is accessed from Cog > Site Permissions and allows us to add people to a Group (see above) and also control permissions. In addition to individuals we have these main groups: team-<something>

## Library Permissions	
Although they come below Site Permissions and above Folder Permissions. These are effectively useless. They can only be set from the Team Site and can be difficult to discern and organize. As a general rule we let Library Permissions = Site Permissions, and then use Sharing/GrantAccess on folders for the rest.

## Folder Permissions	
Folder permissions are managed via the Share function. There are two settings to be aware of. The first is who has access in general, and this can default to everyone. From there, you can select a reduced scope and in cases of Specific People assign individuals.
 
Share vs. Grant Access	Grant/Manage Access is an extension of Sharing and Site Permissions. It is weirdly difficult to find.

##   Naming Convention

Please use "~" in front of a folder that you will change permissions on. For example, in Sales and Marketing "~Contract Samples" is a folder that has different permissions from the rest of the library.
  
## Keeping Sanity.	
We will manage sanity through three approaches:

- Mindful configuration
- Thoughtful policies (documented below) on how to use OneDrive
- Site Permission Check.  
  
  
# SharePoint Site Governance
  
## Sub-site creation	
> Not permitted.
{.is-danger}

Sub-sites are presently discouraged because new sub-sites can be a great benefit to the group, but unrestricted site creation can get out of hand. When sub-sites proliferate freely, problems can arise. For example:

It’s hard for users to find the right sub-site, or be sure if they have.

Information can be duplicated in several sub-sites, using up expensive storage space, and requiring duplicated effort to maintain.

Out-of-date information can reside on sub-sites, potentially for years, showing up in search results. It can be hard to tell what version of information is correct.

Managing permissions for a multitude of sub-sites can become a major chore, and users might inadvertently wind up with access to information they really shouldn’t have.

As employees leave the group, the sub-sites they create may be abandoned, creating confusion and muddying search results for remaining site users.

More at https://support.office.com/en-us/article/create-a-team-site-in-sharepoint-online-ef10c1e7-15f3-42a3-98aa-b5972711777d

## Permission Management	
> Variable & Flexible.
{.is-info}


Each business owner, aka Site Owner, has the ability to grant Site Permissions to their Team Site. They can do this by

Accessing Site Permissions and adding a member.
- Delegating the request to IT.
- Users can request access from Site Owners.

Site Owners can also configure Folder Sharing by disabling inheritance on a folder and setting their own permissions. This is acceptable but should be used with extreme caution.

Site Owners should not remove any groups or users from Site Permissions without clearing with IT, as original security settings were set with intent.

## Information Architecture	
> Simple Rules.
> {.is-success}

We primarily store data in Document Libraries. The data is files/folders. Key things to know are that:

- We do not require check-in/check-out. This leaves room for conflicts. See https://support.office.com/en-us/article/set-up-a-library-to-require-check-out-of-files-0c73792b-f727-4e19-a1f9-3173899e695b.
- We configure Version History for the last 50 revisions. https://support.office.com/en-us/article/how-does-versioning-work-in-a-sharepoint-list-or-library-0f6cd105-974f-44a4-aadb-43ac5bdfd247
  
## Site Landing Page	
> Configured.
{.is-success}

Each site landing page will contain a Purpose statement defining the general usage of the site and what permissions are likely to be in effect.
  