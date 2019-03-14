# API Examples

The files contained in this repo demonstrate how to connect to the Uber API and Zomato API using JQuery and AJAX.  It goes without saying that these are not good examples of production implementation since your API Key(s) would be available in plain sight to anyone interested enough to snoop.  The solutions here are provided as academic examples and should be regarded as such.   

# Zomato (zomato-api.html)

This is a pretty vanilla AJAX request however the piece that we never went over in class was the concept of HTTP headers which both of the APIs in this repo use. The key to making this API work is the following line

```sh
xhr.setRequestHeader('user-key', '<YOUR API KEY>');
```

This is not disimilar from the examples we saw in class where the API key was passed along in the query string it is just a different way to pass the key to the server. 

# Uber (uber-api.html)
Uber's API is much more sophisticated than Zomato's so for the purposes of this example I am assuming you only want to make general API calls (e.g. price estimates to & from a given set of coords) instead of making requests to Uber on behalf of a given user.  Like Zomato the key to getting Uber's API to work is to pass a value along in the HTTP Header like so

```sh
xhr.setRequestHeader('Authorization', 'Token <YOUR API KEY>');
```
Unfortunately this is only part of the problem working with Uber.  If you try to make a call directly to Uber's API with your API Key it will fail due to CORS. 

### Heroku to the rescue!
[CORS Anywhere] is an application that I found that basically allows you to get around the CORS problem in general, not just for Uber. You can navigate to the [CORS Anywhere] site and read the documentation on how it works, however to get things to work properly it basically boils down to concatenating the [CORS Anywhere] URL together with the Uber URL.

# With great power...
...we have all seen / read Spider-man so I will spare you the line.  That being said nothing shown here is an acceptable approach to production implementations. In fact some APIs may forbid you from working with them in this manner via statements in their development documentation. Be mindful of your code and the unintended consequences you might have to face (your API access being turned off perhaps).

[CORS Anywhere]: <https://cors-anywhere.herokuapp.com/>
