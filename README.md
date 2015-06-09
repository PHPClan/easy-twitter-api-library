#Easy Twitter API Library (PHP)

## Welcome!

You now hold in your hands the power to connect to the Twitter REST API with
ease and speed. It has been specifically designed to work with the new Twitter
1.1 API.

Let's get started!

### Using "Easy Twitter API" in your code
It's easy to add "Easy Twitter API". Here is how to do it:


	include 'easy-twitter-api.php';
	define ('TWITTER_CONSUMER_KEY', 'your API consumer key goes here');
	define ('TWITTER_CONSUMER_SECRET', 'your API consumer secret goes here');

	$twitter = new EasyTwitter(TWITTER_CONSUMER_KEY, TWITTER_CONSUMER_SECRET);

Please make sure you have included the "Easy Twitter API" library **before** you
continue to the steps below.

> **NOTE:** You can create a Twitter app, and get your API credentials [over
here](https://apps.twitter.com/).


### Adding your auth tokens

If you are simply using the API for your own calls, simply copy your auth token and secret and assign them like this:

	$twitter->access_token('your oauth access token goes here');
	$twitter->access_token_secret('your oauth access token secret goes here');
  
  
***  

* * *



## Making a **`GET`** request

The easiest way to make a `GET` request is like this:

	$response = $twitter->get($url);// Replace '$url' with the endpoint you want.

> **NOTE:** Please make sure you use the **full** URL for your desired endpoint.

For example, if you want to get the most recent tweets and retweets on the
timeline, here is what you do:

	$response = $twitter->get('https://api.twitter.com/1.1/statuses/home_timeline.json');

It's that simple!

##### `GET` request with parameters

In a similar way, you can simply use the `GET` request together with the query parameters in the URL. For example:

	$response = $twitter->get('https://api.twitter.com/1.1/search/tweets.json?q=london');

Alternatively, if you prefer you can use the `params` method. Let's take a look at an example:
	
	$params = array(

				"screen_name" => "twitter",
				"count" => 2

			);

	$twitter->params( $params );
	$response = $twitter->get('https://api.twitter.com/1.1/statuses/user_timeline.json');

> **IMPORTANT!** If you are using the `params` method makes sure you don't add the query parameters to the endpoint url. If
there are parameters in the url, they will override the parameters you provide to the `params` method.

  
  
***  

* * *

##Making a **`POST`** request

Again, your Easy Twitter API Library has been designed to make post request as
easy as possible.

Let's take a look!

In this example, we will post a new status to our Twitter timeline.

Here is what we do:
	
	//Assign the parameters of your request, using the params method:
    $params = array (

    		'status' => 'Welcome to my Twitter empire! Mwahahahahaha! ( also, I think Jenniffer Lawrance is hot, hot, hot!)'

    	);

    $twitter->params( $params );

  Now we will make our request:
  	//You MUST use the full URL of your desired endpoint
  	$url = "https://api.twitter.com/1.1/statuses/update.json"; 

  	$response = $twitter->post( $url );

  **That's it!** You just made a new status update on Twitter. `Sweet!`
  
  
***  

* * *

  ##Uploading media

  If you wish to upload media, the Easy Twitter API Library has you covered!

  Simply use the `media` method:


    $media_path = "/path/to/your/media";

    $response = $twitter->media( $media_path );

> **NOTE** You can choose to use either a `url` or a server `path` to your
desired media.

You can also send media using the binary format. All you have to do is set the
second parameter of the `media` method to `true`. Example:

	$media_path = "/path/to/your/media";

	$media_content = file_get_contents( $media_path );

	$response = $twitter->media( $media_content, true );



