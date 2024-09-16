# The booger goblin project

Spell Class : Blue Magic

Spell Level : Introduction

Topics : Python, Snort

---


# Why is it always Snort?

So I was forced to attent a training on Detection and Counter Intrustion. TLDR; It was aweful and outdated by an impressive amount. Using such an old version of Security Onion was not even familar with how to login to the service. After our blocks of instruction I had a breaking point when it was told to me that inputing rules by hand was the best way to do it. After picking up my jaw from the floor I set about browsing to the Snort Documentation and setting up the basics of what makes a rule.

https://docs.snort.org/rules/

```snort rule
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

### What makes a rule

For snort3 I make a little chart for myself.

- step one   : Rule Action https://docs.snort.org/rules/headers/actions `*alert* tcp $EXTERNAL_NET 80 -> $HOME_NET any`
 - alert
 - block
 - drop
 - log
 - react
 - reject
 - rewrite
- step two   : Protocol https://docs.snort.org/rules/headers/protocols `alert *tcp* $EXTERNAL_NET 80 -> $HOME_NET any`
 - ip
 - icmp
 - tcp
 - udp
- step three : IP Source / Dest https://docs.snort.org/rules/headers/ips `alert tcp *$EXTERNAL_NET* 80 -> *$HOME_NET* any`
 - any
 - !192.168.1.1 (Inverse operator)
 - \[192.168.1.0/24\] (Range Operator)
 - $TEST (Variable's)
- step four  : Port
 - any
 - $TEST (Variable's )
 - : (Range Operator) 1:10 (Between 1 and 10) :100 (Less than or Equal to 100) 100: (Greather than or equal to 100)
- step five  : Direction 


