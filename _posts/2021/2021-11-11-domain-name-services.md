---
layout: post
title:  "Domain name services: DNS, whois, nslookup, dig"
date:   2021-11-11 12:00:00 +0200
---

What is DNS?

Let’s start from the very beginning. DNS stands for “Domain Name System”, which provides you OSI-compatible set of protocols for transforming domain name to IP-address (and other data, but we will talk about it a bit later). Why do we need that? IPV4 protocol provides you about 255⁴ = 4,228,250,625 IP addresses. Every IP address, at least IPV4 version has next notation:

`[1–255].[1–255].[1–255].[1–255]`

As you probably know, we need IP addresses to find computers, servers and other devices, which have network card by the IP-address. Every site we visit is a server, that returns web page — set of documents with HTML, CSS, JS. Every such server has it’s own IP. But how do we memorize all these IP addresses?

Google, stackoverflow, instagram, facebook, twitter, youtube — we use these services every day and every service is being run on it own server, which have it’s own IP address. It’s unreal to remember!

That’s why smart people have invented DNS — it takes a domain name in human-friendly format , and resolves it to an IP-address for a PC. Before that, you need to add IP address and corresponding domain name to DNS server.
How does DNS search for IP addresses

DNS name (domain name) matches following pattern:

`<string>.{0,4}.`

Examples:

- linkedin.com.
- eu.wikipedia.com.
- my.blog.devops.com.

Global DNS database consists of about 330 million records. It’s unreal to keep such amount of records on one server, so modern DNS is being distributed around the world.

DNS is split on subdomains and every subdomain, as a rule, represent authoritative DNS servers, that contain domain names and corresponding records. Like a table!

DNS name starts from ROOT server, that could be represented as dot (.). Every domain name contain a dot at the end, but browsers/programs hide this dot due to uselessness of this information. What the sense of rendering information that will be same in any case? So when you appear on a site with domain name, for example, “youtube.com”, you are actually appeared on “youtube.com.” domain.

Root is the heart and center of DNS. It binds all domain branches and root is the place where all branches diverge.

If we visualize DNS in a picture, we will see, that DNS have strong hierarchical structure:
DNS have hierarchical structure

We can make a conclusion, that algorithm of search in DNS will be same as for any structure, that represents “tree” data structure: DNS also have root, parent nodes (parent domains), child nodes (subdomains, child domains) and zones. So if you are familiar with “tree” data structure, you can guess how search works.

**Example #1**

For example, let’s imagine, that we are on “linux.org.” DNS server. We are asking DNS to find “eu.wikipedia.org” server. linux.org go upper to “org.” domain. DNS will find out, that both servers are in same domain zone!

Domain zone —zone, where all subdomains could be found downstream of the parent domain.

So, the parent domain of “eu.wikipedia.org” was found. Now we need to ask “org.” domain for “wikipedia.org.” IP address. “org.” domain responses with corresponding IP address, and at the same time we ask “wikipedia.org.” for “eu.wikipedia.org.” domain. Great! We have found the required domain.

**Example #2**

Let’s start now from “donuts.net.” and search for “linkedin.com”. Same steps as in example #1, but there is a problem — “com.” and “net.” domain are not familiar at all! That’s why DNS go to root server (.). Now, from root server, we can achieve “com.” domain and then “linkedin.com”. That’s why ROOT domain is necessary — it binds all domains in one unit structure.

**Example #3**

We are on “linux.org” and asking for “eu.wikipedia.org”. Again. And we will get response immediately, because DNS, probably, has cached “eu.wikipedia.org” domain.
Record types in DNS

DNS gives you not only IP addresses, that correspond to specific domain name. DNS also can give you (if domain name owner has also created) another information from records, that were also attached to domain name, like IPV6 address, mail address, etc.

I want to list most popular records and briefly describe them:

- A record — This record contains IPV4 address, like “15.230.117.95”
- AAAA record — Similar to A record, but instead of IPV6, it contains IPV6 address.
- MX record — Refers to mail server. You can assign, for example, IP address “15.230.117.95” to domain name “backpack.user.com” as an A record, but if you have mail server on another IP address, sending mail on <user_name>@backpack.user.com will send this mail to IP address, specified in MX record.
- NS record — Refers to authoritative DNS servers for current subdomain- to server, that contain exact record’s domain name and corresponding records.
- CNAME record — Forwards from one domain/subdomain to another. For example, we can create CNAME for google.com, that will refer to www.google.com.
- TXT record — Simple text record.
- SRV record — Also defines a port for specific service.
- PTR record — DNS also can do “Reverse DNS search” via PTR records: you provide IP address and DNS gives you corresponding domain. PTR records mostly used for mail security.
- SOA record — Store another important information about domain owner and domain at all.

Tools for work and troubleshooting DNS

No matter what operations system is installed on your PC, you always (in case, if it’s not “Denchik’s Debian-based linux distro rebuild 2020”) have a set of utilities for interaction with DNS. As a rule, all these utilities could be found or downloaded for any operating systems. Operating systems differ in DNS utilities question only by preinstalled utilities. You always have option to install lacking software.

## dig

The dig command is being used for interrogating DNS name servers. As man dig says:

    Most DNS administrators use dig to troubleshoot DNS problems because of its flexibility, ease of use, and clarity of output.

And this is true! The dig command is the most flexible and expanded tool for work with DNS. It has a bunch of flags, that help you to specify your query as deep, as it possible.

The dig command usage:

`dig @server name type`

Where server is name or IP address of DNS server. If there is no server parameter provided, the command will check /etc/resolv.conf for them. resolv.conf file contain list of name servers.

Name is a domain name you want to receive information about.

Type is for DNS record type, that I have described above. Like A, AAAA, MX, etc.

Let’s try to search for MX record in linkedin.com domain name. We need only answers, so we add flags +noall and +answer:

```
ArtemMaksymov@my-pc ~ % dig +noall +answer @8.8.8.8 linkedin.com MX
linkedin.com.        1888    IN    MX    10 mail-d.linkedin.com.
linkedin.com.        1888    IN    MX    10 mail-a.linkedin.com.
linkedin.com.        1888    IN    MX    10 mail-c.linkedin.com.
linkedin.com.        1888    IN    MX    20 mail.linkedin.com
```

The dig command provides you more flags and options, so I want to give you advice to read man page of dig and following commands.

## whois

The whois command is interesting, because it provides you metadata about your domain name, like domain, organization, that provides this name, contacts, phone numbers, etc.

The whois command usage:

`whois <domain_name>`

Whois could be useful, if you want to find owner of the domain, for example, if you want to redeem this domain, but you need to get in touch with owner before. Social engineers and penetration testers can find this tool useful too.

Let’s try to find some information about the same linkedin.com domain. Whois command returns you massive output, so I will put only head of response.

```
ArtemMaksymov@my-pc ~ % whois linkedin.com
% IANA WHOIS server
% for more information on IANA, visit http://www.iana.org
% This query returned 1 object

refer:        whois.verisign-grs.com

domain:       COM

organisation: VeriSign Global Registry Services
address:      12061 Bluemont Way
address:      Reston Virginia 20190
address:      United States

contact:      administrative
name:         Registry Customer Service
organisation: VeriSign Global Registry Services
address:      12061 Bluemont Way
address:      Reston Virginia 20190
address:      United States
phone:        +1 703 925-6999
fax-no:       +1 703 948 3978
e-mail:       info@verisign-grs.com

contact:      technical
name:         Registry Customer Service
organisation: VeriSign Global Registry Services
address:      12061 Bluemont Way
address:      Reston Virginia 20190
address:      United States
phone:        +1 703 925-6999
fax-no:       +1 703 948 3978
e-mail:       info@verisign-grs.com

nserver:      A.GTLD-SERVERS.NET 192.5.6.30 2001:503:a83e:0:0:0:2:30
nserver:      B.GTLD-SERVERS.NET 192.33.14.30 2001:503:231d:0:0:0:2:30
nserver:      C.GTLD-SERVERS.NET 192.26.92.30 2001:503:83eb:0:0:0:0:30
nserver:      D.GTLD-SERVERS.NET 192.31.80.30 2001:500:856e:0:0:0:0:30
nserver:      E.GTLD-SERVERS.NET 192.12.94.30 2001:502:1ca1:0:0:0:0:30
nserver:      F.GTLD-SERVERS.NET 192.35.51.30 2001:503:d414:0:0:0:0:30
nserver:      G.GTLD-SERVERS.NET 192.42.93.30 2001:503:eea3:0:0:0:0:30
nserver:      H.GTLD-SERVERS.NET 192.54.112.30 2001:502:8cc:0:0:0:0:30
nserver:      I.GTLD-SERVERS.NET 192.43.172.30 2001:503:39c1:0:0:0:0:30
nserver:      J.GTLD-SERVERS.NET 192.48.79.30 2001:502:7094:0:0:0:0:30
nserver:      K.GTLD-SERVERS.NET 192.52.178.30 2001:503:d2d:0:0:0:0:30
nserver:      L.GTLD-SERVERS.NET 192.41.162.30 2001:500:d937:0:0:0:0:30
nserver:      M.GTLD-SERVERS.NET 192.55.83.30 2001:501:b1f9:0:0:0:0:30
ds-rdata:     30909 8 2 E2D3C916F6DEEAC73294E8268FB5885044A833FC5459588F4A9184CFC41A5766
```

## host

You can treat this command as a simplified version of dig. Lite output for people, who need basic dig functionality.

The host command usage:

`host <domain_name> # Not difficult at all!`

Let’s check for MX records of an old plain linkedin.com

```
ArtemMaksymov@my-pc ~ % host -t MX linkedin.com
linkedin.com mail is handled by 10 mail-a.linkedin.com.
linkedin.com mail is handled by 10 mail-c.linkedin.com.
linkedin.com mail is handled by 10 mail-d.linkedin.com.
linkedin.com mail is handled by 20 mail.linkedin.com.
```

## nslookup

The nslookup command is used for same targets as host command, but nslookup is interesting because of interactive mode this command have unlike host command.

The nslookup command usage:

`nslookup # For interactive mode`

`nslookup <domain_name> [options] # For non-interactive mode`

Linkedin…it’s your time!

# Non-interactive mode

```
ArtemMaksymov@my-pc ~ % nslookup linkedin.com -querytype=mx
Server:        192.168.20.167
Address:    192.168.20.167#53

Non-authoritative answer:
Name:    linkedin.com
Address: 13.107.42.14# Interactive mode 
ArtemMaksymov@my-pc ~ % nslookup                           
> linkedin.com set querytype=mx
Server:        192.168.20.167
Address:    192.168.20.167#53

Non-authoritative answer:
Name:    linkedin.com
Address: 13.107.42.14
Name:    linkedin.com
Address: 2620:1ec:21::14
>
```

{% include farewell.md conclusion="We have found out why do we need DNS and what commands will be useful for work with DNS." %}

Sources:

- https://computer.howstuffworks.com/dns.htm
- https://www.networkworld.com/article/3268449/what-is-dns-and-how-does-it-work.html
- https://computer.howstuffworks.com/dns.htm
- https://library.netapp.com/ecmdocs/ECMP1155586/html/GUID-B8B50EB6-638F-4DAD-BEA7-E2F72E20953C.html
- https://www.cloudflare.com/en-ca/learning/dns/dns-records/
- https://constellix.com/news/dns-record-types-cheat-sheet