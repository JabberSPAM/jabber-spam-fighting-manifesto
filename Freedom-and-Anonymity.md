# Freedom and Anonymity on XMPP

There were some concerns that the [Spam Fighting Manifesto](README.md) will
impede the Freedom of Speech, break XMPP for (legitimately) anonymous users
and is an unacceptable invasion into the users' privacy. Examples of concerns
raised in public:

* [XMPP Manifesto for Freedom](https://gitlab.com/senpie/xmpp-manifesto-for-freedom)
* [xmpp.is: Why We DO NOT Fully Support “The Jabber Spam Fighting Manifesto”](https://xmpp.is/2018/02/21/the-jabber-spam-fighting-manifesto/)

All these points need to be discussed and addressed, but this discussion is
too long and too complex for the Manifesto. Therefore, we would like to
address them in this separate post.

## Freedom of Speech and Censorship

In the Manifesto of Freedom, it was implied that filtering spam and blocking
servers is a form of censorship, and that it violates the fundamental freedom
of users.

Freedom of Speech is considered a fundamental human right for good reasons.
And one might make the argument that [sending spam is covered by Freedom of
Speech rights](https://www.washingtonpost.com/news/the-intersect/wp/2014/07/31/is-spam-free-speech/).
And some of our users might even be interested in stolen credit cards, gift
cards and cheap drugs.

### Blocking Messages

With email, we have the luxury of hiding all the spam messages (automatically
filtered by our server) into a dedicated folder, which is well hidden in the
client and doesn't make our phone vibrate at 3 AM. For XMPP, we lack such a
function yet.

It would be great if each user could easily define which kind of unsolicited
messages they are interested in, right from their client. We already have a
mechanism for a user to [block individual senders](https://xmpp.org/extensions/xep-0191.html),
but it does not keep up with the auto-registered spam bots.

And it would be great if automatially classified messages would end up in a
dedicated "mailbox" that can be checked on demand. I'm sure we all miss the
XMPP version of the often-heard advice "please check your spam folder".

The reality for most users, however, is that they don't want to receive spam.
And they don't want to be bothered with configuring anti-spam plugins, jumping
through hoops to chat with a friend, and getting their important messages
[silently dropped](https://github.com/processone/ejabberd/issues/2197).

If we, the server operators, don't solve the spam problem for our non-nerd
users, they will simply move away to a different chat platform. And we will
have nobody but us to blame if they end up on Facebook Messenger, WhatsApp or
Telegram.

If we don't want the Jabber network to lose users even faster than it is
already, we must take measures now. Centralized spam detection and rejection
is such a measure, and it can be implemented with comparably low overhead.

### Blocking Servers

Obviously, blocking servers is also a kind of censorship. The Manifesto
imposes three preconditions to blocking a server:

* the server is public (i.e. allows anyone to register there) AND
* the server is used to send spam (and is thus actively harming the Jabber
  network) AND
* the admins do not react to abuse reports.

However, the Manifesto does not require the signers to block a server if these
conditions are met - it is still a judgment call for the operators.

There are hundreds of servers that are used by spambots, and most of these
servers lack proper abuse reporting mechanisms. The most probable background
is that their "admins" followed a How-To, read "allow to register accounts
right from your client" and enabled [In-band
Registration](https://xmpp.org/extensions/xep-0077.html) (IBR). They probably
even forgot that they enabled it, and maybe even forgot that they have an XMPP
server running.  Reports sent to the contact info on the respective domain or
IP address are ignored or not taken seriously.

Judging from the XMPP domain names of most such servers, they are small
businesses without a dedicated IT person, and they probably don't have more
than five real users. On the other hand, they have hundreds of spam bots
abusing the registration feature and harming the whole XMPP ecosystem.

If it is not possible to contact the administrators and to let them know of
the spam problem, we can either choose to let them poison our network, or take
appropriate measures. By blocking the whole server, there is a chance that the
actual users of the server will notice and complain to their admin, causing
them to finally take action.

By making a public "shame list", there is a chance that it will be reported
about and that the administrators will notice.

These servers are essentially open relays, and the email network provides [a
good precedent](https://en.wikipedia.org/wiki/Open_mail_relay) for how to
handle them. There are many alternative [DNS-based blacklists](https://en.wikipedia.org/wiki/DNSBL)
that identify open relays, proxy servers, Tor exit nodes or even dial-up
networks. The operators of these lists have documented their policies for
addition and for removal of IP addresses, allowing a server operator to choose
the most appropriate blacklist.  Most email providers will reject messages
sent from open relays, based on one of those lists.

Creating the framework for such lists is the mid-term goal of the Spam
Fighting Manifesto.

## Client-side Spam Blocking

The Manifesto for Freedom's main point is "Spam can be mitigated via
client-side entirely", but this does not scale well, and most people are
not technically competent enough to solve the spam problem on their own.

Some clients provide plug-ins to block messages from strangers, to ask them to
solve a captcha or to perform some other task to prove they are not a spam
bot. However, these mechanisms need to be set up by the user (which is often
complex, and requires that the user knows about the plug-in in the first
place). Furthermore, they break down if the user is connected with multiple
clients (should their friend solve a captcha for each client? What if the
clients deploy different mechanisms? What if their favorite mobile client does
not have any anti-spam plug-ins at all?).

On the other hand, having server-centralized spam protection works really
well, because it's easy to detect message patterns and to apply and adopt
block lists.


## Access over Tor

The most controversial requirement of the Spam Fighting Manifesto is this:

* Monitor and review registrations from IP addresses with bad reputation (open
  proxy servers, Tor exit nodes), OR enforce additional checks on those users,
  for example by requesting a CAPTCHA or verifying the user's phone number.

Blocking of Tor users and requiring phone numbers is obviously the end of the
privacy for all Jabber users with a legitimate interest in anonymity. Some
server operators already consider recording of IP addresses as a privacy
violation.

However, there are multiple reasons why this requirement was made:

1. Almost all spam bots registered on the author's server came from open
   proxies and Tor exit nodes, worsening the signal-to-noise ratio. From a
   purely pragmatic position, it makes sense to apply additional scrutiny to
   them.

2. Operating a server that's well suitable for anonymous users is much more
   than just allowing users to come via Tor. You also need to have good data
   hygiene, encrypted storage and proper physical access control. Otherwise,
   the roster and communication meta-data of your Tor users might leak enough
   information to get them identified and decapitated.
   If you care deeply enough about those things to not endanger people who
   must rely on Tor for their anonymity, it is not too much to assume that you
   can also detect and block spammers on your server in a timely fashion,
   without recording whatever data is against your policy. The Manifesto is
   written for "normal" administrators, running a server for the general
   public. They might actually have different trade-offs than you, like e.g.
   not to have their users spammed.

3. The Manifesto doesn't *forbid* access via Tor, it merely asks to
   monitor and review registrations, or to enforce additional checks. So it
   would be perfectly compliant to provide other means of ensuring that no
   spam is sent out. Ideas for alternative solutions are:

   * limit the number of pending subscription requests + unsolicited messages
     for accounts registered via Tor to 3 per day. Flag them if they attempt
     to exceed that by a large amount.

   * Prevent Tor accounts from communicating with external servers.

   * Ask Tor accounts to join your support MUC where you can un-flag them
     manually.


## On Requiring Phone Numbers

Asking for the phone number is merely one example of how to implement
anti-spam safeguards, not a binding requirement of the Manifesto. For a mobile
messenger it might make sense to bind the user identity to a phone number
anyway - this would allow easy password recovery and provide sensible limits
on the number of per-user accounts, because phone numbers cost real money.

For desktop messengers, it might make more sense to use some cloud account
instead of a phone number, however [prices on those](https://krebsonsecurity.com/2013/06/the-value-of-a-hacked-email-account/)
[vary significantly](https://buyaccs.com/en/).

