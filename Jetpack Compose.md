## Jetpack Compose
- Jetpack Compose is a modern toolkit for building native Android UI.
- Jetpack Compose simplifies and speedup UI development on Android with less code, powerful tools, and intuitive Kotlin APIs
- No need of XML layout
- Programmatically creating the UI widgets using Kotlin language.
- Jetpack Compose Built around composable functions
- Android Studio Preview version needed since it's not stable
- UI preview is available while development similar to XML design

### Composable functions 
- Jetpack Compose functions are called for adding each element in the view.
- Can only be called from within the scope of other composable functions
- Define your app's UI programmatically by describing its shape and data dependencies
- `@Composable` annotation is used for defining Compose functions
- Functions names are in Camel Case

### Preview your function in Android Studio
- Android Studio lets you preview your composable functions within the IDE
- The composable function must not take any parameters.
- Need to Rebuild your project for refresh the preview


### Reference
https://developer.android.com/jetpack/compose/tutorial?gclid=EAIaIQobChMIvK2_isWw8QIVGCQrCh05gQcqEAAYASABEgIxavD_BwE&gclsrc=aw.ds
