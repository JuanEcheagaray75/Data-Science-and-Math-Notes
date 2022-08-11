# AAA Security

- [AAA Security](#aaa-security)
  - [Authentication](#authentication)
    - [Authentication models](#authentication-models)
    - [Authentication factors](#authentication-factors)
    - [Common scenarios](#common-scenarios)
    - [Authentication techniques](#authentication-techniques)
  - [Authorization](#authorization)
    - [Authorization techniques](#authorization-techniques)
    - [Secure Assertion Markup Language (SAML)](#secure-assertion-markup-language-saml)
    - [OAuth2.0](#oauth20)
  - [Accountability](#accountability)

> Framework used to control and track access within a computer network

- Authentication attempts to impede the usurpation of identity or that someone foreign to the system gets access to the system.
- Authorization attempts to impede the misuse of resources, either abuse or waste
- Accountability makes reference to monitoring and permitting the audit of the activities that each user performs, either a legitimate user or an intruder.

In particular the AAA framework attempts to:

- Control accesses
- Know each activity performed, independent of its nature
- Determine who performs each activity
- Verify that every use is correct and authorized, to avoid resource wasting or misuse
- Perform auditing of each activity
- Prevent attacks, information leaks and frauds

## Authentication

> The process of taking an identity and using some form of verification, the identity can be verified as being legitimate

The authentication process consists of 2 steps:

- Element A must have/generate some form of evidence that proves its identity (the client has credentials or proofs that its authentic)
- Element B must verify said evidence

### Authentication models

- Mutual authentication: the participants, user and server authenticate both ways
- Two-party: 2 elements participate in the authentication process, user and server without intermediaries
- Three-party: an element called Network Access Server acts as intermediary between 2 parties that want to communicate. User (supplicant) and server

### Authentication factors

- Knowledge factors: require the user to provide some data or information before they can access a secured system (passwords, concrete answers)
  - Password
  - Personal identification number (PIN)
- Possession factors: require the user to possess a specific piece of information or device before they can be granted access to the system
  - OTPs like the one used for Canvas
- Inherence factors: authenticate access credentials based on factors that are unique to the user
  - Fingerprints, thumbprints
  - Voice and facial recognition
  - Retina or iris scans
  - Any type of biometric scan
- Location factors: network administrators can implement services that use geo-location security checks to verify the location of a user before granting access to an application
  - IP addresses
  - If an organization just has employees in a certain city
- Behavior factors: based on actions undertaken by the user to gain access to the system. Systems that support behavior-based authentication factors may allow users to pre-configure a password by performing behaviors within a defined interface and repeating them later as a method of identity verification.
  - Mobile phone lock screens with a grid of dots
  - Windows 8 picture password feature

### Common scenarios

- Offline: local authentication, it compares the input data with the data stored on the machine. As an example, think of all the times you log in to your computer.
  - Manual: classical method of checking some form of physical ID before accessing a place.
  - Digital: needs devices or objects that interact with digital devices, either through a physical ID or through the usage of a digital code (like a QR code)
- Online: authentication via the internet, it connects to remote resources to authenticate the user, like when you log in to a website.
  - Search matches against a database
  - Usage of PKIs (Public Key Infrastructure)
  - OTP (One Time Password)
  - Fast ID Online Authentication (FIDO)

### Authentication techniques

- Password: needs a user and a password
- No password: for this case, the user is verified through the use of an OTP or via a link sent to the user's email
- 2 or more factors: adds an extra layer of security to the verification process. There exists the schemes 2FA or MFA, in general they use tokens, captchas, pins or security questions.
- Single sign-on: using the same credentials the user can access different systems, like the web browser, a social media and an app.
- Via social media: takes advantage of the user's social media accounts to verify its identity (log in with Facebook, Google, etc.)

## Authorization

> Involves checking what the identity that's been authenticated has access to

- Prevents an user from accessing an account that he/she is not authorized to access
- Verifies the privileges of the user
- Makes sure the user receives the right privileges for its needs

### Authorization techniques

- Role-based control access (RBAC): grants access and privileges based on the role the user plays in the organization
- Attribute-based access control (ABAC): uses attributes particular to the user in question depending on some additional factories like hierarchy, groups, etc. Its more complicated to manage, but provides more customization

### Secure Assertion Markup Language (SAML)

Authentication data is shared between the user, the identity server and a service provider through XML documents. The process can be described as follows:

1. The user requests a resource
2. The service provider receives the request and redirects it to the identity server
3. The user receives a petition from the identity server to provide a credential
4. The identity server authenticates the user and communicates the result to the service provider of whether provide permissions to the user or not
5. The service provider receives the request and depending upon the authentication process allows or denies the user access to the resource

### OAuth2.0

An open standard oriented to authorization that grants secure access in a delegated fashion through the usage of access tokens. It grants access to resources and data in apps, APIs and servers.

The process is described as follows:

1. The user (or resource owner) makes an authentication request through an app or a client
2. This request is redirected to an authorization server, it receives it, authenticates the user, and furthermore, there must exist a _consent_ step from the user
3. If everything was okay, the user is taken back to the client app, he's given a code
4. A token access is requested with the code given to the user to access the resource asked from the client application to the authorization server
5. If everything went accordingly, the user is granted an access token for the client app.
6. Now with the token in hand, the user asks access to the resource to a resource server
7. The token is validated for the user to finally have access to the protected resource from within the resource server

## Accountability

> Being accountable for the actions a person takes, the easiest way to do is to record all performed activities

It allows administrators to:

1. Trend analysis
2. Planning capacity
3. Perform billing
4. Assign costs and control them
5. Perform auditing

One of the most well known AAA protocols is RADIUS (Remote Authentication Dial In User Service), its improved version is called Diameter.
