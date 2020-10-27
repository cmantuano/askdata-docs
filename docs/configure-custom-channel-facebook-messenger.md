---
title: Configure custom channel: Facebook Messenger
keywords: documentation
last_updated: October 15th, 2020
tags: [getting_started]
sidebar: mydoc_sidebar
layout: doc

---

Configuration process:

Open the Askdata Console and select one Askdata agent.

If you are the editor the agent you will be able to open the agent in edit mode.

Show the “Advanced settings” at the end of the page.

Click on the [+] button close to the Channels section.

This is a handy guide that explains how to configure your agent to work with your page of Facebook Messenger.

Create a Facebook Page

Go to this website:

<https://www.facebook.com/pages/creation/>

Create Page on **Facebook Platform**, simply specifying its category

Select the requires options and then fill the page name and the category that describes it.

The page has been created.

Add Send Message button and then click Save Create a Facebook APP

Go To <https://developers.facebook.com/>

Add new App

Create App ID

Setup the Webhook.

Select the “Page” option and fill the Callback URL and the Verify token. Both these parameters will be provided by Askdata platform (next paragraph).

Press Verify and Save button

In the Webhook section, select the following events: messages, messaging\_postbacks, messaging\_optins, messaging\_account\_linking

Go to Messenger section on the sidebar

Select the Facebook Page among the list of ones the user owns. The page will be associated to the App ID and the page access token will be generated.

The token has to be inserted in the Application Token field of the Facebook channel on the Askdata Platform.

Select the same Facebook Page on the list

From now on you can use the agent created through the Askdata platform as a chat to that Facebook page

In order to allow users to test the agent, it is needed to set their role. From the sidebar, go to Roles.

Press Add Testers Button and provide the name, the fbId or username of the person to add.

Configure a new channel on Askdata

Login at Askdata platform

Go to the Agents section and click on the agent to whom you want to create a custom Facebook Messenger page

Clieck on the [+] button close to the channel section on the left menu and then choose Facebook

Automatically the webhook and verify token to insert on Facebook Developer Edit Page Subscription will be provided.

The token got on Facebook Developer Has to be inserted on Application Token field and Save.

The agent will be added to the contact and you can start using the service.

Start using the agent

You can now open your **Facebook Messenger** app and chat with the Askdata agent

‍



    {% include links.html %}

    