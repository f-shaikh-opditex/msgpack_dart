# msgpack_dart

MessagePack implementation for dart.

Clean, simple, fast and with sane API and implementation.
---
This fork of knopp's masgpack dart package uses an alternative approach for the implementation of the _readint64 and _readUint64 methods of the deserializer so that the method does not return an int64 type.

### Reason for creating this fork:
JavaScript (and by extension dart2js) doesn't natively support 64-bit integers. For this reason, when the deserializer's output contains int64, an exception is thrown.

### How the problem is solved:
From the differet approaches available, this fork uses a platform dependent appraoch that check whether the platform is web or not. If it is not web, it uses the same approach as previously present in the msgpack dart package, but if platform is web, the methods return bigint.
Alternative implementations could also be to return int32 or a custom data type. These alternatives have not been used here.

### Performance of BigInt
For performance differences between relevant data types, refer to this github issue: https://github.com/dart-lang/core/issues/166
