---
title: "Automatically start a chatbot conversation"
description: "Configure your bot to start a conversation automatically, as soon as it's loaded"
keywords: "PVA"
ms.date: 01/25/2022

ms.topic: article
author: iaanw
ms.author: iawilt
ms.reviewer: digantak
manager: shellyha
ms.custom: "customization, ce06102020"
ms.collection: virtualagent
---

# Configure your bot to start the conversation automatically

Select the version of Power Virtual Agents you're using here:

> [!div class="op_single_selector"]
>
> - [Power Virtual Agents web app](configure-bot-greeting.md)
> - [Power Virtual Agents app in Microsoft Teams](teams/configure-bot-greeting-teams.md)

By default, chatbots created with Power Virtual Agents and [published to a website](publication-connect-bot-to-web-channels.md) will load without a greeting, and will passively wait for the user to start the conversation.

However, you can use custom CSS and JavaScript code to automatically have the bot start the conversation when the bot loads.

For example, you could have your bot say, "Hi, I'm Botty, a virtual agent" as soon as the bot loads.

First, you'll need to deploy a custom canvas that includes arguments that trigger the greeting. By default, the custom canvas calls the default system greeting topic. You can, however, create a new topic to be used as the greeting, although you will need to divert the default system greeting topic to a new topic.

You can also combine the customized greeting with [customization to the look and feel of the bot](customize-default-canvas.md).

> [!IMPORTANT]
> Having the bot start the conversation will show up in your [analytics](analytics-overview.md) and will increase your session count.
>
> If the user of your bot doesn't engage with the bot (for example, they load the page but don't ask the bot anything), the session will be [marked as an unengaged session](analytics-summary.md#engagement-over-time-chart).
>
> This might impact your analytics.

## Prerequisites

- [Learn more about what you can do with Power Virtual Agents](fundamentals-what-is-power-virtual-agents.md).

> [!IMPORTANT]
> You may install and use the sample code included in this documentation only for use with the Microsoft Power Virtual Agents product. The sample code is licensed "as is" and is excluded from any service level agreements or support services. You bear the risk of using it.  
>
> Microsoft gives no express warranties, guarantees, or conditions and excludes all implied warranties, including merchantability, fitness for a particular purpose, and non-infringement.

## Retrieve bot ID details

To customize the greeting, you need to know your Bot ID.

You can get the Bot ID by [going to the Mobile app under Channels](publication-connect-bot-to-custom-application.md#retrieve-your-power-virtual-agents-bot-parameters).

## Deploy a custom canvas for your bot

You'll need to deploy a custom canvas that includes arguments that cause the [default system greeting topic](authoring-create-edit-topics.md#use-system-and-sample-topics) to be displayed when the bot loads.

1. [Create and publish a bot](fundamentals-get-started.md).

1. Follow the steps to [Customize the default canvas](customize-default-canvas.md#customize-the-default-canvas-simple).
    

## Change the bot's default greeting

The code in the *index.html* file causes a topic to be called automatically when the bot is loaded. By default, it calls the system greeting topic. You can also create a new topic and divert the default system greeting topic to that new topic.

In both instances, you [make changes to the topic you want to call as you would normally](authoring-create-edit-topics.md).

If you modify or create a new greeting topic, it's a best practice to include some sort of identification that the user is talking to a bot (or "virtual agent"), so they don't think they're talking to a human.

We recommend you modify the system greeting topic so that you don't have to edit the *index.html* code.

### Modify the system greeting topic (recommended)

1. Select **Topics** on the side navigation pane, then select the **Greeting** topic row.

    :::image type="content" source="media/configure-bot-greeting/select-greeting-topic.png" alt-text="Screenshot of the Topics page, with the Greeting topic highlighted.":::

1. Edit the text inside the **Message** nodes. You can also [add or delete additional nodes](authoring-create-edit-topics.md#insert-nodes).

1. Select **Save**.

    :::image type="content" source="media/configure-bot-greeting/custom-greeting-message.png" alt-text="Screenshot of the system greeting topic showing the message nodes that can be edited." border="false":::

1. [**Publish** your bot](publication-fundamentals-publish-channels.md).

    :::image type="content" source="media/configure-bot-greeting/channel-publish-latest-content.png" alt-text="Publish latest bot content." border="false":::

You can now test your bot by going to the webpage where you deployed your bot's custom canvas. You'll see the bot start the conversation by automatically showing the greeting topic.

### Create a new user topic

> [!WARNING]
> Using a user topic to start a conversation will increase your [billed sessions](analytics-billed-sessions.md#definition-of-a-billed-session). A billed session is an interaction between a customer and a bot and represents one unit of consumption. The billed session begins when a user topic is triggered. For more information, see the topic [Analyze billed session information](analytics-billed-sessions.md).

1. Select **Topics** on the side pane.

1. Select **New topic**, and give it a name.

1. Add the text inside the **Message** node.

1. Select **Save** when you've finished editing the message.

1. Select **Topics** again on the side navigation pane, then select the **Greeting** topic row.

1. [Delete the message nodes](authoring-create-edit-topics.md#insert-nodes) on the **Greeting** topic.

1. To automatically divert the bot to a user topic, select **Add node** (**+**) to add a node, and then [Go to another topic](authoring-create-edit-topics.md#redirect-to-another-topic).

1. In the flyout menu, select the user topic you created above.

1. Select **Save** when you've finished editing the message.

1. [**Publish** your bot](publication-fundamentals-publish-channels.md).

You can now test your bot by going to the webpage where you deployed your bot's custom canvas. You'll see the bot start the conversation by automatically showing the new topic.

[!INCLUDE[footer-include](includes/footer-banner.md)]
