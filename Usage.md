Getting Started with ClientSuccess Usage Tracking
===================

ClientSuccess uses event/usage information to provide CSMs and Account Managers with views and insights into customer health.  This helps CSMs prioritize their time and act proactively to reduce customer churn.

We currently support two ways of sending event data into ClientSuccess:
> 1. Server-Side API
> 2. JavaScript Tracking Library

----------

###Server-Side API

You can send event information using simple `GET` requests.  Documentation for the server-side API can be found at [ClientSuccess Usage API Docs](http://docs.clientsuccessusage.apiary.io/).

----------

###JavaScript Tracking Library

####Quick Start

1. Include the `csTrack.js` library on your page.
	```
	<script src="//cdn.clientsuccess.com/csTrack.min.js"></script>
	```

2. Initialize the CSTrack library.
	```
	window.csTrack = new CSTrack('YOUR_PROJECT_ID', 'YOUR_API_KEY');
	
	// Add identification
	window.csTrack.identify({
	    organization: {
	        id: 12345,                      // REQUIRED     A unique identifier for the organization (may be string or number)
	        name: 'Widget Factory'          // REQUIRED     A human readable name for the organization.
	    },
	    user: {
	        id: 456789,                     // OPTIONAL     A unique identifier for the user (may be the user's email address)
	        name: 'Bob Jones',              // OPTIONAL     The logged in user’s name
	        email: 'bob@widgetfactory.com'  // OPTIONAL     The logged in user’s email address
	    }
	});
	```
	NOTE: Users of ClientSuccess can get the PROJECT_ID and API_KEY from the [ClientSuccess settings page](https://app.clientsuccess.com/cs/settings/usage)

3. Track event.
	```
	window.csTrack.trackEvent(eventName, aggregatedNumericValue /* optional */);
	
	// Example:
	window.csTrack.trackEvent('pageview');
	// OR
	window.csTrack.trackEvent('subscription renewed', 1299.95);
	```
	NOTE: The ```aggregatedNumericValue``` is OPTIONAL, but if used, it MUST be a number. This replaces the default value of 1 and will be aggregated within ClientSuccess. Example use-cases include: Tracking multiple events using a single tracking call, or Tracking monetary values associated with events.
