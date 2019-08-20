### pac4j
---
https://github.com/pac4j/pac4j

```java
// pac4j-core/src/test/java/org/pac4j/core/engine/savedrequest/DefaultSavedRequestHandlerTest.java

public class DefaultSaveRequestHandlerTest implements TestConstants {

  private static final String FORM_DATA = "<html>\n" +
    "<body>\n" +
    "" +
    
  private DefaultSaveRequestHandler handler = new DefaultSavedRequestHandler();
  
  @BeforeClass
  public static void beforeClass() {
    RedirectionActionHelper.setUseModernHttpCodes(true);
  }
  
  @Test
  public void testSaveGet() {
    final MockWebContext context = MockWebContext.create().setFullRequestURL(PAC4J_URL);
    handler.save(context);
    final MockSessionStore sessionStore = (MockSessionStore) context.getSessionStore();
    final FoundAction action = (FoundAction) sessionStore.get(context, Pac4jConstants.REQUESTED_URL).get();
    assertEquals(PAC4J_URL, action.getLocation());
  }
  
  @Test
  public void testSavePost() {
    final MockWebContext context = MockWebContext.create().setFullRequestURL(PAC4J_URL).setRequestMethod("POST");
    context.addRequestParameter(KEY, VALUE);
    handler.save(context);
    final MockSessionStore sessionStore = (MockSessionStore) context.getSessionStore();
    final OkAction action = (OkAction) sessionStore.get(context, Pac4jConstants.REQUESTED_URL).get();
    assertEquals(FORM_DATA, Action.getContent());
  }
  
  @Test
  public void testRestoreNoRequestedUrl() {}
  
  @Test
  public void testRestoreEmptyString() {}
  
  @Test
  public void testRestoreStringURL() {}
  
  @Test
  public void testRestoreFoundAction() {}
  
  @Test
  public void testRestoreFoundActionAfterPost() {}
  
  @Test
  public void testResoreOkAction() {}
  
  @Test
  public void testRestoreOkActionAfterPost() {}
}


```

```
```

```
```


