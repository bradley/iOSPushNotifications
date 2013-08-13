Recieves Push Notifications
===========
This project will, once allowed, recieve push notifications from the server.

It's pretty rudimentary. When the app is started, and the user accepts to recieve
notifications, the app will log the user's token to be used by APNS. 

Note: The app does not, as it is, pass up the token to the server. This project simply
shows what is necessary setup a Rails server to send notifications, and what is necessary
to setup an iOS app to recieve them. Therfore, sending notifications must be done manually.

The server app is 'setup' for our UrbanAirship account already and push notifications
can be sent from the rails console using the token returned in step described above.

*However*, it's easier to test push notifications from the UrbanAirship admin panel. To
do so, just go to the app in the panel, select 'Messages' from the sidebar, Select the 
'Test Push'	option, and construct your push notification.

In any case, this is how you construct a push notification from the console:
```
@notification = {:schedule_for => [Time.now], :device_tokens => ["aaaa1111bbbb2222cccc3333dddd4444eeee5555"], "aps" => {"alert" => "Hey you!", "badge" => "3"}}

Urbanairship.push(@notification)
```

##Things to Try

> Send yourself a push notification when the app is closed (not in background state) and open it from the notification alert.
> Send yourself a push notification when the app is opened.
> Send yourself a push notification when the app is in the background state and open it from the notification alert.


##Troubleshooting

Q. The badge is updating but I am not seeing the alert message component of the notification
A. Should you find a reason to delete the app, and find yourself no longer recieving the
alert message component of a push notification (Note: you can only ever see this if the
app is closed or in the background state), try going into your general settings and 
resetting the device settings.

Q. I am not seeing any log messages.
A. In the scheme for the project (in Xcode), the app is likely set to launch setting
   is likely set to wait for the app to be launched manually. This is good because you 
   can test the reception of push notifications on a closed app. To view the log, go to 
   organizer > the device name > console.

Q. How do I test push notifications on a closed app when running through Xcode?
A. Read the answer above.

