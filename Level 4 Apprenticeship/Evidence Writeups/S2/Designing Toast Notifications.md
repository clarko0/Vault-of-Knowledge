
#### Arthur Clarkson
**20th September 2024**

On the intranet, we had an issue of display success/warning/error/information messages to users, in most cases we were either using a popup or a banner at the top of the page to display these.

Popups are good at letting the user know what they've done wrong, but are annoying because you have to click off them to fix the issue. Banners are a non-obtrusive way of getting a message across, but are fixed to the top of the page, leaving them unseen from lower down the page on longer forms.

After doing some research, the best way to get information across to the user was to use toast notifications.

After doing some thinking I had these thoughts in mind:
- We don't want to show too much information to the user, so I decided to limit the toast notifications to only one line.
- The best place to put them was in the centre bottom, with the newest notifications being closer to the bottom.
- Have a very simplistic colour pallet: red for errors, amber for warnings, green for success, and black for information.

With this in mind I came up with the following design in Figma:
![[Pasted image 20240920151058.png]]

After this I opened up the intranet in Firefox, took some screenshots of the website and overlayed the toast notifications, to see if they suited the intranet:
![[Pasted image 20240920151247.png]]

![[Pasted image 20240920151444.png]]

With me being happy with how they looked, I started to develop them.