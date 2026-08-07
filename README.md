🎁 GameCentral Daily System

A fully automated Daily Role Reward System for Discord servers using YAGPDB Custom Commands.

Members can claim one Daily Role every 24 hours, with randomized rarities, Troll Events, Daily Streaks, a Pity System and special Weekend Bonuses.

Built for GameCentral with a modular and future-ready configuration.

---

📸 Preview

🎁 Daily Reward
![Daily Reward](screenshots/Daily-reward.jpg)

💀 Troll Event
![Daily Troll](screenshots/Daily-troll.jpg)

⏳ Cooldown
![Cooldown](screenshots/Daily-cooldown.jpg)

---

✨ Features

🎁 Daily Role Rewards
Receive one random role every 24 hours.

🎲 Rarity System
Roles are divided into four rarity tiers:

- 🟢 Common
- 🔵 Rare
- 🟣 Epic
- 🟡 Legendary

💀 Troll Event
There is a chance that the Daily reward turns into a Troll Event, causing the user to lose their current Daily Role instead of receiving a new one.

🔥 Daily Streak
Every successful Daily claim increases the user's streak.

🎰 Pity System
Repeated non-Epic/Legendary rewards gradually increase the chance of reaching higher rarities.

🌞 Weekend Bonus
The rarity system receives a bonus during Friday, Saturday and Sunday.

⏳ 24-Hour Cooldown
Users can claim their Daily Role once every 24 hours.

🔄 Automatic Role Replacement
The previous Daily Role is automatically removed before the new one is assigned.

📊 Detailed Embeds
Every result is displayed through a clean Discord embed.

🇬🇷 Greek Time Support
Cooldown availability can be displayed using Greek local time, including the correct summer/winter UTC offset.

⚙️ Configurable
Almost every important setting can be changed from one configuration section.

🔮 Future Ready
The system is structured so additional reward mechanics can be added later.

---

🎮 Command

Command| Description
"!daily"| Claim your Daily Role

---

🎁 Rarity System

The Daily System uses a randomized rarity system.

Rarity| Emoji| Role Pool
Common| 🟢| 10 Roles
Rare| 🔵| 6 Roles
Epic| 🟣| 3 Roles
Legendary| 🟡| 1 Role

The system randomly selects a role from the corresponding rarity pool.

🟢 Common

The most frequently awarded rarity.

🔵 Rare

A less common reward tier with a smaller role pool.

🟣 Epic

A high-tier reward with a significantly smaller pool.

🟡 Legendary

The rarest possible Daily reward.

The Legendary reward uses its own dedicated role pool and receives a special embed color.

---

💀 Troll Event

The Daily System includes a Troll Event.

There is a configurable chance for a Daily claim to become a Troll Event instead of a normal reward.

When triggered:

1. 💀 The Troll Event activates.
2. 🔄 The user's existing Daily Role is removed.
3. ❌ No new Daily Role is awarded.
4. ⏳ The normal 24-hour cooldown is applied.
5. 🎭 A random Troll message is displayed.

Example messages include:

«💀 The Daily Role distributor went for coffee. Come back tomorrow.»

«🤡 Congratulations! You won... absolutely nothing.»

«🦝 A raccoon stole your box.»

«🎰 Critical Miss!»

«💣 You fell into a Trap Card!»

This makes the Daily system more unpredictable and entertaining.

---

🔥 Daily Streak

Every successful Daily claim increases the user's streak.

Example:

🔥 Daily Streak: 1
🔥 Daily Streak: 2
🔥 Daily Streak: 3

The streak is stored individually for each Discord user using the YAGPDB database.

The streak is displayed directly inside the reward embed.

---

🎰 Pity System

The Daily System includes a progressive Pity System.

Every non-Epic and non-Legendary reward increases the user's Pity counter.

The system calculates a Pity Bonus based on the number of previous unsuccessful high-rarity rolls.

The bonus is capped to prevent the rarity system from becoming unbalanced.

Pity Configuration

Pity Bonus per 5 claims: +1%
Maximum Pity Bonus: +5%

The Pity counter resets when the user receives:

- 🟣 Epic
- 🟡 Legendary

This gives users a gradually improving chance of receiving a higher-tier reward.

---

🌞 Weekend Bonus

The Daily System provides a special bonus during the weekend period.

The bonus is active on:

- 📅 Friday
- 📅 Saturday
- 📅 Sunday

Current configuration:

Weekend Bonus: +5%

This gives users an additional incentive to claim their Daily during the weekend.

---

⏳ Cooldown System

Each user can claim the Daily Role once every:

24 hours

The cooldown is stored per user using YAGPDB's database system.

If the user attempts to use "!daily" before the cooldown expires, the system displays:

- ⏳ Remaining hours
- 🕑 Remaining minutes
- 🕐 Remaining seconds
- 📅 Next available claim time

Example:

⏳ Remaining Time:

🕒 12 hours
🕑 34 minutes
🕐 21 seconds

📅 Available Again:
07/08/2026 at 21:45:32

---

🔄 Role Management

The system automatically manages Daily Roles.

Before awarding a new Daily Role, it checks all configured Daily Role pools.

If the user already has a Daily Role:

Old Daily Role
      ↓
Remove
      ↓
New Daily Role
      ↓
Assign

This prevents users from accumulating multiple Daily Roles.

---

🎨 Embed System

The system uses different colors for different Daily events.

Event| Color
🎁 Normal Reward| Success Color
⏳ Cooldown| Cooldown Color
💀 Troll| Troll Color
🟡 Legendary| Legendary Color

All embeds use the configured footer:

GameCentral Daily System

---

⚙️ Configuration

The main configuration is located at the beginning of the Custom Command.

{{$config := sdict
    "cooldownKey" "gc_daily_cooldown"
    "pityKey" "gc_daily_pity"
    "streakKey" "gc_daily_streak"

    "cooldown" 86400

    "commonChance" 60
    "rareChance" 88
    "epicChance" 98

    "trollChance" 5

    "weekendBonus" 5
    "maxPityBonus" 5
}}

---

🎲 Chance Configuration

Common Chance: 60
Rare Chance: 88
Epic Chance: 98

The rarity system uses these values as cumulative thresholds.

Current base distribution

Rarity| Base Range
🟢 Common| 1–60
🔵 Rare| 61–88
🟣 Epic| 89–98
🟡 Legendary| 99–100

The final probability can be affected by the Weekend Bonus and Pity System.

---

💀 Troll Configuration

Troll Chance: 5%

Change:

"trollChance" 5

to your preferred percentage.

For example:

"trollChance" 10

would create a 10% Troll Event chance.

---

🌞 Weekend Bonus Configuration

Current value:

"weekendBonus" 5

This represents a +5% bonus during the configured weekend days.

---

🎰 Pity Configuration

Current maximum Pity bonus:

"maxPityBonus" 5

The system increases the Pity Bonus based on accumulated failed high-rarity rolls and caps it at the configured maximum.

---

🏅 Role Pools

Roles are separated into four pools.

🟢 Common

1524022878738059364
1524023080475824271
1524023154308157521
1524023221421211741
1524023289809338428
1524023348672331806
1524023419090243745
1524023481556271185
1524023542910423091
1524023603191087316

🔵 Rare

1524023670962389012
1524023731029151906
1524023791053832366
1524023863862886420
1524023920326611144
1524023979109515304

🟣 Epic

1396486705074405479
1524024041932066866
1524024101738385529

🟡 Legendary

1524024171917480087

You can replace these IDs with your own Discord Role IDs.

---

🗄️ Database Keys

The system uses three user-specific database keys.

Key| Purpose
"gc_daily_cooldown"| Stores the Daily cooldown
"gc_daily_pity"| Stores the user's Pity counter
"gc_daily_streak"| Stores the user's Daily Streak

All values are stored separately for each Discord user.

---

🇬🇷 Timezone

The cooldown expiration display supports Greek local time.

Summer

+3 hours

Current configuration:

{{$next := ($cd.ExpiresAt.Add 10800e9).Format "02/01/2006 στις 15:04:05"}}

Winter

Change:

10800e9

to:

7200e9

This changes the display from UTC+3 to UTC+2.

«⚠️ The cooldown itself remains 24 hours. This offset only affects the displayed availability time.»

---

📋 Example Reward

A successful Daily claim can look like:

🎁 Daily Reward

🎉 Congratulations!

🏅 You won:
Royal Guardian

🎲 Rarity:
🟣 Epic

🔥 Daily Streak: 7

⏰ Come back tomorrow for a new Daily!

---

💀 Example Troll

💀 Daily Troll

🤡 Congratulations! You won...
absolutely nothing.

🏅 Lost Daily Role:
Royal Guardian

💀 Better luck next time!

---

📦 Installation

1. Open your YAGPDB dashboard.
2. Go to Custom Commands.
3. Create a new Custom Command.
4. Set the trigger to:

!daily

5. Paste the Daily System code.
6. Replace the example Role IDs with your own Daily Role IDs.
7. Make sure YAGPDB has permission to:
   - Manage Roles
   - View Channels
   - Send Messages
   - Embed Links
8. Make sure the YAGPDB bot role is higher than all Daily Roles.
9. Save the Custom Command.
10. Test using:

!daily

---

🔐 Permissions

YAGPDB needs permission to manage the configured Daily Roles.

Make sure:

YAGPDB Bot
      ↓
Daily Roles
      ↓
Members

The YAGPDB role must be positioned above every Daily Role it needs to assign or remove.

---

🧪 Testing

For testing purposes, you may temporarily reduce:

"cooldown" 86400

to something smaller, for example:

"cooldown" 60

This allows you to test the system without waiting 24 hours.

After testing, restore:

"cooldown" 86400

---

🛠️ Troubleshooting

❌ Daily Role is not assigned

Check:

- YAGPDB has Manage Roles permission.
- YAGPDB's role is above the Daily Role.
- The Role ID is correct.
- The role has not been deleted.

---

❌ User receives the cooldown message

This means the user already has an active Daily cooldown.

Wait until the displayed expiration time.

---

❌ Previous Daily Role is not removed

Check that the old role exists inside one of the configured:

$common
$rare
$epic
$legendary

role pools.

---

❌ Legendary color does not appear

The reward color is selected using a normal YAGPDB "if" condition.

The system does not use unsupported functions such as "cond".

---

🔮 Future Development

The system is designed to support additional mechanics in future versions.

Possible future additions include:

- 🎁 Special event rewards
- 🎟️ Bonus Daily tokens
- 📈 Advanced streak rewards
- 🏆 Streak milestones
- 🎰 More rarity tiers
- 🌙 Special event days
- 🎉 Seasonal Daily events
- 📊 Statistics
- 🔔 Claim notifications
- 🧩 Additional reward types

---

📜 Version

Current Version: "1.0.0"

System: GameCentral Daily System
Author: Ethelior
Platform: YAGPDB Custom Commands
License: MIT

---

📄 License

This project is licensed under the MIT License.

You are free to use, modify and distribute the system according to the terms of the license.

---

🎮 GameCentral

Built for GameCentral with ❤️ and a little bit of chaos. 💀🎁

«Claim your Daily. Build your Streak. Chase the Legendary. 🌟»

---