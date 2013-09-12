# Introduction

The Internet is a decentralized system for sharing information of all
types, but unfortunately most social information (namely, identity
information intended for social consumption and related content
published by individuals) is concentrated within the centralized servers
of very few corporations, making it undesirably difficult for
individuals to reliably and efficiently access, transfer and preserve
much of the information they post online. Additionally, the
centralization of this personal information restricts the myriad ways in
which people could otherwise use it to publish and communicate, leaving
the development of new functionality that leverages this information to
these few corporations and their particular profit motives.

Asheville is a system intended to help individuals achieve more control
and functionality with the information they've historically handed over
to these corporations while *not* requiring these same individuals to
divorce themselves from the centralized status quo, since that would
impose an unreasonably costly requirement. It does so by leveraging the
emergence of cloud synchronization solutions such as Dropbox and iCloud
to copy the information that individuals post to centralized social
networks over to their own cloud storage accounts and devices and
simultaneously provide a platform for applications to use these
individually owned copies as their data sources.

This has the immediate benefit of ensuring close ownership of social
information by individuals rather than just centralized hosts, enabling
local file access to this information and safeguarding against future
changes to those hosts that may jeopardize access even further. The
concomitant decentralized hosting of this same information via the APIs
of the individuals' cloud storage solutions also enables any number of
services to be built that improve the ways in which these individuals
share their information and communicate online, such as to publish
social information on their own domains and independently maintain their
own online profiles. These independent hosts can be used to power
isolated websites and similar publishing points, or they can be used by
applications that use various individuals' data to produce rich social
experiences.

# Three Components

Asheville can be broken down into three main components: **Sync**,
**Platform** and **Apps**. These should be designed to operate and be
hosted independently of one another, but they can also be consolidated
into a single service that plays all three roles.

The "Sync" component is responsible for synchronizing a person's data
from various social networks and user-generated-content services (e.g.
Facebook, Instagram, Foursquare or Twitter) over to their cloud storage
account (e.g. Dropbox or iCloud) on an initial and then ongoing basis.
It must have authorization to read content from the person's various
online presences as well as write to his or her storage account. It must
also have the intelligence to understand the various formats used by
service APIs to host user data and then combine similar or identical
data types from these various services into locally consistent formats
within their cloud storage accounts (using well-documented file and
folder structures).

Because people oftentimes post the same content across several services
online, the Sync service must also know how to detect when it has
already synced a given piece of content from a different service,
deciding then to combine data about the content from the several
services rather than creating a new copy as if it were a different piece
of content. For example, if a person were to post a photo originally to
Instagram but syndicate it to Facebook, that photo should be stored as a
single copy within the person's cloud storage with meta data from both
Instagram and Facebook saved alongside it.

The meta data included alongside synchronized content can include any
number of types, such as timestamp data for when the content was
originally published, source data for where it was originally published,
and syndication data for where it was cross-published. It can also
include related social data, such as any likes or comments that other
people have left in response to the content. Since including social
feedback within content metadata involves the identities of other
people, it may be useful to store data about the person's social
connections separately, but relatedly, within their cloud storage as
well.

The user experience around setting up Sync for a given person primarily
involves obtaining authorization to their online services and cloud
storage account. This would permit workers to begin importing and
processing data from these services in the background. However, to
ensure the person has full visibility into, and control over, the
synchronization process, a dashboard should be provided (probably via
the web, at least to start) that informs the person in real-time just
which accounts with importable data are set up, the progress of their
synchronization, and a breakdown of just what kinds of content has been
scheduled for synchronization or already synchronized. It should also
provide options to tweak just what kinds of content should be
synchronized from each source as well as to kickstart or restart
synchronization outside of the background workers' default schedules. It
could additionally provide a preview of the synchronized content,
particularly in a stream of updates as they get imported initially.
