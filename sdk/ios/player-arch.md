---
title: Player structure
description: Player structure
keywords: Player structure
sort: 1 
---

![Image](https://raw.githubusercontent.com/movika/public.docs.movika.com/develop/images/ios_player-arch.png)
# Структура плеера
**MKInteractivePlayer** is the main class for working with player based on **MKPlayer**. If you need more detailed setup, you should use **MKPlayer**, otherwise you should use **MKInteractivePlayer**.

### Description of the main components for working with the player
- **MKInteractivePlayer** - is the main class for working with player, responsible for the main logic and player creation. Methods to control player playback are described in **MKPlayerPlayback**.
- **MKEventsContainer** is a protocol responsible for displaying interactives. Basic implementation is described in **MKDefaultsEventsContainer** class. For your own customization, it is possible to implement your own class and embed it in **MKPLayer**. 
- **MKPlayerView** - protocol, which is responsible for video display and playback control in interactive player. Basic implementation is described in **MKDefaultPlayerView** class.

### Player control methods, MKInteractivePlayer class
```
    reset() // Reset player
  
    restart() // Restart the player
    
    pause() // Pause
    
    play() // Startup
  
    seek(to position: Double) // Move to position
  
    canSeek(to position: Double) -> Bool // Method that returns Bool for the current second 

    playNextEvent() // Play the next interactive
  
    playNextChapter() // Play the next chapter
  
    playFirstChapter() // Play the first chapter
  
    playPreviousChapter() // Play the previous chapter
  
    setNextChapter(with chapterId: String) // Set the next chapter to chapterId
 
    replaceCurrentChapter(with chapterId: String) // Change this chapter to chapterId
```
