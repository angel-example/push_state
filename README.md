# push_state
Pseudocode for supporting pushstate routing via [angel_static](https://github.com/angel-example/static).

The `VirtualDirectory` (including `CachingVirtualDirectory`) API exports `source` property, which points to the `Directory`
the plug-in is serving files out of. Use this to easily serve a static index file on a 404.

```dart
import 'package:angel_common/angel_common.dart';

configureRoutes(Angel app) async {
  var vDir = new VirtualDirectory();
  var indexFile = new File.fromUri(vDir.source.uri.resolve('index.html'));
  
  app.after.add((req, ResponseContext res) async {
    // Instead of throwing a 404, render the `index.html` file...
    await res.sendFile(indexFile);
  });
}
```
