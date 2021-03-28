# Commands

#### /pronouns help
Shows all available commands available to the sender.

#### /pronouns set &lt;set&gt; [set]...
Sets the sender's pronouns ([see below](#setting-your-pronouns)).

#### /pronouns show [user]
Shows a player's pronouns.

- user (optional) - the user to show pronouns for. Defaults to the sender.

#### /pronouns clear
Clears the sender's pronouns.

#### /pronouns list
Lists all predefined pronoun sets.

#### /pronouns preview
Sends a message to the sender, substituting their pronouns.

#### /pronouns version
Shows the plugin's name, version, author, and LucyCommonLib version.

#### /pronouns reload
Reloads the config. Note that not all settings are reloaded by this command.

- Requires the permission pronouns.admin

#### /pronouns sudo &lt;player&gt; &lt;subcommand&gt; [args]...
Executes a subcommand as another player.

- Requires the permission pronouns.admin
# Config file

### `accent`
A [LucyCommonLib formatter](/commonlib/#setting-a-plugins-accent-colour) that formats accent text.

Default value: `'{#fa9efa>}%s{#9dacfa<}'` (`'&d'` in version 1.0.4 and below)
### `main`
A [LucyCommonLib formatter](/commonlib/#setting-a-plugins-accent-colour) that formats main text.

Default value: `'&f'`

### `checkForUpdates`
Whether to check for updates or not. I'm not entirely sure why you'd want to disable this, but the
option's there if you want it.

Default value: `true`
 
### `connection`
How ProNouns should store data. There are two acceptable values for this:

- `'yml'` (default) - stores data in a file. Use this if you're not sure what to use.
- `'mysql'` stores data in a MySQL database. Suitable for BungeeCord servers.

### `mysql`
These values will be ignored if MySQL is not being used.

- `host` - default is `'127.0.0.1'`
- `port` - default is `3306`
- `database` - default is `pronouns`
- `username` - default is `pronouns`
- `password` - default is `password` (please don't use this as a password!)

### `predefinedSets`
Add extra pronoun sets to the predefined list. This means users can type out the set like they would
with the defaults (he/she/they). Default is `[]` (empty). Sets should be written out in the standard
full-set (6) format ([see below](#setting-your-pronouns)).

# Setting your pronouns
Pronoun sets can be specified in a number of formats.

- `they`
- `they/them`
- `she/they` (more sets can be chained like this)
- `they/them/they're/their/theirs/themself` - this is the "full format". This format will **always work** -
if you're using neopronouns and the admins haven't added your pronouns, this is how you do it!
  
# PlaceholderAPI
ProNouns provides some PlaceholderAPI placeholders. As of version 1.1.0, an eCloud expansion is needed to use them.
Install it with `/papi ecloud download pronouns` followed by `/papi reload`. 

- `%pronouns_pronouns%` - pronouns, in the Subjective/Objective format ie She/Her 
- `%pronouns_subjective%` - subjective pronoun
- `%pronouns_objective%` - objective pronoun
- `%pronouns_progressive%` - progressive pronoun
- `%pronouns_possessiveadj%` - possessive adjective
- `%pronouns_possessivepro%` - possessive pronoun
- `%pronouns_reflexive%` - reflexive pronouns
- `%pronouns_all%` - all 6 pronouns

All placeholders also have some formatting modifiers that can be added to the end of the name to control capitalisation:

- upper - uppercase (SHE)
- lower - lowercase (she)
- capital - first letter uppercase, everything else lowercase (She)

Some examples using the she/her pronoun set:

- `%pronouns_subjective_upper%` - SHE
- `%pronoun_possessivepro_capital%` - Hers

# Developer API
![](https://img.shields.io/nexus/r/me.lucyy/pronouns-api?label=version&server=https://repo.lucyy.me&color=#fd0)

<https://javadoc.lucyy.me/pronouns/latest>

ProNouns exposes an API for Java plugin developers to use. Versioning works slightly differently for the API - the major and minor versions must match the plugin versions. For example, API v1.0 works on 1.0.0-RC1, 1.0.0, 1.0.5 etc, but not 1.5.x.

## Including

Include with Maven as follows:

```xml
<repositories>
    ...
    <repository>
        <id>lucy</id>
        <url>https://repo.lucyy.me/repository/public/</url>
    </repository>
    ...
</repositories>

<dependencies>
    ...
    <dependency>
        <groupId>me.lucyy</groupId>
        <artifactId>pronouns-api</artifactId>
        <version><VERSION></version>
        <scope>provided</scope>
    </dependency>
    ...
</dependencies>
```

Or with Gradle:

```kotlin
repositories {
	maven { url "https://repo.lucyy.me/repository/public/" }
}

dependencies {
	compileOnly 'me.lucyy:pronouns-api:VERSION'
}
```

## Getting an instance

Get an instance of `PronounHandler` using the `RegisteredServiceProvider`:

```java
RegisteredServiceProvider<PronounHandler> rsp = getServer().getServicesManager().getRegistration(PronounHandler.class);
PronounHandler handler = rsp.getProvider();
```
