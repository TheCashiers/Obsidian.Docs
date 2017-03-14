# Claims in Obsidian Management API
## Introduce
Obsidian uses Token-based Authentication and Claims-based Authorization.

If user wants to access a manament API action, a JsonWebToken must be added into the request.JsonWebToken generated by Obsidian OAuth Server contains claims that user owns. Some claims represent user's personal information, others represent permissions which user is endowed with. 

In this section, we mainly list all available claims that can be given to user.

For claims represented user's personal information, see [Claims in Obsidian OAuth Server](http://github.com)

>**Notice : Claim represents a theoretical permission. In fact, What a user can operate depends on authorization policies definitions in authorizationpolicy.json**

## Claims
|Type|ClaimType|ClaimValue|Enables|
|:-|:-|:-|:-|
|User| http://schema.za-pt.org/Obsidian/ManagementAPI/User |Add|Represents user can add a new user
|User| http://schema.za-pt.org/Obsidian/ManagementAPI/User |Get|Represents user can query any user's information
|User| http://schema.za-pt.org/Obsidian/ManagementAPI/User/UserName |Update|Represents user can modify other user's user name
|User| http://schema.za-pt.org/Obsidian/ManagementAPI/User/Password |Update|Represents user can modify other user's password
|User| http://schema.za-pt.org/Obsidian/ManagementAPI/User/Profile |Update|Represents user can modify other user's profile
|User| http://schema.za-pt.org/Obsidian/ManagementAPI/User/Claims |Update|Represents user can modify other user's claim
|Client| http://schema.za-pt.org/Obsidian/ManagementAPI/Client |Add|Represents user can add a new client
|Client| http://schema.za-pt.org/Obsidian/ManagementAPI/Client |Get|Represents user can query information of a client
|Client| http://schema.za-pt.org/Obsidian/ManagementAPI/Client |Update|Represents user can modify a client
|Client| http://schema.za-pt.org/Obsidian/ManagementAPI/Client/Secret |Get|Represents user can query secret of a client
|Client| http://schema.za-pt.org/Obsidian/ManagementAPI/Client/Secret |Update|Represents user can modify secret of a client
|Scope| http://schema.za-pt.org/Obsidian/ManagementAPI/Scope |Add|Represents user can add a new permission scope
|Scope| http://schema.za-pt.org/Obsidian/ManagementAPI/Scope |Get|Represents user can query information of a permission scope
|Scope| http://schema.za-pt.org/Obsidian/ManagementAPI/Scope |Update|Represents user can modify a scope