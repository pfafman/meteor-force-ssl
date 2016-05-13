# force-ssl

A fork of Meteor 'force ssl' package with the addition of stopping sockjs from sending out the CORS header for non-ROOT_URL origins.
It does this by denying any request with the origin header set and it is not set to the current ROOT_URL base.

Other than that it causes
Meteor to redirect insecure connections (HTTP) to a secure URL
(HTTPS). Use this package to ensure that communication to the server
is always encrypted to protect users from active spoofing attacks.

To simplify development, unencrypted connections from `localhost` are
always accepted over HTTP.

Application bundles (`meteor bundle`) do not include an HTTPS server or
certificate. A proxy server that terminates SSL in front of a Meteor
bundle must set the standard `x-forwarded-proto` header for the
`force-ssl` package to work.

Applications deployed to `meteor.com` subdomains with
`meteor deploy` are automatically served via HTTPS using Meteor's
certificate.