# [Haze](https://chrisbanes.github.io/haze/)

## overview

Haze is a library that provides a composable that can be used to blur the content behind it.
It's designed to be used with the Material3 components.

主体内容使用haze方法修饰

需要模糊的内容使用hazeChild方法修饰


## Usage

```
val hazeState = remember { HazeState() }

Box {
  LazyColumn(
    modifier = Modifier
      .fillMaxSize()
      // Pass it the HazeState we stored above
      .haze(state = hazeState)
  ) {
    // todo
  }

  LargeTopAppBar(
    // Need to make app bar transparent to see the content behind
    colors = TopAppBarDefaults.largeTopAppBarColors(Color.Transparent),
    modifier = Modifier
      // We use hazeChild on anything where we want the background
      // blurred.
      .hazeChild(state = hazeState)
      .fillMaxWidth(),
  )
}
```

## Sample

=== "Scaffold"
  ```
  val hazeState = remember { HazeState() }

  Scaffold(
    topBar = {
      TopAppBar(
        // Need to make app bar transparent to see the content behind
        colors = TopAppBarDefaults.largeTopAppBarColors(Color.Transparent),
        modifier = Modifier
          .hazeChild(state = hazeState)
          .fillMaxWidth(),
      ) {
        /* todo */
      }
    },
    bottomBar = {
      NavigationBar(
        containerColor = Color.Transparent,
        modifier = Modifier
          .hazeChild(state = hazeState)
          .fillMaxWidth(),
      ) {
        /* todo */
      }
    },
  ) {
    LazyVerticalGrid(
      modifier = Modifier
        .haze(
          state = hazeState,
          style = HazeDefaults.style(backgroundColor = MaterialTheme.colorScheme.surface),
        ),
    ) {
      // todo
    }
  }
  ```

