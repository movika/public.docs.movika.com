---
title: Saving movie state
description: Saving movie state
keywords: Saving movie state
sort: 1
---

# Saving movie state

During movie playback, the state of the movie is automatically saved at the current moment. This kind of saving occurs before the events that change the plot of the film (the user is given a push-button choice of the plot option).

If the user left the movie without watching it, you can give him the opportunity to continue playing from the savepoint. To do this, when calling the self.setup method pass "true" value as startFromSavePoint parameter.

The presence of savepoints can be checked using PlayerRepository class:

```
PlayerRepository.isMoveSaved(movieId: String)
```
