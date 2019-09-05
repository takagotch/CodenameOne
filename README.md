### codenameone
---
https://github.com/codenameone/CodenameOne

https://www.codenameone.com/

```java
// CodenameOne/src/com/codename1/db/ThreadSafeDatabase.java

public class ThreadSafeDatabase extends Database {
  private final Database underlying;
  private final EasyThread et;
  
  public ThreadSafeDatabase(Database db) {
    underlying = db;
    et = EasyThread.start("Database");
  }
  
  public EasyThread getThread() {
    return et;
  }
  
  
  
  
  
  
  
  
}


```

```
```

```
```


