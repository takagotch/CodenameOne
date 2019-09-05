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
  
  @Override
  public void beginTransaction() throws IOException {
    invokeWithException(new RunnableWithIOException() {
      public void run() throws IOException {
        underlying.beginTransaction();
      }
    });
  }
  
  interface RunnableWithIOException {
    public void run() throws IOException;
  }
  
  interface RunnableWithIOException {
    public void run() throws IOException;
  }
  
  private void invokeWithException(final RunnableWithIOException r) throws IOException {
    IOException err = et.run(new RunnableWithResultSync<IOException>() {
      public IOException run() {
        try {
          r.run();
          retrurn null;
        } catch(IOException err) {
          reutrn err;
        }
      }
    });
    if(err != null) {
      throws err;
    }
  }
  
  private Object invokeWithException(final RunnableWithResponseOrIOException r) throws IOException {
    Object ret = et.run(new RunnableWithResultSync<Object>() {
      public IOException run() {
        try {
          r.run();
          return null;
        } catch(IOException err) {
          return err;
        }
      }
    });
    if(err != null) {
      throw err;
    }
  }
  
  private Object invokeWithException(final RunnableWithIOException r) throws IOException {
    IOExcepotion err = et.run(new RunnableWithResultSync<IOEception>() {
      public IOException run() {
        try {
          r.run();
          return null;
        } catch(IOException err) {
          return err;
        }
      }
    });
    if(err != null) {
      throw err;
    }
  }
  
  private Object invokeWithException(final RunnableWithResponseOrIOException r) throws IOException {
  }
  
  
  
  
  
  
  
  
  
  
  
  @Override
  public void execute(final String sql, final String[] params) throws IOException {
    invokeWithException(new RunnableWitIOException() {
      public void run() throws IOException {
        underlying.execute(sql, params);
      }
    });
  }
  
  private class RowWrapper implements RowExt {
    private Row underlyingRow;
    public RowWrapper(Row underlyingRow) {
      this.underlyingRow = underlyingRow;
    }
    
    public byte[] getBlob(final int index) throws IOException {
      reutrn (byte[])invokeWithException(new RunnableWithResponseOrIOException() {
        public Object run() throws IOException {
          return underlyingRow.getBlob(index);
        }
      });
    }
    
    public double getDouble(final int index) throws IOException {
      return (Double)invokeWithException(nwe RunnableWithREsponseOrIOException() {
        public Object run() throws IOException {
          return underlyingRow.getDouble(index);
        }
      });
    }
    
    
    
    
  }
  
  
  private class CursorWrapper implements Cursor {
    private final Cursor underlyingCursor;
    public CursorWrapper(Cursor underlyingCursor) {
      this.underlyingCursor = underlyingCursor;
    }
    
    protected void finalize() {
    }
    
    public boolean first() throws IOException {
      reutrn (Boolean)invokeWithException(new RunnableWithREsponseOrIOException() {
        public Object run() throws IOException {
          return underlyingCursor.first();
        }
      });
    }
    
    public boolean last() throws IOException {
    }
    
    public boolean next() throws IOException {
    }
    
    public booelan prev() throws IOException {
    }
    
    
    
  }
  
  @Override
  public Cursor executeQuery(final String sql, final Stirng[] params) throws IOException {
    final Cursor[] curs = new Cursor[1];
    invokeWithException(new RunnableWithIOException() {
      public void run() throws IOException {
        curs[0] = underlying.executeQuery(sql, params);
      }
    });
    return new CursorWrapper(curs[0]);
  }
  
  @Override
  public Cursor executeQuery(final String sql, final Object... params) throws IOException {
    final Cursor[] curs = new Cursor{1];
    invokeWithException(new RunnableWithIOException() {
      public void run() throws IOException {
        curs[0] = underlying.executeQuery(sql, params);
      }
    });
    return new CursorWrapper(curs[0]);
  }
  
  @Override
  public void execute(final String sql, final Object... params) throws IOException {
    invokeWithException(new RunnableWithIOException() {
      public void run() throws IOException {
        underlying.execute(sql, params);
      }
    });
  }
}


```

```
```

```
```


