# Features

This chapter is intended to help you understand what features the CAS server product can provide. A subsequent chapter _Editorial note: alas, that subsequent chapter is still to be written!_ discusses configuration of these features -- this chapter is just the tour of what there is to configure.

(There's also a [four-page PDF][cas-product-brochure] that may meet your glossy brochure needs.)

## Single Sign-On for the Web

Jasig CAS implements single sign-on for the Web.

This means that, within a browser session, users can log in once to CAS, and then log in to additional applications without having to again enter their credentials (most commonly, username and password).

CAS accomplishes this by means of a secure cookie between the end user's Web browser and the CAS server. This cookie is exclusively to allow the CAS server to recognize that user on a subsequent login attempt within the single sign-on session -- services making use of CAS don't have to (indeed, shouldn't) see this cookie, nor is this cookie required to accomplish CAS-mediated login to a service.

CAS-using applications can opt out of participation in single sign-on, instructing the CAS server to require that the end user present username and password to accomplish login to the application even if a CAS single sign-on session is already otherwise established.

Single sign-on improves the user experience and improves user convenience.

## Centralized login experience

CAS centralizes the login experience for participating applications in your institution.

Applications can enjoy this benefit even if they do not choose to participate in single sign-on.

Centralizing the login user experience creates opportunities to optimize this experience once centrally, adorning it with the supporting information and links that will allow users to log in successfully and applying your institutional brand to the login experience.

## User authentication

CAS services as the login and single sign-on user experience web application, but is not itself a repository for end-user accounts and credentials. Rather, CAS integrates with an external means of credential validation of your choice. You'll probably choose LDAP (whether as implemented in Microsoft ActiveDirectory or as implemented in another LDAP server implementation), but you could instead choose to check against hashed passwords stored in a database, rely upon the container (say, an Apache module), use RADIUS, accept an X.509 certificate, or rely on a JAAS plugin. CAS boasts many existing useful implementations of its AuthenticationHandler API and of course you can write your own if needed.

## Delegated authentication

CAS provides end-user-facing single sign-on for the Web. CAS also provides more than this -- it supports delegated authentication by the services making use of CAS. When a user logs in to a service, that service can then authenticate to other services on behalf of that user in the course of this CAS single sign-on session, providing those other services accept this delegated authentication, all without replay of the end user's password.

This is the CAS proxy ticket feature, a compelling, more secure alternative to password replay.

## Attribute Release and Per-Service Opaque Identifiers

In building a user single sign-on session, CAS can collect user attributes for an authenticated using the Jasig PersonDirectory software library. This software supports reading attributes from LDAP and from databases with many configurable options, and of course also offers extensible APIs so that if you need to read attributes from somewhere other than LDAP and databases, you can.

Collecting these attributes is useful because CAS can release these attributes to services using the SAML validation response support.

By default, CAS will release the end user's username to any service using CAS, even if they're using the traditional CAS validation responses rather than SAML. (Indeed, the username is the only user identifier the traditional CAS protocols release.) However, you can on a per-CAS-using-application basis choose instead to release a computed per-service unique identifier rather than a username.

## Services registry

That per-service configuration happens in the Services Registry.

In the Services Registry, which features a Web-based administrative UI, CAS administrators can configure which services are permitted to use CAS for user login, to participate in single sign-on, and to perform delegated authentication. Service registrations can select which user attributes will be released to each service. Registrations can match patterns to apply to multiple services -- by default the Services Registry includes patterns with will apply generic, permissive registration to all services. As such use of the Services Registry is optional.

## Extensible login web-flow experience

CAS implements its login experience using Spring Web Flow, a free and open source framework for building end-user-facing Web-based flows. That simple CAS login form is actually a whole flow, processing the user's login request to apply single sign-on behaviors if appropriate, to request and authenticate user credentials, and to send the user along to the requested service.

It's a web flow, but it's still a pretty simple one.

CAS adopters have extended this Spring Web Flow login flow to do require user acknowledgement of policy, to reflect account status, and to otherwise provide customized login experiences.

## Audit trail

CAS implements Inspektr, an open source Java software library for audit trail generation.

Several important user and service interactions with the CAS server generate audit log events, including end user login and validation of CAS-issued tickets by the applications making use of CAS.

By implementing CAS, you can optionally attain an audit log of who logged in to what services from what IP addresses when, across all of your CAS-using applications, an audit log that may prove useful in following up on a security incident inquiry.

## Support for high availability

By default, CAS uses simple in-memory implementations of its ticket cache and the registry of services making use of CAS. However, several options are provided for multi-node, high-availability clustering of ticket registry state and service registry state. These options for the ticket registry include JPA (database), JBossCache, memcached, and -- as a contributed but not shipping-with-CAS extension -- EhCache. The service registry supports JPA for shared storage of the registrations.

## No license fees

Jasig CAS Server is free and open source software. There are no license fees to pay, no expiring trial periods, no license keys, no per-server fees, no enterprise edition, none of that, for the CAS server itself. (However, your source of the CAS server may have packaged CAS or a modified version of CAS with other software, and charged you license fees for that. They can do that because of the freedoms they enjoy over the software discussed in the next point. Jasig CAS Server itself, as developed, shared, and vended by Jasig, is free and open source software and there is no license fee for Jasig CAS as distributed by Jasig.)

## Freedom

Jasig CAS Server is free and open source software. You can use it for anything you like, on any hardware you like, anywhere you like, give copies to anyone you like, make any changes you like, and share those changes with anyone you like. You're also free to not do any of these things. You can build proprietary software on CAS and charge anyone you like whatever you can get them to pay for it, though CAS as developed and distributed by Jasig will always be freely available at no license fee.

## Community

Jasig is a collaborative free and open source software project sponsored by Jasig, a consortium of higher education institutions and commercial partners advancing free and open source software -- and especially advancing collaboration upon free and open source software.

The greatest feature of CAS may be its community, including an active email list for discussion of adopting and locally implementing CAS, an active email list for discussion of and collaborating upon advancing the Jasig CAS open source software project, a plethora of institutions who have adopted CAS (within and beyond higher education), presence at Jasig's periodic (in recent history, annual) conferences, a frequented IRC chat room on freenode, and commercial partners ([Jasig CAS Solutions Providers]) providing commercial services in support of CAS implementation.

[Jasig] is a membership organization. If you've derived value from CAS, or even if you haven't, perhaps your organization should consider a relationship with Jasig.


[cas-product-brochure]: http://www.jasig.org/sites/jasig.webchuckhosting.com/files/cas_brochure_v4.pdf

[Jasig CAS Solutions Providers]: http://www.jasig.org/cas/support/solutions-providers
[Jasig]: http://www.jasig.org/
