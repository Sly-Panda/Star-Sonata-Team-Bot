# Star Sonata Team Bot

A Star Sonata 2 bot bridging in-game chats and Discord, delivering real-time alerts (Attacks, Constructions, Termites, Low Fusions and more) and commands to improve quality of life both ingame and through discord.

## Table of Contents

* [Description](#description)
* [Installation](#installation)
* [Usage](#usage)
* [Config](#config)
* [Required Settings](#required-settings)
* [Commands](#commands)
* [Contributing](#contributing)
* [License](#license)

## Description

The Star Sonata 2 Bot is designed to make life in SS easier. It integrates your in-game chat with your Discord server, providing real-time alerts, useful commands, and other quality-of-life features.

**Key Features**

Real-time Alerts: Stay informed with instant Discord notifications for in-game events:

Attack Alerts: Get notified about attacks on your bases or fleets.
Team Updates: Track changes in your team roster, including joins, leaves, promotions, and demotions.
Base Management: Get alerted when construction runs out of commodities or galaxies are low on fusion cells.
Discord Commands: Access a variety of helpful commands directly within Discord to perform tasks such as:

Calculate fusion times, augment stats, manhours, and build savings
Manage galaxies and owners
Display DG and Uber locations
Manage your squad and character ownership information
Additional Features (Optional):

Relay in-game chats to Discord and vice-versa
Manage a standing team fleet
Access certain bot commands within the Star Sonata 2 game itself.

**Customization: The bot is highly customizable, allowing you to enable or disable most commands and functions in the config file to suit your team's needs.**

## Installation

1. Prerequisites

.NET 8.0: The bot requires .NET 8.0 to run. 
Download and install it from the official Microsoft website: https://dotnet.microsoft.com/download/dotnet/8.0

2. Create a Discord Bot

- Go to the Discord Developer Portal
- Create a new application and give it a name (e.g., "Star Sonata 2 Bot").
- In your application, navigate to the "Bot" section and click "Add Bot".

**In the "Bot" settings enable the following intents:**

- Presence Intent
- Server Members Intent
- Message Content Intent
- Copy the bot's token. You'll need this for the configuration file later.

3. Generate an Invite Link

- In your Discord application, go to the "OAuth2" section.
- In the "URL Generator" tab, select "Bot" under "SCOPES".

**Under "BOT PERMISSIONS", enable the following:**

- View Channels
- Read Message History
- Manage Messages
- Send Messages
- Use Slash Commands

Copy the generated invite URL at the bottom of the page.

4. Invite the Bot to Your Server

**Paste the invite URL into your web browser and follow the prompts to add the bot to your desired Discord server.**

5. Configure the Bot

- Once the bot is on your server, right-click on its profile and select "Copy ID".
- Open the StarSonataInfo.json configuration file.
- Paste the bot's ID into the "BotDiscordId" field.

**Fill in the rest of the configuration options based on your preferences and which features you want to use. See the detailed configuration section below for explanations of each option.**

6. Run the Bot

Once the configuration is complete, you can run the bot by running the included StarSonataTeamBot.exe or using the following command in your terminal or command prompt:

Bash
dotnet StarSonataTeamBot.dll

Next Steps:

**After the bot is running, you can use the slash commands within Discord to interact with it and access its features. Refer to the "Commands" section below for a list of available commands and their descriptions.**

## Config

The StarSonataInfo.json file allows you to customize various aspects of the bot's behavior and features.

## Required Settings

* "ServerUrl": The URL of the Star Sonata 2 server you play on (e.g., "liberty.starsonata.com").
* "BotDiscordId": The Discord ID of your bot. You can obtain this by right-clicking on the bot's profile in Discord after inviting it to your server.
* "DiscordToken": Your Discord bot's token. You can find this in the "Bot" section of your Discord application in the Developer Portal.
* "GameUsername": Your Star Sonata 2 username for the bot account.
* "GamePassword": Your Star Sonata 2 password for the bot account.
* "CharacterName": The name of the in-game character you want the bot to log in as.

**Optional Settings**

* "ReconnectDelay": The number of minutes the bot should wait before attempting to reconnect to the game server if it gets disconnected (default: 1).
* "DiscordAdminUsers": An array of Discord user IDs who have admin privileges for certain bot commands (e.g., /clear).
* "RelayChats": Enable or disable relaying in-game chats (Team, Trade, All) to specified Discord channels (default: true).
* "AutoReconnect": Enable or disable automatic reconnection to the game server if the bot gets disconnected (default: true).
* "EnableStandingFleet": Enable or disable the standing fleet management features (default: true).
* "FleetAlertsChannel": The Discord channel ID where fleet alerts (e.g., fleet creation, kicks) will be sent.
* "CreateFleetCommand": The in-game chat command to create a new standing fleet (default: !newfleet).
* "JoinFleetCommand": The in-game chat command to request an invite to the standing fleet (default: !fleet).
* "FleetKickCommand": The in-game chat command to kick someone from the standing fleet (default: !boot).
* "ToggleFleetPublicCommand": The in-game chat command to toggle the standing fleet between public and private (default: !flt-public).
* "CheckFleetStatus": The in-game chat command to check the current status (public/private) of the standing fleet (default: !flt-status).
* "PublicFleetInviteWord": A keyword used in the fleet invite message when the fleet is public. This helps prevent accidental invites (default: "x").
* "AllChatChannel": The Discord channel ID where in-game "All" chat messages will be relayed.
* "TradeChatChannel": The Discord channel ID where in-game "Trade" chat messages will be relayed.
* "TeamChatChannel": The Discord channel ID where in-game "Team" chat messages will be relayed.
* "UseTeamAlerts": Enable or disable team alerts (joins, leaves, promotions, demotions) in Discord (default: true).
* "TeamAlertsChannel": The Discord channel ID where team alerts will be sent.
* "ChannelToPostProdAlerts": The Discord channel ID where construction and base alerts will be sent.
* "EnableIngameManhoursAndSavings": Enable or disable the in-game !manhours and !savings commands (default: true).
* "ConstructionBonusMax": The maximum construction bonus percentage to use in manhour calculations (default: 196).
* "UseBaseAlerts": Enable or disable base alerts (e.g., attacks, construction, fuel) in Discord (default: true).
* "BaseAlertsChannel": The Discord channel ID where base alerts will be sent.
* "MinutesBetweenSpam": The minimum number of minutes between sending repeated alerts for the same message (default: 20).
* "SpamItems": An array of keywords that trigger spam prevention for construction alerts.
* "SendAlertsToTeamChat": Enable or disable sending base and construction alerts to the in-game team chat (default: true).
* "CommandChannel": (Depreciated) Previously used for a dedicated command channel, now handled by slash commands.
* "ErrorChannel": The Discord channel ID where error messages will be sent.
* "ChannelMappings":
* "Game": An array of mappings to relay specific in-game chat channels to Discord channels
* "Discord": An array of mappings to relay specific Discord channels to in-game chat channels


**Important:**

- Replace the placeholders (e.g., your_discord_bot_token_here, 123456789012345678) with your actual information

- Ensure that the channel IDs you provide correspond to existing channels on your Discord server

- If you want the bot to post base alerts e.g construction halted/finished you'll need to dock the bot at your production base**

- If you want the bot to invite multiple of your own characters when you do the join fleet command then you should add those characters to the list in TeamCharacters.json in the format provided. Otherwise it will only invite the character that uses the command.  This is useful if you have people who run multiple clients at once**


**Feel free to ask if you have questions about any specific configuration option or need help setting it up!**

## Commands

Commands
**The bot has a bunch of slash commands through Discord:**

* /fusions [amount] - Calculates the remaining time a galaxy will be owned based on the number of fusion cells.
* /aug [name] - Displays the stats of an Augmenter based on its name.
* /manhours [manhours] [maxworkers] (completion) - Calculates the estimated time to complete a build based on manhours, max workers, and optional completion percentage.
* /savings [amount] (creditCostPerBuild) - Calculates discounts for builds, showing percentage saved and optional total cost details if credit cost per build is provided
* /listgals [owner] - Lists all galaxies owned by a specified player.
* /addgal [owner] [galaxy] - Adds a galaxy to the list of a specified owner.
* /removegal [owner] [galaxy] - Removes a galaxy from the list of a specified owner.
* /admindeleteowner [owner] (Admin Only) - Removes an owner and their galaxies from the list (irreversible).
* /addowner [owner] [discordID] - Adds an owner to the list, associating them with their Discord ID.
* /clear [count] (Admin Only) - Deletes a specified number of messages in the channel.
* /squad - Lists your own squad members (main character and alt characters)
* /whois [character] - Checks who owns a specified character.
* /galaxies - Lists all currently owned galaxies and their owners.
* /owners - Lists all owners in the system
* /stellas - Displays known Stella DG locations.
* /addstella [galaxy] [dg] - Adds a Stella DG location to the list.
* /cyborgs - Displays known Cyborg DG locations (may be disabled based on configuration).
* /addcyborg [galaxy] [dg] - Adds a Cyborg DG location to the list.
* /ubers - Displays known Uber locations.
* /updateuberlocation [name] [location] - Changes the location of an Uber.

**There are also some additional ingame commands (other than the ones you set yourself in the config**

* !manhours [manhours] [workforace] - Calcualtes build time based on the set production % in the config (ConstructionBonusMax).
* !savings [amount] - Calculates savings for bulk builds.
* !ubers - Displays known uber locations and links them for easy AP (update through discord with /updateuberlocation [name] [location])
* !stellas - Displays known stella DG locations and their AP links (update through discord with /addstella)
* !cyborgs - Displays known cyborg DG locations and their AP links (update through discord with /addcyborg)
* ![Join Fleet Command] - Will invite you to a fleet run by the bot (If you wish to have multiple of your own characters invited at the same time, then add them to TeamCharacters.json)




**Note: Some commands may have additional options or require specific permissions. You can access the config in Configuration/StarSonataInfo.json**

## Contributing

I welcome contributions to improve this project! 

* **Feature Requests & Suggestions:** If you have ideas for new features or improvements, please open an issue on GitHub and describe your suggestion in detail.

* **Bug Reports:** If you encounter any bugs or issues, please open an issue on GitHub and provide as much information as possible to help us reproduce and fix the problem. Include steps to reproduce the issue, your operating system and version, and any relevant error messages.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.