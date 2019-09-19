---
title: Send custom notifications to users with Microsoft Intune 
titleSuffix: Microsoft Intune
description: Use Intune to create and send custom push notifications to users of iOS and Android devices
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure

ms.collection: M365-identity-device-management
---

# Send custom notifications in Intune  

Use Microsoft Intune to send custom notifications to the users of managed iOS and Android devices. These messages appear as standard push notifications from the Company Portal app and from the Microsoft Intune app on a user’s device, just as notifications from other applications on the device appear. Intune custom notifications aren’t supported by Windows devices.   

Custom notification messages include a short title and a message body of 500 characters or less. These messages can be customized for any general communication purpose.

## Common scenarios for sending custom notifications  

- Use custom notifications to alert specific users that a new app is available in the Company Portal.  
- Notify all employees of a change in schedule, such as building closures due to inclement weather.  

## Considerations for using custom notifications  

**Device configuration**:  
- Devices must have the Company Portal app or the Microsoft Intune app installed before users can receive custom notifications. They must also have configured permissions to allow the Company Portal app or the Microsoft Intune app to send push notifications. If needed, the Company Portal app and the Microsoft Intune app may prompt users to permit notifications.  
- On Android, Google Play Services is a required dependency.  
- The device must be MDM enrolled.

**Creating notifications**:  
- To create a message, use an account that is assigned an Intune role that includes the **Update** permission for **Organization**. To assign permissions to a user, see [Role assignments](role-based-access-control.md#role-assignments)  
- Custom notifications are limited to 50-character titles and 500-character messages.  
- Intune doesn’t save sent messages. To resend a message, you must recreate that message.  
- You can only send up to 25 messages per hour. This restriction is at the tenant level.  
- Each notification can directly target up to 25 groups. Nested groups don't count against this total.  
- Groups can include users or devices, but messages are sent only to users, and are sent to each iOS or Android device that the user has registered.  

**Delivery**:  
- Intune sends messages to the users' Company Portal app or the Microsoft Intune app, which then creates the push notification. Users don't need to be signed into the app for the notification to be pushed on the device.  
- Intune, as well as the Company Portal app and the Microsoft Intune app, can’t guarantee delivery of a custom notification. Custom notifications might show up after several hours of delay, if at all, so they shouldn't be used for urgent messages.  
- Custom notification messages from Intune appear on devices as standard push notifications. If the Company Portal app is open on an iOS device when it receives the notification, the notification displays in the app instead of being a push notification.  
- Custom notifications can be visible on lock screens on both iOS and Android devices depending on device settings.  
- On Android devices, other apps might have access to the data in your custom notifications. Don't use them for sensitive communications.  
- Users of a device that was recently unenrolled, or users that were removed from a group, might still receive a custom notification that is subsequently sent to that group.  Likewise, if you add a user to a group after a custom notification is sent to the group, it's possible for the newly added use to receive that previously sent notification message.  

## Send a custom notification  

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) with an account that has permissions to create and send notifications, and go to **Devices** > **Send custom notifications**.  

2. On the Basics tab, specify the following, and then select **Next** to continue.  
   - **Title** – Specify a title for this notification. Titles are limited to 50 characters.  
   - **Body** – Specify the message. Messages are limited to 500 character

   ![Create a custom notification](./media/custom-notifications/custom-notifications.png)  

3. On the **Assignments** tab, select the groups to which you’d like to send this custom notification, and then select Next to continue.  

4. On the **Review + Create** tab, review the information and when ready to send the notification, select **Create**.  

Intune processes messages that you create immediately. The only confirmation that the message was sent is the Intune notification that confirms that the custom notification was sent.  

![Confirmation of a sent notification](./media/custom-notifications/notification-sent.png)  

Intune doesn’t track the custom notifications you send, and devices don’t log the receipt outside of the device’s notification center.  

## Receive a custom notification  

On a device, users see custom notification messages that are sent by Intune as a standard push notification from the Company Portal app or the Microsoft Intune app. These notifications are similar to the push notifications users receive from other apps on the device.  

On iOS devices, if the Company Portal app is open when the notification is received, the notification displays in the app instead of being a push notification.  

The notification remains until the user dismisses it.  

## Next steps  
[Manage devices](device-management.md)
