# push_state
Pseudocode for supporting pushstate routing via angel_static.

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
