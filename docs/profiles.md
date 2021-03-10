# Commands

#### /profile help
Shows all available commands available to the sender.

#### /profile set <field> <value>
Sets a field.

#### /profile show [user]
Show a user's profile.
- user (optional) - the user to show the profile for. Defaults to the sender.

#### /profile clear <field>
Clears a field.

#### /profile setother <user> <field> <value>
Sets a field for another user.
- Requires the permission profiles.moderator

#### /profile clearother <user> <field>
Clears a field for another user.
- Requires the permission profiles.moderator

#### /profile version
Shows the plugin's name, version, author, and LucyCommonLib version.

#### /profile reload
Reloads the config. Note that not all settings are reloaded by this command.
- Requires the permission profiles.admin


# Config file
### `checkForUpdates`

Whether to check for updates or not. I have no clue why you'd want to disable this. 

Default value: `true`
### `format`

#### `format.accent`
A [LucyCommonLib formatter](/commonlib/#setting-a-plugins-accent-colour) that formats accent text.

Default value: `'{#fa9efa>}%s{#9dacfa<}'`
#### `format.main`
A [LucyCommonLib formatter](/commonlib/#setting-a-plugins-accent-colour) that formats main text.

Default value: `'&f'`


### `fields`

This is where the real fun starts. Fields are what make up a profile. By default, there are four fields - name, gender,
pronouns, and discord. Of course, there's no need to keep these fields, you can set them to whatever you like!

#### Field properties
    fields:
        <unique field id>:
            type: <type>
            order: <position on the profile, lower numbers come first>
            displayName: <user-friendly display name>
- unique field id - this can be anything, as long as it's not used by any other field on the server. It'll be used in
  commands.
- type - the field type. See below for more details.
- order - an integer number that dictates in which position this field will be displayed. Lower numbers come first.
- displayName - a nice display name for the field. This will be shown in the /profile command.

#### Field types
- `simple` - a "typical" field. Users can set this using /profile set, it will show on their profile as you'd expect.
- `pronouns` (requires [ProNouns](https://lucyy.me/pronouns) to be installed) - shows a user's pronouns. Setting this
  with /profile set will cause a player's pronouns to update as if they set them through ProNouns.
- `placeholder` (requires [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) to be installed) -
  shows the value of a placeholder. These cannot be set using /profile set. To specify a placeholder to display,
  set the "format" property of the field, like so (this example shows a user's Vault prefix):
    
    	fields:
    		prefix:
    			type: placeholder
    			order: 0
    			displayName: Prefix
    			format: '%vault_prefix%'
    
**NOTE: if you're using PlaceholderAPI, you MUST wrap your format in quotes! This is due to a restriction of YAML.**

I do appreciate this is kinda complicated. If you'd like some help with it, feel free to join my support Discord server at https://support.lucyy.me. I'd love to help you!

# Developer API

Docs for the API aren't done yet, [join my discord server](https://support.lucyy.me) and I'll walk you through using it.
It can both interact with profile fields and create custom field types.
