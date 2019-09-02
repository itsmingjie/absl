# AirTable Based Link Shortener

## Setup

Please make sure your AirTable is setup exactly like the one in the following screenshot:
![Airtable Setup](docs/airtable_setup.png)

Please also grab the AirTable API Key & Base Key from the API documentations. Head [here](https://airtable.com/api) and click on the base you just created to get started.

Set `AIRTABLE_BASE` to your Base Key, and `AIRTABLE_KEY` to your API Key.
Set `APP_USER` to your desired username.
Set `APP_SECRET` to a passphrase or key that only you know.

## Using

All links will be routed through a 302 (Temporary Redirect) because you're using AirTable. Simply visit `example.com/slug` to get redirected.

Navigate to `/admin` for a GUI to add new links.

## Using the API

You can make changes the database easily with the API.

### `/api/trace`
Find where a slug points to without getting redirected.

#### Parameters
* `slug` (required) - the slug you're looking up.

#### Result
* `dest` - the destination URL.
* `error` - the error message, if exists.
* `status` - status code of the request

### `/api/push`
Make changes to a specific record.

#### Parameters
* `auth` (required) - the `APP_SECRET` environment variable, used for authentication.
* `dest` (optional) - the destination URL you're pointing to. Must exist if `slug` does not exist.
* `slug` (optional) - the slug you're making changes to. If it does not exist, a random slug will be generated. Must exist if `dest` does not exist.

#### Result
* `error` - the error message, if exists.
* `slug` - the slug of the short link, if generated
* `status` - status code of the request

## License

ABLS is released under [the MIT license](LICENSE).