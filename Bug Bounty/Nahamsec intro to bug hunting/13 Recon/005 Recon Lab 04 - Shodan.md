

https://www.shodan.io/

All right, the last tool we're going to talk about is **Shodan**. Shodan(https://www.shodan.io/) is also very, very powerful and can actually be used to identify more assets.
![[Screenshot From 2025-03-18 16-08-13.png]]
We're just going to start by simply type in the hostname. This is the hostname, like `gm.com`, we’re going after. Based on this, it will give us a list of assets that include the IP addresses with the open ports, the headers, and all that information that we need.
![[Screenshot From 2025-03-18 16-12-07.png]]
So, we're going to pull up one of these. We’ll open this one up just to show what kind of information it indexes.
![[Pasted image 20250318161248.png]]
![[Screenshot From 2025-03-18 16-13-13.png]]
You can see that it shows you where it’s hosted, what country, who the ISP is — which is General Motors — the organization is Akami as well. Ports 80 and 443 are also available to this. It could be kind of old; you can rely on it sometimes, but ==I highly recommend doing your own port scanning.==

But again, we can do this by typing _hostname_ and it gives you all this information. On the left side, you can also do it based on the _product_. So, if you want to look for Microsoft IIS, you can click on this. If you’re looking for Apache Tomcat, you can filter by it and it will show you all the applications that are on the domain _gm.com_ that are hosted on Apache Tomcat as well.


Let this load, and you can see right here, the organization is General Motors and it shows that it is a Tomcat. It also shows the common name for the certificate, who issued it, and so on.

Let’s look at _organization_. We’re going to click on this. You can also manually type this in and do _organization_ as "General Motors" — put the organization name in quotation marks. It will bring you all the IP addresses that match all the filters in the search.

For this case, I’m going to take everything out. We’re just going to leave _org_ as General Motors. Also, this is a really, really good way to find domains that belong to another company by putting the organization name based on who owns the actual IP address.

In other words, the domain may come back as something else other than _gm.com_, but it’s pointing to an IP address that is owned by GM. In this case, I don’t see any of them, but there are times where they could come up as an internal domain that we didn’t know existed but is hosted on their IP address as well.

The other thing you can do is you can type in _SSL_ — which looks for certificates — and you can do _gm.com_, for example. That would bring up all of the different domains that have _gm.com_ in the SSL.

And last but not least, the other cool thing you can do with this is you can actually specify ports, for example, 8443. You can say, "Hey, bring me everything that has SSL, has GM in it, with the open port 8443 where an application could be hosted."

Let’s see if anything comes up for this. It might take a second because of how large that target is. But as you can see, it just came back. We can click on it and go on to the actual results.

And right here, we can see that 8443 is open and so is port 8080. But it looks like they’re hosting some Microsoft IIS on there. Doesn’t matter what it is, but again, it extends your attack vector and also shows you other domains that could be owned by them — like this one _gm.com_ that belongs to China Telecom, but it looks like the common name of the certificate has _GM_ in it. Port 22 is open, port 8443 is also open, which also shows us a system that has a certificate on it.

And you can see right here, it’s aimed at _-gm.com_, which looks like it doesn’t belong to GM because it’s not the same domain. But it’s a good place to show how the port filtering works as well.

So again, we could do this. We can even narrow it down even more by getting rid of the _SSL_ term and typing in _organization = General Motors_. This way, we don’t get any false positives.

So start again by typing _org = General Motors_. And this would only look at IP addresses that are owned by General Motors. And the 8443 is actually open, and you can see a bunch of them are coming back. A bunch of them are coming back right now with port 8443 being open.

And you can actually look at it. This one has port 8443 and 8443 open as well.