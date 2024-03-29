# The Jabber Spam Fighting Manifesto

*Version 0.8, 2018-04-07*

The Jabber network (a federated set of thousands of servers with many
tens or hundreds thousands of users) is under a continuous flood of spam
messages for multiple years. Similar to the open email relays of the
mid-1990s, public (and often abandoned) XMPP servers are being abused to
deliver those messages.

We, as the operators of public XMPP servers, commit to the following
*Server Policies* to fight spam on our servers, and we announce our intent
to block incoming communication from public servers that distribute spam
messages and do not react to abuse reports. Furthermore, we
will inform other *Public Server* operators and the general public of
domains sending spam and not reacting to abuse reports by keeping those
servers on a [public blacklist](https://github.com/JabberSPAM/blacklist).

## Server Policies

A *Public Server* is an XMPP server that allows both the registration of
accounts by third parties (either via [In Band Registration][XEP-0077]
or by other means, like a web form), and federation to other XMPP
servers, making it possible for its users to reach out to other XMPP
domains.

The operators of a *Public Server* shall perform the following actions to
fight spam:

* Provide an abuse contact according to
  [XEP-0157: Contact Addresses for XMPP Services][XEP-0157] and
  react to incoming abuse reports in a timely fashion.

* Limit the number of new user registrations per IP address per hour.

* Monitor and review registrations from IP addresses with bad reputation
  (open proxy servers, Tor exit nodes), OR enforce additional checks on
  those users, for example by requesting a CAPTCHA or verifying the user's phone number.

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

## Commitment

Signed,

 * Ave Ozkal, Luna Mendes, **a3.pm** (https://a3.pm/xmpp.html)
 * Thomas Camaran, **chatme.im** (https://chatme.im/)
 * Mathias Ertl, **jabber.at** (https://jabber.at)
 * Emmanuel Gil Peyrot, Mathieu Pasquet, **jabber.fr** (https://jabberfr.org)
 * Stian B. Barmen **jabber.no** (https://www.jabber.no/)
 * Oxpa, Ermine, **jabber.ru** (https://jabber.ru/)
 * Rafal Zawadzki, **jabberpl.org** (https://jabberpl.org)
 * Sven Sperling, **jabbers.one** (https://jabbers.one)
 * Marco Cirillo, **lightwitch.org** (https://lightwitch.org)
 * Nico Wellpott **magicbroccoli.de** (https://magicbroccoli.de/xmpp/)
 * Carlos Lopez, **parloteo.es** (https://parloteo.es)
 * Carlos Lopez, **suchat.org** (https://www.suchat.org)
 * Tsukasa Hamano, **xmpp.jp** (https://www.xmpp.jp/)
 * Georg Lukas, **yax.im** (https://yaxim.org/yax.im/)
 * ... _(ordered by server name)_

*	*	*

_If you run a public Jabber server and commit to the above Policies, please
sign the manifesto by opening a PR with your name, server domain and a URL
of the service description._
