# Honeywell-Lyric
Honeywell Lyric for Home Assistant

I take no responsibility for this working or messing up anything with your furnace or thermostats. This is experimental.

This builds on the code of previous iterations, and adds a working config flow to Home Assistant. This is working as of 8/2/2020.

Note: the API has changed since last working, so if you had this installed before, you will need to change the API at Honeywell developers. See instructions below.


    Visit Honeywell Developers, and sign in. Create an account if you don’t have one already.
    Fill in account details.
    Submit changes
    Click “My Apps” at top of page, under your account.
    Click “Create New App”
    Fill in details:
    App name. Can be anything, I use Home Assistant.
    In the “Callback URL” enter the adress to your Home Assistant instance: “https://yourhomeassistant:8123/auth/lyric/callback”. 
    It is set up to use your external url in Home Assistant, so use that as your address (not the IP address)
    Click “Save Changes”
    On the apps page, click on the just created app.
    The “Consumer Key” and “Consumer Secret” are shown now. These will be used as client_id and client_secret below.


This is based on four great libraries that unfortunately appear to be abandoned, buggy, and no longer work:

* https://github.com/home-assistant/core/tree/92082b687a46c17a9a94a598b245728a8832b179/homeassistant/components/lyric
* https://github.com/shellster/lyric
* https://github.com/bramkragten/python-lyric
* https://github.com/bramkragten/lyric

This will give support for the Honeywell Lyric thermostats in Home Assistant.

Once you install the custom component, navigate to Configuration-->Integrations and find "Honeywell Lyric". Once you add the integration, a configurator will pop up asking you to log into your Lyric account.

### Configuration
```yaml
# Example configuration.yaml entry
lyric:
  client_id: CLIENT_ID
  client_secret: CLIENT_SECRET
```

```yaml
# Example configuration.yaml entry to show only devices at your vacation and primary homes
lyric:
  client_id: CLIENT_ID
  client_secret: CLIENT_SECRET
  locations:
    - Vacation
    - Primary
```

Configuration variables:

- *client_id* (Required): Your Lyric developer client id.
- *client_secret* (Required): Your Lyric developer client secret.
- *locations* (Optional): The location or locations you would like to include devices from. If not specified, this will include all locations in your Lyric account.
