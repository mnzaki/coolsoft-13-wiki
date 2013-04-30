1. Add CoolsterPusher class inside the controller of the action that needs instant updating.  
2. Define methods that set changes to be sent to Coolster to be updated instantly  
3. On change call the appropriate method from the defined methods  
  
```sh 
class CoolsterPusher < AbstractCoolsterPusher  
    # define method that uses:  
    # Coolster.update('list of user ids as strings', 'script')  
    # or Coolster.update_all('script')  
    # or Coolster.update_each('list of user ids as strings', 'block')  
    # to push changes to users online    
 end   
```
**Example:**  
In notifications_controller:
```sh
class CoolsterPusher < AbstractCoolsterPusher

    def push_notification(user_ids, notification)
      Coolster.update_each(user_ids) do |user_id|
        count = User.find(user_id).unread_notifications_count
        render 'notifications/add_notification',
              locals: { notification: notification, read: false, count: count}
      end
    end

end
```  
 [View controllor](https://github.com/DevYah/coolsoft-13/blob/C1_AminaZoheir_%23226_PollingFramework/Idearator/app/controllers/notifications_controller.rb)  

Then in the send_notification method in notification controller:  
```sh
 def self.send_notification (user_sender, idea, users_receivers)
    vote_notification = VoteNotification.create(user: user_sender, idea: idea, users: users_receivers)
    user_ids = []
    users_receivers.each do |user|
      user_ids << user.id.to_s
    end
    NotificationsController::CoolsterPusher.new.push_notification user_ids, vote_notification
  end
```  
[View model](https://github.com/DevYah/coolsoft-13/blob/C1_AminaZoheir_%23226_PollingFramework/Idearator/app/models/vote_notification.rb)