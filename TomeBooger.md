# The booger goblin project

Spell Class : Blue Magic

Spell Level : Introduction

Topics : Python, Snort

---


# Why is it always Snort?

So I was forced to attent a training on Detection and Counter Intrustion. TLDR; It was aweful and outdated by an impressive amount. Using such an old version of Security Onion was not even familar with how to login to the service. After our blocks of instruction I had a breaking point when it was told to me that inputing rules by hand was the best way to do it. After picking up my jaw from the floor I set about browsing to the Snort Documentation and setting up the basics of what makes a rule.

https://docs.snort.org/rules/

```rule
alert tcp $EXTERNAL_NET 80 -> $HOME_NET any
(
    msg:"Attack attempt!";
    flow:to_client,established;
    file_data;
    content:"1337 hackz 1337",fast_pattern,nocase;
    service:http;
    sid:1;
)

```
