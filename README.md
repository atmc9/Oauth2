# OAuth2

* **Why do we need OAuth2 standard, why cannot we share username and password with 3rd party applications?**
  
   In the traditional client-server authentication model, the client requests an access-restricted resource (protected resource) on the
   server by authenticating with the server using the resource owner's credentials.  In order to provide third-party applications access    to restricted resources, the resource owner shares its credentials with the third party. This creates several problems and    limitations:

   o Third-party applications are required to store the resource owner's credentials for future use, typically a password in clear-text.

   o Servers are required to support password authentication, despite the security weaknesses inherent in passwords.

   o Third-party applications gain overly broad access to the resource owner's protected resources, leaving resource owners without any
     ability to restrict duration or access to a limited subset of resources.

   o Resource owners cannot revoke access to an individual third party without revoking access to all third parties, and must do so by
     changing the third party's password.
      
   o Compromise of any third-party application results in compromise of the end-user's password and all of the data protected by that password.
   
* **How does OAuth helps?**

   OAuth addresses these issues by introducing an authorization layer and separating the role of the client from that of the resource
   owner.  In OAuth, the client requests access to resources controlled by the resource owner and hosted by the resource server, and is
   issued a different set of credentials than those of the resource owner.
   
   Instead of using the resource owner's credentials to access protected resources, the client obtains an access token -- a string denoting a
   specific scope, lifetime, and other access attributes. Access tokens are issued to third-party clients by an authorization server with the
   approval of the resource owner. The client uses the access token to access the protected resources hosted by the resource server.
   
 * **Example Scenario where OAuth can be helpful?**
 
   An end-user (resource owner) can grant a printing service (client) access to her protected photos stored at a photo-
   sharing service (resource server), without sharing her username and password with the printing service.  Instead, she authenticates
   directly with a server trusted by the photo-sharing service (authorization server), which issues the printing service delegation-
   specific credentials (access token).
   
 * **Roles in OAuth proccess**

   OAuth defines four roles:

   **resource owner**
      An entity capable of granting access to a protected resource. When the resource owner is a person, it is referred to as an
      end-user.

   **resource server**
      The server hosting the protected resources, capable of accepting and responding to protected resource requests using access tokens.

   **client**
      An application making protected resource requests on behalf of the resource owner and with its authorization.  The term "client" does not imply any particular implementation characteristics (e.g.,whether the application executes on a server, a desktop, or other devices).

   **authorization server**
      The server issuing access tokens to the client after successfully authenticating the resource owner and obtaining authorization. The authorization server may be the same server as the resource server or a separate entity. A single authorization server may issue access tokens accepted by multiple resource servers.
  
* **OAuth protocol flow**

![OAuth abstract flow](http://i.imgur.com/4eAzc9U.png "Oauth Abstract flow")

 The abstract OAuth 2.0 flow describes the interaction between the four roles and includes the following steps: 
  (A) The client requests authorization from the resource owner. The authorization request can be made directly to the resource owner (as shown), or preferably indirectly via the authorization server as an intermediary. 
  (B) The client receives an authorization grant, which is a credential representing the resource owner's authorization, expressed using one of four grant types defined in this specification or using an extension grant type. The authorization grant type depends on the method used by the client to request authorization and the types supported by the authorization server. 
  (C) The client requests an access token by authenticating with the authorization server and presenting the authorization grant. 
  (D) The authorization server authenticates the client and validates the authorization grant, and if valid, issues an access token. 
  (E) The client requests the protected resource from the resource server and authenticates by presenting the access token. 
(F) The resource server validates the access token, and if valid, serves the request.



