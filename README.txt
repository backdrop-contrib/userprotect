$Id$

****************************************************
User Protect Module -- README

written by Chad Phillips: thehunmonkgroup at yahoo dot com
****************************************************

This module provides various editing protection for users.  The protections can
be specific to a user, or applied to all users in a role. The following protections
are supported:

  username
  e-mail address
  password
  status changes
  roles
  deletion
  all edits (any accessed via user/X/edit)

When a protection is enabled for a specified user or an entire role, it takes effect
for all editing operations that any user might try to perform on the user in question
(exceptions listed below).   The the module will protect fields by disabling them at user/X/edit.

These protections are valid both when trying to edit the user directly from their
user/X/edit page, or using the mass user editing operations at admin/user/user.

The module also provides protection at the paths user/X/edit and user/X/delete,
should anyone try to visit those paths directly.


SETTINGS:

At administer -> user management -> userprotect settings, you'll find the general
settings for the module.  Most of it should be pretty self-explanatory.

In particular, note the available bypass settings--both the root user (uid 1) and
users with the 'administer users' permission can be allowed to bypass the
configured protections.


ADDING PROTECTIONS FOR ROLES:

This is done at administer -> user management -> userprotect settings.  Be
cautious about adding protections by role, or you can lock out users from things
unintentionally!

In particular, note the if you enable role protections for a specific role, and you have
no bypasses enabled, you've effectively locked out any role editing for that role by
anybody, unless you come back to the settings page and disable the role
protection!


ADDING PROTECTIONS FOR A SINGLE USER:

This is done at administer -> user management -> protected users.  Any time
a user is added for protection, they will initially receive the default protections
enabled in the settings area.


HOW THE MODULE DETERMINES A PROTECTION:

First it checks if the current user is allowed to bypass all protections.  If so, then
it stops there.  If not, it first examines all the roles of the user in question for role
protections, then examines the individual user's protections.  If a protection exists
in any of the user's roles or for the user themselves, then the protection is active
for that user.