---
title: Secure WordPress or Drupal Sites with Sucuri Cloud Proxy
description: Detailed information on using Sucuri Cloud Proxy to protect against malware, hackers, and blacklists.
category:
  - developing
authors:
  - atjuch
date: 8/7/2015
---
With malicious attacks gaining popularity across the internet, it is becoming increasingly important to secure your site. The intent of these attacks vary, ranging from service interruption to malware injections, and more. In this guide, we will set up a Cloud Proxy service to protect your website and stay ahead of potential attacks.

## Why Sucuri?

[Sucuri](https://sucuri.net) offers a variety of online tools ranging from Website AntiVirus, Cloud Proxy (Firewall), Free Website Security Scan, and more.

### How Sucuri Protects Against DDoS / DoS Attacks

They protect these attacks by implementing a multi-layer filtering system that comes from several Internet Service Providers (ISP) to provide additional bandwidth when the attack happens.

The goal is to saturate or flood the network to the point of failure. With the added bandwidth from companies such as (Amazon AWS, Google CE and OVH), it allows Sucuri to sustain and divert the volumetric attacks. They also do not not have to manage their own infrastructure, the ability to scale and respond on-demand delivers faster resolution.

### Block any type of attack

Since all of the web requests are proxied, the network layer DDoS attackers never actually hit the client's server. This creates the ability to mitigate all network level attacks.

<table class="table">
	<tbody>
			<tr>
        <th align="left" style="width: 130px">TCP SYN+ACK</th>
        <th align="left" style="width: 130px">Slowloris</th>
        <th align="left" style="width: 130px">DNS Flood</th>
        <th align="left" style="width: 130px">TCP FIN</th>
        <th align="left" style="width: 130px">Spoofing</th>
			</tr>
			<tr>
			</tr>
			<tr>
        <th align="left" style="width: 130px">NXDomain</th>
        <th align="left" style="width: 130px">TCP RESET</th>
        <th align="left" style="width: 130px">ICMP</th>
        <th align="left" style="width: 130px">Mixed SYB</th>
        <th align="left" style="width: 130px">TCP ACK</th>
			</tr>
      <tr>
        <th align="left" style="width: 130px">IGMP</th>
        <th align="left" style="width: 130px">Ping of Death</th>
        <th align="left" style="width: 130px">TCP ACK + PSH</th>
        <th align="left" style="width: 130px">HTTP Flood</th>
        <th align="left" style="width: 130px">Smurf</th>
			</tr>
      <tr>
        <th align="left" style="width: 130px">TCP Fragment</th>
        <th align="left" style="width: 130px">Brute Force</th>
        <th align="left" style="width: 130px">Reflected ICMP & UDP</th>
        <th align="left" style="width: 130px">UDP</th>
        <th align="left" style="width: 130px">Connection Flood</th>
      </tr>
			</tr>
	</tbody>
</table>

## Prerequisites

### Direct Your Domain to Pantheon
In order to add Sucuri Cloud Proxy services, you must already have a domain directed to Pantheon and added to the Live environment. For more instructions, please see [DNS Records for Directing Your Domain to Your Pantheon Site](/source/docs/articles/sites/domains/dns-records-for-directing-your-domain-to-your-pantheon-site/).

## Create a Sucuri Account

Get started by [selecting a plan](https://sucuri.net/website-firewall/signup) that fits your needs. Once a plan is selected, you will be instructed to create your Sucuri account and select a payment method.

![Sucuri sign up form](/source/docs/assets/images/sucuri-cloud-proxy-signup.png)​

## Login to your Sucuri Account

After receiving your confirmation email, sign in to your [Sucuri account](https://login.sucuri.net/login/). From within the Dashboard, click on **CloudProxy Website Firewall**.

![Sucuri Account Settings](/source/docs/assets/images/sucuri-account-settings.png)

## Add Your Site

Enter your domain and click **Add Site** to enable CloudProxy. You can add it with or without www, Sucuri will remove the www automatically.

![Sucuri Add Site](/source/docs/assets/images/sucuri-add-website.png)

## Verify Domain Name

You will see a pop-up that asks you to verify the domain name and server location. Pantheon sites are served from North America, but you can select a location that represents where you live.

Indicate whether you are currently under a DDoS attack or if you would like to restrict your site's backend to whitelisted IPs. When you are ready, click **Proceed**

![Sucuri Add New Domain](/source/docs/assets/images/sucuri-add-new-domain.png)

CloudProxy will display a status bar which will configure the account settings for your domain name. It should not take more than 1-2 minutes and will close automatically when finished.

![Sucuri CloudProxy Loading](/source/docs/assets/images/sucuri-cloud-proxy-loading.png)

## Activating CloudProxy / Setting up your DNS

You will want to copy the Firewall IP address which is located under the General Settings. This will be the record you will point to CloudProxy.

![Activating CloudProxy](/source/docs/assets/images/sucuri-cloudproxy-activating.png)

### Pointing to the correct records

Login to your domain registrar or DNS service, wherever your DNS records are managed. You will want to create **2 A records**.

<table class="table">
	<tbody>
			<tr>
        <th align="left" style="width: 130px">Host</th>
        <th align="left" style="width: 130px">Points To</th>
        <th align="left" style="width: 130px">TTL</th>
			</tr>
			<tr>
			</tr>
			<tr>
        <td align="left">@ or domain.com</td>
        <td align="left">192.237.224.60</td>
        <td align="left">600s or default</td>
			</tr>
      <tr>
        <td align="left">www</td>
        <td align="left">CloudProxy IP</td>
        <td align="left">600s or default</td>
			</tr>
			</tr>
	</tbody>
</table>

Here is an example:

![DNS A records](/source/docs/assets/images/sucuri-dns-a-records.png)

### Adding the Pantheon CNAME to Sucuri

Earlier on in the guide we removed the CNAME from the DNS records. Now, we are going to add it back to tell Sucuri where to route the "www" website traffic. After you have activated the CloudProxy you will see an area labeled **HOSTING IP ADDRESSES**, that is where you want to be.

In the IP field copy and paste the CNAME provided for your from the [Pantheon site dashboard](/source/docs/articles/sites/domains/dns-records-for-directing-your-domain-to-your-pantheon-site/#pantheon-dns-records-for-http-sites)

![Sucuri CloudProxy CNAME](/source/docs/assets/images/sucuri-cloud-proxy-cname-entry.png)

## Waiting for the site to propagate

Sucuri mentions on the site that it takes typically under an hour. I saw the changes to the domain around 10-15 minutes. Once the site is complete being setup through the CloudProxy you should be able to view your site and it's now protected!

![Sucuri CloudProxy Active Status](/source/docs/assets/images/sucuri-cloud-proxy-active-status.png)


![Sucuri CloudProxy Final](/source/docs/assets/images/sucuri-cloud-proxy-final.png)


## Congratulations!

You have now successfully integrated and protected your site from the forces of evil on the internet!

## See Also

- [CloudProxy Knowledge base on Sucuri](https://kb.sucuri.net/cloudproxy)
- [CloudProxy Intro Video](https://www.youtube.com/watch?v=MLhVsetSoxw)
- [Support Ticket Help for Sucuri](https://support.sucuri.net/support/?newcloudproxy)
- [Sucuri.net](https://sucuri.net/)
