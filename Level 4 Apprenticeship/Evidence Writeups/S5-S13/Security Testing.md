### Security Testing Holiday Creation

#### Arthur Clarkson
**4th September 2024**

Security testing is a process aimed at identifying vulnerabilities in an information system's security mechanisms, ensuring the system can safeguard data and maintain its intended functionality.

Following the user stories during from the analysis stage, these were the ones that were security related:
```
As an HR user, I am able to see the "Assign User" input.
As an HR user, I am able to create holiday entries for any user.

As a normal user, I am only able to create holiday entries for myself.
```

To test the security of holiday creation, I impersonated a "normal user" by making sure I didn't have the "HR" permission. After opening the holiday popup, I was unable to see the "Assign User" input:
![[Pasted image 20240904170249.png]]

I then attempted to send an HTTP POST to the `/Timesheet/CreateHolidayEntries` endpoint containing "userId: 2130" in the body, of which it returned a 401 (Unauthorized) HTTP status:
![[Pasted image 20240904170341.png]]

I then gave myself the "HR", causing me to impersonate an "HR user", re-opened the popup, and I was able to see the "Assign User" input:
![[Pasted image 20240904170528.png]]

Then testing the HTTP POST request, I was able to get a 200 (Success) HTTP response status:

![[Pasted image 20240904170718.png]]

These results concluded that my tests were successful, and the security was up to standards with the users stories.