### Description:
There is a separate class for each notification type. Each class has a method `send_notification`.  
There are two major classes which all other class inherit from.  
*  **IdeaNotifications:** *for all idea related notifications.*
    1. VoteNotification
    2. CommentNotification
    3. DeleteNotification
    4. EditNotification
    5. ArchiveNotification
    6. DisapproveIdeaNotification   
 
    
*  **UserNotifications:** *for all user related notifications.*
    1. InviteCommitteNotification
    2. ApproveCommitteeNotification   
 
### How to send notification:  
1. IdeaNotifications:
    use `class.send_notification(user_sender, idea, users_receivers)`.  
2. UserNotifications:
    use `class.send_notification(user_sender, users_receivers)`.   
  
  `user_sender` is a User instance, the one who caused the notification.   
  `users_receivers` is an array of User objects that are supposed to receive this notification.  
  `idea` is an Idea instance, the related idea.  
  
###Examples:   
1. User1 commented on user2's idea idea1:  
`CommentNotification.send_notification(User.find(1), Idea.find(1), [User.find(2)])`

2. User2 edited his idea idea1 and user1, user3 had commented/voted:
`EditNotification.send_notification(User.find(2), Idea.find(1), [User.find(1), User.find(3)])`

3. Admin invited user2 and user 3 to become committe members, user4 is an admin:
`InviteCommitteeNotification.send_notification(User.find(4), [User.find(2), User.find(3)])`

4. User3 signed up as committee and user4, user5 are admins:
`ApproveCommitteeNotification.send_notification(User.find(3), [User.find(4), User.find(5)])`

  