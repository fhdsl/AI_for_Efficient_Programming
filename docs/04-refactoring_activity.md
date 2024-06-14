



# Refactoring Code: Hands-On Exercise

Now it's your turn to try. 

## The Code

Let's say you are dusting off some code from your past (no judgment here). You were investigating tweets about [Mr. Trash Wheel](https://www.mrtrashwheel.com/), a beloved Baltimore-based contraption that filters trash out of the waterways.

**Note**: This code is just an example and was written strictly for educational purposes.


``` python
import tweepy
import pandas

# Enter your API keys and access tokens here
consumer_key = 'your_consumer_key'
consumer_secret = "your_consumer_secret"
access_token = 'your_access_token'
access_token_secret = 'your_access_token_secret'

# Authenticate with Twitter API
auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_token_secret)

# Search for tweets containing the search term
tweets = tweepy.Cursor(tweepy.API(auth).search_tweets, q="Mr. Trash Wheel", tweet_mode='extended').items(100)

# Create empty list to store tweet data
date_data = []
location_data = []
text_data = []

def get_tweet_length(tweet):
    # Return the length of the tweet text
    return len(tweet.full_text)

# Loop through each tweet and extract desired data
for tweet in tweets:
      date_info = {
        'date': tweet.created_at
    }
    date_data.append(date_info)

# Search for tweets containing the search term
tweets = tweepy.Cursor(tweepy.API(auth).search_tweets, q="Mr. Trash Wheel", tweet_mode='extended').items(100)

# Loop through each tweet and extract desired data
for tweet in tweets:
    location_info = {
        'location': tweet.user.location
    }
        location_data.append(location_info)
    
# Search for tweets containing the search term
tweets = tweepy.Cursor(tweepy.API(auth).search_tweets, q='Mr. Trash Wheel', tweet_mode='extended').items(100)
    
# Loop through each tweet and extract desired data
for tweet in tweets:
    text_info = {
        'text': tweet.full_text
    }
    text_data.append(text_info)

# Combine lists into a dictionary
data = {'date': date_data, 
  'location': location_data, 'text': text_data}

# Store results in pandas dataframe
df = pandas.DataFrame(data)

# Print dataframe
print(df)
```

## Questions

1. Create an AI prompt that fixes any formatting issues with the code that would cause it not to run.

1. Devise an AI prompt that removes any dead code from your sample above. What gets removed?

1. Create a prompt that makes the code less repetitive, adhering to the DRY principle. What aspect of the code was repetitive?

1. Construct a prompt that makes the code more concise. What are some trade-offs that appear in this code between readability and brevity?

