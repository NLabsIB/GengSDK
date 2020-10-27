<img src="https://upload.wikimedia.org/wikipedia/en/thumb/b/be/Gamepad.svg/600px-Gamepad.svg.png" width="100" alt="" data-canonical-src="https://avatars1.githubusercontent.com/u/54474115?s=460&v=4">  &nbsp;
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/HTML5_Badge.svg/600px-HTML5_Badge.svg.png" width="100" alt="" data-canonical-src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/HTML5_Badge.svg/600px-HTML5_Badge.svg.png">

# Geng SDK
This repository contains the Geng Javascript SDK for HTML5 games. <br>
This allows you to integrate single player and turn based multiplayer games published on the Geng platform.

# Implementation
<p>Add the following piece of code into your index.html file (head section or body section). Fill gameId and use SDK events when you need it (start game, update local state, etc).</p>
<p>Initialize Geng HTML5 SDK</p>

```js
window["GENG_OPTIONS"] = {
    "gameId": "[YOUR GENG GAME ID HERE]",
    "onEvent": function(event) {
        switch (event.name) {
            case "START:GAME":
                // start game play here
                // startGame()
                break;
            case "OPPONENT:STATE":
                // update game state with opponent last state
                // updateLocalState(event)
                break;
        }
    },
};
(function(d, s, id) {
    let js, fjs = d.getElementsByTagName(s)[0];
    if (d.getElementById(id)) return;
    js = d.createElement(s);
    js.id = id;
    js.src = 'https://geng-games.s3.eu-west-2.amazonaws.com/sdk.min.js';
    fjs.parentNode.insertBefore(js, fjs);
}(document, 'script', 'geng-js-sdk'));
```

## SDK properties
The sdk is available via the window namespace ```window['gengSync']``` <br>
The object returns some properties for you to be able to interact with the sdk:

| Function        | Description |
| --------------- | ----------- |
| ```window['gengSync'].isHost()```    | Checks if the current user is the host        |
| ```window['gengSync'].getUser()```    | Get the current user ```name``` and ```photo```        |
| ```window['gengSync'].getOpponents()```    | Get the list of opponents ```name``` and ```photo```      |
| ```window['gengSync'].sendGameScore()```   | Send the current user score as an ```int```       |
| ```window['gengSync'].sendGameState()```   | Send the current user state as a ```map```       |
| ```window['gengSync'].endGame()```    | End the game session        |


## Events
### SDK EVENTS
Developers should react to the events emitted by the SDK to start the game or update local game state to reflect opponent(s) move.

| Event | Description |
| --- | --- |
| START:GAME | When the SDK is ready. |
| OPPONENT:STATE | When the opponent game state has changed |

# FAQ
<h2>How to upload a game files?</h2>
<p><b>Answer</b>: Contact us when your game is ready to upload. You'll need to compress all game files to a .ZIP file - Root folder of the .ZIP file must include index.html and game files</p>

# Support:
If you have any technical questions or comments, please email us at:
sdk@joingeng.com


