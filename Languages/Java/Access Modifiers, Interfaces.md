| Method Type | Can Call in Implementing Class? | Can Override? | How to Call?                     |
| ----------- | ------------------------------- | ------------- | -------------------------------- |
| `default`   | ✅ Yes                           | ✅ Yes         | `obj.method()`                   |
| `static`    | ✅ Yes                           | ❌ No          | `InterfaceName.method()`         |
| `private`   | ❌ No (internal use only)        | ❌ No          | Only usable inside the interface |