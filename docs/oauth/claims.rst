Claims in Obsidian OAuth Server
=================================

Claims in OAuth Server
-------------------------

Though Obsidian is mainly designed as an OAuth Authentication Server, the whole Obsidian program is commonly divided into three parts. On one hand, Obsidian's user model contains user's personal information which will be provided to third-part client on OAuth process, on the other hand, because it contains user's information, it can be regarded as a Resource Server.

Claims in user domain model mainly represent user's personal information instead of what a user can do.

Claims list
-----------

+------------+--------------------------------------------------------------------------------+--------------------------------+
|Model       |ClaimType                                                                       |Content                         |        
+============+================================================================================+================================+
|User        |http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier            |User Id of user model           |
+------------+--------------------------------------------------------------------------------+--------------------------------+
|User        |http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name                      |Username of user model          |
+------------+--------------------------------------------------------------------------------+--------------------------------+
|UserProfile |http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname                 |User's givenname                |
+------------+--------------------------------------------------------------------------------+--------------------------------+
|UserProfile |http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname                   |User's surname                  |
+------------+--------------------------------------------------------------------------------+--------------------------------+
|UserProfile |http://schemas.xmlsoap.org/ws/2005/05/identity/claims/gender                    |User's gender                   |
+------------+--------------------------------------------------------------------------------+--------------------------------+
|UserProfile |http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress              |User's email emailaddress       |
+------------+--------------------------------------------------------------------------------+--------------------------------+