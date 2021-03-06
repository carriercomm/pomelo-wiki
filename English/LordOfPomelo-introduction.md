# LordOfPomelo Introduction
LordOfPomelo is a distributed MMORPG game demo based on Pomelo framework.
 
## The main content of LordOfPomelo
LordOfPomelo covers the core elements of mainstream MMORPG: a number of different game scenes, two kinds of career, a variety of types of tasks, the wide variety of items and weapons, team, copy, and with a variety of monsters and boss battles. Players can move back and forth across multiple virtual scenes, complete the various tasks, improve levels, and interact with other players. 
 
LordOfPomelo adopts a partition-based scene management, said a map to a game scene, and a separate scene server, provides the corresponding service by the server. This design avoids the complex cross-server transactions while providing the server extension support, developers can add new game scene to improve the whole service side load capacity. In order to evaluate the responsiveness of Pomelo server, we adopted real-time game mode in the scene: the player's attack, skill release, pick up and use of items are performed in real time. 
 
The whole game adopts the standard development mode of Pomelo framework, implements the clustering server management, and you can use the support for the linear expansion in LordOfPomelo, adding a new server to improve the overall load capacity. After several rounds of performance testing and optimization, achieves the load capacity of 800 people per single scene, at the same time can ensure a good response time (around 100 ms). 
 
## LordOfPomelo overall architecture 
    
<img src="http://pomelo.netease.com/resource/documentImage/lordofpomelo/lordofpomelo-all-arch.png" alt="lordofpomelo overall architecture" width="600px"></img>

As shown above, LordOfPomelo includes two types of server: game-server and web-server. Web-server is http-based web server, players can do the registration and login logic through the web-server. After completion of verification, the player will connect to the game-server cluster and enter the actual game scene. Game-server is LordOfPomelo's core server cluster, including a group of front-end websocket servers, and the back-end game logic server cluster, game-server architecture as shown below: 
 
<img src="http://pomelo.netease.com/resource/documentImage/lordofpomelo/game-server.png" alt="game server" width="600px"></img>

The client in the above image can be any supporting websocket client, LordOfPomelo's client is implemented using HTML5, not only can run on the PC browser, and can run in other supporting terminals (such as the iPhone, iPad, android devices configured higher). Players on different platforms can do equal and real-time interaction. 
 
As shown above, game-server cluster is divided into two categories: frontend and backend server, frontend server is a group of websocket server cluster, used to dealing with message communications between the websoket clients and is responsible for message forwarding, filtering, broadcasting, and other functions. Backend server is mainly used to handle the game logic, including various types of game logic servers. Among them, the scene server is the most important game server, is mainly responsible for the game scene management, game data updating and saving, client request processing, as well as monsters and NPC behavior driving, etc. These functions are realized through collaborative work with other servers. At the same time, the scene server has also taken a extensible server form, each scene corresponding to a separate scene server. Can increase the game scenes to disperse the pressure of a single server, to improve the overall load. 
 
## LordOfPomelo analysis 
* [LordOfPomelo server introduction] (wiki/LordOfPomelo-server_introduction)
* [LordOfPomelo data compression] (https://github.com/NetEase/pomelo/wiki/Pomelo-%E6%95%B0%E6%8D%AE%E5%8E%8B%E7%BC%A9%E5%8D%8F%E8%AE%AE)
* [LordOfPomelo code organization](wiki/LordOfPomelo-code_organization)
* [LordOfPomelo boot process] (wiki/LordOfPomelo-boot_process)

