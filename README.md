# Covid19-hesitance-tweets
The repository contains tweet collections associated with vaccine hesitancy on Twitter. Tweet were collected by leveraging Twitter search API filtered using keywords.
## How to Hydrate
### Hydrating using Twarc (CLI)
Many thanks to Ed Summers (edsu) for writing this script that uses Twarc to hydrate all Tweet-IDs stored in their corresponding folders.

First install Twarc and tqdm

    pip3 install twarc
    pip3 install tqdm

Configure Twarc with your Twitter API tokens (note you must apply for a Twitter developer account first in order to obtain the needed tokens). You can also configure the API tokens in the script, if unable to configure through CLI.

    twarc configure
Run the script. The hydrated Tweets will be stored in the same folder as the Tweet-ID file, and is saved as a compressed jsonl file

    python3 hydrate.py -streaming
for hydrating the streaming collection or

    python3 hydrate.py -account
for hydrating the account collection

### Hydrating using Tweepy:
    import tweepy
    auth = tweepy.AppAuthHandler(consumer_key, consumer_secret)
    api = tweepy.API(auth, retry_count=5, retry_delay=2, wait_on_rate_limit=True, wait_on_rate_limit_notify=True)
    api.statuses_lookup(list_of_ids) #consider the limitations in tweepy documentation
