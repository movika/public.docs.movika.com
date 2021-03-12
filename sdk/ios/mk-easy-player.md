---
title: Ready-to-use player
description: Ready-to-use player
keywords: Ready-to-use player
sort: 4
---

# Ready-to-use player

### MKEasyPlayer

MKEasyPlayer UIView component that allows you to add an interactive player to your project with minimal settings.

This UIView includes:
- MKPlayer (interactive video engine);
- Default implementation of MKPlayerView (video display layer);
- Playback controls (play, pause, rewind, fast forward);
- Playback bar;
- Debug menu for debugging the state of the movie;

use this code to add MKEasyPlayer:
    
```
    let avplayer = AVPlayerView(frame: view.frame)
    avplayer.playerItemAdapter = AVPlayerItemAdapterImpl(videoConfig: VideoTypeConfiguration(videoType: videoType))
    self.view.addSubview(avplayer)

    let mkplayer = MKEasyPlayer(frame: view.frame)
    mkplayer.playerView = avplayer
    avplayer.avPlayerViewDelegate = mkplayer
```

to display the debug menu use:
```
    mkplayer.isShowDebugView = isShowDebugView
```

to keep track of the state of an interactive movie use:
```
\\implement MKPlayerDelegate 
mkplayer.delegate = self 
```
