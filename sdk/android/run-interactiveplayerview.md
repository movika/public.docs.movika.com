---
title: Playback
description: Playback
keywords: Playback
sort: 2
---

## Playback

In order to play interactive movies, you need to call the **run** method of the **InteractivePlayerView**
The method itself looks like this:

```
fun run (
     movieBundle: MovieBundle,
     config: Config,
     savedInstanceState: Bundle? = null
)
```

- movieBundle - contains a description of an interactive movie.
- config - configuration of the interactive player.
- savedInstanceState is an instance of the Bundle class. This argument is optional. Used for
  restoring state after re-creating Activity / Fragment.
