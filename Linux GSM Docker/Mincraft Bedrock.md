# Installation
Ports Using: `UDP:19132` `UDP:19133`


```bash
docker run -d \
--name MC-Bedrock \
-v /volume1/Docker/<YOURFOLDER>:/data \
-p 19132:19132/udp \
-p 19133:19133/udp \
--restart unless-stopped \
gameservermanagers/gameserver:mcb
```  
# Server Setting
File: ```/serverfiles/server.properties```

| Server  | Values | Descrition | Value |
| :---: | :---: | ------------- | :---: |
| server-name  | ```<YOURSERVERNAME>``` | Used as the server name  | Any string |
| gamemode  | ```survival```  | Sets the game mode for new players | ```survival``` ```creative``` ```adventure``` |
| difficulty  | ```easy``` | Sets the difficulty of the world | ```peaceful``` ```easy``` ```normal``` ```hard``` |
| allow-cheats | ```false``` | If true then cheats like commands can be used | ```true``` ```false``` |
| max-players | ```10``` | The maximum number of players that can play on the server | Any positive integer |
| online-mode | ```true``` | If true then all connected players must be authenticated to Xbox Live.<br>Clients connecting to remote (non-LAN) servers will always require Xbox Live authentication regardless of this setting.<br>If the server accepts connections from the Internet, then it's highly recommended to enable online-mode| ```true``` ```false``` |
| white-list | ```false``` | If true then all connected players must be listed in the separate whitelist.json file.| ```true``` ```false``` |
| server-port | ```19132``` | Which IPv4 port the server should listen to.| ```1 - 65535``` |
| server-portv6 | ```19133``` | Which IPv6 port the server should listen to. | ```1 - 65535``` |
| view-distance | ```32``` | The maximum allowed view distance in number of chunks. | Any positive integer |
| tick-distance | ```4``` | The world will be ticked this many chunks away from any player.| ```4``` ```12``` |
| player-idle-timeout | ```30``` | After a player has idled for this many minutes they will be kicked.<br>If set to 0 then players can idle indefinitely. | Any non-negative integer |
| max-threads | ```8``` | Maximum number of threads the server will try to use.<br>If set to 0 or removed then it will use as many as possible. | Any non-negative integer |
| level-name | ```<YOURWORLD>``` | Name the Level you found in folder ```/serverfiles/worlds/<YOURWORLD>``` | Any positive integer |
| level-seed | | Use to randomize the world | Any string |
| default-player-permission-level | ```member``` | Permission level for new players joining for the first time. | ```visitor``` ```member``` ```operator```|
| texturepack-required | ```false``` | Force clients to use texture packs in the current world | ```true``` ```false``` |
| content-log-file-enabled | ```false``` | Enables logging content errors to a file | ```true``` ```false``` |
| compression-threshold | ```1``` | Determines the smallest size of raw network payload to compress | ```0-65535``` |
| server-authoritative-movement | ```true``` | Enables server authoritative movement. If true, the server will replay local user input on<br>the server and send down corrections when the client's position doesn't match the server's.<br>Corrections will only happen if correct-player-movement is set to true.| ```true``` ```false``` |
| player-movement-score-threshold | ```20``` | The number of incongruent time intervals needed before abnormal behavior is reported.** | Any non-negative integer |
| player-movement-distance-threshold | ```0.3``` | he difference between server and client positions that needs to be exceeded before abnormal behavior is detected.** | Any non-negative integer |
| player-movement-duration-threshold-in-ms | ```500``` | The duration of time the server and client positions can be out of sync<br>(as defined by player-movement-distance-threshold)<br>before the abnormal movement score is incremented.<br>This value is defined in milliseconds.** | |
| correct-player-movement | ```false``` | If true, the client position will get corrected to the server position if the movement score exceeds the threshold.| ```true``` ```false``` |

**= Disabled by server-authoritative-movement

### Admin & OP 
File: ```/serverfiles/permissions.json```

add an admin/OP
To add yourself or another player admin (OP) you need to know its xuid (Xbox Live ID).
If you don't know the xuid here are the steps to follow:

    Signup on https://xboxapi.com/register and chose the free plan
    Validate your registration then click on "Signin to Xbox Live" 
    Once connected go to https://xapi.us/v2/xuid/GAMER_TAG and replace GAMER_TAG by the player's gamer tag

Its xuid should now be displayed, copy it.

Now to add an admin you need to edit your bedrock server permissions.json config file. 

Permissions.json looks like this:

```
[
{
"permission": "operator",
"xuid": "451298348"
},
{
"permission": "member",
"xuid": "52819329"
},
{
"permission": "visitor",
"xuid": "234114123"
}
]
```
