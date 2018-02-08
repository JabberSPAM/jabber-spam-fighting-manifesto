# The Jabber Spam Fighting Manifesto

*Version 0.3, 2017-12-30*

The Jabber network (a federated set of thousands of servers with many
tens or hundreds thousands of users) is under a continuous flood of spam
messages for multiple years. Similar to the open email relays of the
mid-1990s, public (and often abandoned) XMPP servers are being abused to
deliver those messages.

We, as the operators of public XMPP servers, commit to the following
*Server Policies* to fight spam on our servers, and we announce our intent
to block incoming communication from public servers that distribute spam
messages and do not adhere to the *Server Policies*. Furthermore, we
will inform other *Public Server* operators and the general public of
domains sending spam and not reacting to abuse reports.

## Server Policies

A *Public Server* is an XMPP server that allows both the registration of
accounts by third parties (either via [In Band Registration][XEP-0077]
or by other means, like a web form), and federation to other XMPP
servers, making it possible for its users to reach out to other XMPP
domains.

The operators of a *Public Server* shall perform the following actions to
fight spam:

* Implement [XEP-0157: Contact Addresses for XMPP Services][XEP-0157] and
  react to incoming abuse reports in a timely fashion.

* Limit the number of new user registrations per IP address and hour.

* Monitor or block registrations from IP addresses with bad reputation
  (open proxy servers, Tor exit nodes), or enforce additional checks on
  those users, like a CAPTCHA or a valid phone number.

* Throttle the traffic from local clients, especially unsolicited
  subscription requests and messages.


[XEP-0077]: https://xmpp.org/extensions/xep-0077.html
[XEP-0157]: https://xmpp.org/extensions/xep-0157.html

## Schedule

With our signature under this Manifesto, we assure that our servers are
already following the above stated *Server Policies*.

Starting with **July 1st, 2018**, we will start blocking incoming server
connections from Public Servers not following the *Server Policies* above,
if those are forwarding spam messages to our users. The blocking message
will contain a reference to this Manifesto.

## Committment

Signed,

Georg Lukas, **yax.im** (https://yaxim.org/yax.im/)
Carlos Lopez, **suchat.org** (https://www.suchat.org)

...

*	*	*

_If you run a public Jabber server and commit to the above Policies, please
sign the manifesto by opening a PR with your name, server domain and a URL
of the service description._
