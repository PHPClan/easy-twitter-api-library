### Get available trends

The `trends/available` trend returns location for which Twitter has trending
topic information for.

You check it out in the official documentation [here](https://dev.twitter.com/rest/reference/get/trends/available).

Now, let's get to it!

#### Step 1

Let's include our Easy Twitter API library:

	include 'easy-twitter-api.php';
	define ('TWITTER_CONSUMER_KEY', 'your API consumer key goes here');
	define ('TWITTER_CONSUMER_SECRET', 'your API consumer secret goes here');

	$twitter = new EasyTwitter(TWITTER_CONSUMER_KEY, TWITTER_CONSUMER_SECRET);


#### Step 2

Now, we add your access token, and your access secret:


	$twitter->access_token('your oauth access token goes here');
	$twitter->access_token_secret('your oauth access token secret goes here');

#### Step 3

Finally, we will get our available trends locations!

	$url = "https://api.twitter.com/1.1/trends/available.json";

	$available_trends = $twitter->get($url);

**That's it!**


