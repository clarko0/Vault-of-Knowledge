### Non-Functional Testing During Development

#### Arthur Clarkson
**4th September 2024**

Error handling was outside of the functional specification, and is brought down to the developer to implement and test - meaning that it had to be non-functionally tested. I tried multiple UI components to show the exception returned from the server, such as an banners at the top of the holiday entry form, popups, and toast notifications. 

Toast notifications were the best pick, due to them being more visible than a banner, and not being as obtrusive as popups. The API returns an exception if the user gives no days to add as holiday, this is caused by this bit of code:

```cs
public void CreateHolidayEntriesForUser(List<HolidayEntryItem> holidayEntries, int userId)
{
	// Start of CreateHolidayEntriesForUser...
	
	bool noHolidayEntires = holidayEntries.Count == 0;
	if (noHolidayEntires)
	{
		throw new Exception("No holiday entries given");
	}
	  
	// Rest of CreateHolidayEntriesForUser...
}

```

To test that the toast notifications are working, I pressed the "Enter Holiday" without any holidays selected:

![[Pasted image 20240904152631.png]]
With the toast notification being displayed with the exception message thrown in the API's business method, this non-functional test is considered a success.