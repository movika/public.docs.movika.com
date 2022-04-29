---
title: Interactive History
description: Interactive History
Keywords: Interactive History
sort: 4
---

Within the **MovikaSDK**, the state of an interactive movie is stored in the **MKPlayerState** struct. When working with the player you may need to use the history of the movie in your project, for example, to save the user's choices of interactives or to get the passing time of a certain chapter. 

Viewing and updating the history of user interaction with the interactive movie is done by implementing the **MKPlayerDelegate** delegate and calling next method

```
func mkplayer(_ player: MKPlayer, didUpdate state: MKPlayerState)
```

*Through the **MKPlayerState** struct, the following information about the status of the interactive movie can be obtained:* 

1) Manifest ID
2) Current chapter ID
3) The current time on the chapter
4) The ID of the next chapter
5) Current Story

# Movie state initialization 

In order to initialize a standard player **MKInteractivePlayer** after the **MKPlayerState** struct state has been saved, you need to pass **MKPlayerState** directly as the second argument to the player during the initialization stage using the **setManifestAsset** method. This will create a player with already saved history.

The **setManifestAsset** method is mainly responsible for initializing the interactive movie within manifest, but it also provides an option to save the state of the movie. If the second argument is not passed, the **MKPlayerState** structure will be set default to __nil__ and the movie will be played from beginning.
```
func setManifestAsset(_ manifestAsset: MKManifestAsset, with playerState: MKPlayerState) 
```

(_Careful, in case there is an invalid *ID* in the **MKPlayerState** struct in the *Chapter ID* variable, a __fatalError__ will occur_) 