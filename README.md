# Simple Hash Decoder

The exercise is to decode string hashed by the following function

```csharp
long GetHash(string s) {
    long h = 7;
    for (int i = 0; i < s.Length; i++)
        h = h * 37 +
           "acegilmnoprstuwxyz".IndexOf(s[i]);
    return h;
}
```

We can generalize the problem by replacing ``7`` with salt variable, ``37`` with devider variable and ``"acegilmnoprstuwxyz"`` with randomizer variable.

### Example of solution (in Java):
```java
String DecodeHash(long salt, long devider,
    String randomizer, long hash) {
    String result = "";
    do {
        long reminder = hash % divider;
        result = randomizer.charAt(reminder) + result;
        hash = (hash - reminder) / divider;
    } while (hash > salt);
    return result;
}
```

### Example of hashes:
```JavaScript
"rano"===13625924
"marzenie"===25157672851591
```

Working code avaliable at https://mielowski.com/simple-hash-decoder/

### Know problems:
- Error can be thrown if randomizer contains less characters than maksimal remainder
- Devider equal 0 cause error