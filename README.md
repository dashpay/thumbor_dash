# thumbor_dash
A thumbor server extension for DASH


## Setup

#### Requirements

- Python >= 3.9
- Pip >= 21.1

1. Install thumbor_dash

`pip install thumbor_dash`

Note: thumbor_dash, thumbor, and other required dependencies will be installed

2. Create a thumbor configuration file
  
`thumbor-config > thumbor.conf`

3. Add these lines to `thumbor.conf` file

```python
# Set allowed dimensions
MIN_WIDTH = 1
MIN_HEIGHT = 1
MAX_WIDTH = 1200
MAX_HEIGHT = 800

# Set security key
SECURITY_KEY = "0"
```

## Usage

1. Start thumbor_dash server

   `thumbor_dash --conf=thumbor.conf`

2. Sign image URL

   `thumbor_dash-url --key=<securityKey; must be "0"> --width=<width> --height=<height> --dashauth=<dashauth> --filters=<filters> <imageURL>`

output:

   `/<signature>/<width>x<height>/dashauth:requester(<requesterId>):contract(<contractId>):document(<documentType>):field(<field>):owner(<ownerId>):updatedAt(<updatedAt>)/filters:format(<format>)/<encodedImageUrl>`

3. Thumbor_dash image retrieval URL

   `http://<thumbor_dash-server>/<signature>/<width>x<height>/dashauth:requester(<requesterId>):contract(<contractId>):document(<documentType>):field(<field>):owner(<ownerId>):updatedAt(<updatedAt>)/filters:format(<format>)/<encodedImageUrl>`

   Note: If running the server locally, <thumbor_dash-server> should be `localhost:8888`


## Example

   `http://localhost:8888/Ai-ZyWWtJ0MHUQAm0GAlBTQMZ_Y=/1200x800/dashauth:requester(GCAFKUdw7PtUcDEG8j3sicMJ4ngx1aTqCdb4HD5n5WZ7):contract(En3GRoMNAnt69firp32h3NEBxyveLcHQMUbwhDW2UqoX):document(thumbnailField):field(avatarUrl):owner(GCAFKUdw7PtUcDEG8j3sicMJ4ngx1aTqCdb4HD5n5WZ7):updatedAt(1627076771396)/filters:format(jpeg)/https%3A//github.com/thumbor/thumbor/raw/master/example.jpg`



