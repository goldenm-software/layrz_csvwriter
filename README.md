# layrz_csvwriter

Lightweight, cross-platform Dart package to write CSV data to a `StringSink`. Supports and extends RFC 4180.

Forked from https://pub.dev/packages/csv_writer to support better cross-platform compatibility.

# Usage

```dart
import 'dart:io';

import 'package:layrz_csvwriter/layrz_csvwriter.dart';

void main() async {
  var numbersFile = File('number_props.csv');
  var numbersCsv = CsvWriter.withHeaders(numbersFile.openWrite(), ['Number', 'Odd?', 'Even?']);

  try {
    for (var i = 0; i < 100; i++) {
      numbersCsv.writeData(data: {'Number': i, 'Odd?': (i % 2) != 0, 'Even?': (i % 2) == 0});
    }
  } finally {
      await numbersCsv.close();
  }
}
```
