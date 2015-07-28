---
title: Using Sucuri Cloud Proxy with WordPress and Drupal
description: Detailed information on using Sucuri Cloud Proxy to protect against malware, hackers, and blacklists.
category:
  - developing
authors:
  - atjuch
date: 7/28/2015
---
Blocking hackers, DDOS attacks, malware, and blacklists is becoming a necessity on the internet nowadays and the attacks have increased in popularity. The ease of deployment and effectiveness allows the attacker to do little in order to cause harm to your website. The end goal of setting up a Cloud Proxy is to protect your website and not allow it to go off-line by staying ahead of the attackers.

## Why Sucuri?

[Sucuri](https://sucuri.net) is one of the leading website security companies in the world. They offer a variety of paid and online tools ranging from [Website AntiVirus](https://sucuri.net/website-antivirus/), [Cloud Proxy (Firewall)](https://sucuri.net/website-firewall/), [Free Website Security Scan](https://sitecheck.sucuri.net/), and more.

For basic and enterprise clients, you can find a solution that will work for you. They also have 24/7 support via tickets and their response time is incredible. No matter what type of security you need, Sucuri has you protected!

## Prerequisites

### 1. Setup Your DNS with Pantheon
Before you can have Sucuri add a Cloud Proxy it needs to have an DNS records to scan from. Make sure you have your domain name pointed at [Pantheon's DNS before you start](/source/docs/articles/sites/domains/dns-records-for-directing-your-domain-to-your-pantheon-site/).

## Create a Sucuri Account

Get started by [signing up](https://sucuri.net/website-firewall/signup) for a service level plan that meets your website needs. They offer a 30 day money back guarantee so if you do not like the service or it doesn't work for your site, simply ask for a refund. They [several different plans](https://sucuri.net/website-firewall/signup) to help fit your business.

![Sucuri sign up form](/source/docs/assets/images/sucuri-cloud-proxy-signup.png)​

## Login to your Sucuri Account

After receiving your confirmation email, sign in to your [Sucuri account](https://login.sucuri.net/login/). From within the Dashboard, click on **CloudProxy Website Firewall** located on the left menu.

![Sucuri Account Settings](/source/docs/assets/images/sucuri-account-settings.png)

## Add Your Site

Next you will add your website domain name. You can add it with or without the "www", Sucuri will remove the www automatically. Once you have typed in your domain, click **Add Site**.

![Sucuri Add Site](/source/docs/assets/images/securi-add-website.png)

## Verify Domain Name

You will see a pop-up that asks you to verify the domain name and the server location. Since Pantheon is in North America I chose that but you can select a location that represents where you live.

Answer the two questions that it's asking, typically you can leave these blank unless they apply to your website. When you are ready, click **Proceed**

![Sucuri Add New Domain](/source/docs/assets/images/sucuri-add-new-domain.png)

CloudProxy will display a status bar which will configure the account settings for your domain name. It should not take more than 1-2 minutes and will close the status bar automatically when finished.

![Sucuri CloudProxy Loading](/source/docs/assets/images/sucuri-cloud-proxy-loading.png)

## Activating CloudProxy

When the status bar is done, you will see a long page of information. You will want to scroll down until you see the blue area labeled **Activating CloudProxy**. This is where you will follow the instructions to enable CloudProxy.

1. First, check the URL provided and verify your site loads on the temporary address.
2. Second, if you need SSL support click the link provided for further instructions.
3. Login to where your DNS settings are for your domain name and remove the records you received from Pantheon. Add just an **A Record** to the IP address Sucuri lists. Save your DNS settings and come back to your Sucuri dashboard screen.
4. The domain name is now propagating, let's move on.

![Sucuri CloudProxy Activation](/source/docs/assets/images/sucuri-cloud-proxy-activating.png)

## Adding the Pantheon CNAME to Sucuri

Earlier on in the guide we removed the CNAME from the DNS records. Now, we are going to add it back to tell Securi where to route the "www" website traffic. After you have activated the CloudProxy you will see an area labeled **HOSTING IP ADDRESSES**, that is where you want to be.

In the IP field copy and paste the CNAME provided for your from the [Pantheon site dashboard](/source/docs/articles/sites/domains/dns-records-for-directing-your-domain-to-your-pantheon-site/#pantheon-dns-records-for-http-sites)

![Sucuri CloudProxy CNAME](/source/docs/assets/images/sucuri-cloud-proxy-cname.png)

## Waiting for the site to propagate

Sucuri mentions on the site that it takes typically under an hour. I saw the changes to the domain around 10-15 minutes. Once the site is complete being setup through the CloudProxy you should be able to view your site and it's now protected!

![Sucuri CloudProxy Active Status](/source/docs/assets/images/sucuri-cloud-proxy-active-status.png)


![Sucuri CloudProxy Final](/source/docs/assets/images/sucuri-cloud-proxy-final.png)


## Congratulations!

You have now successfully integrated and protected your site from the forces of evil on the internet!

## Resources

- [CloudProxy Knowledge base on Sucuri](https://kb.sucuri.net/cloudproxy)
- [CloudProxy Intro Video](https://www.youtube.com/watch?v=MLhVsetSoxw)
- [Support Ticket Help for Sucuri](https://support.sucuri.net/support/?newcloudproxy)
- [Sucuri.net](https://sucuri.net/)
