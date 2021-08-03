---
title: "WebSocket"
category: "Mendix Runtime"
description: "Mendix Runtime で websockets を使用する方法の説明"
#menu_order: 99
tags:
  - "ランタイム:"
  - "web socket"
  - "endpoint"
  - "ジャバ"
---

## 1つの紹介

Mendix Runtime は、 `javax.websocket` API を使用してカスタム Web ソケット エンドポイントの登録をサポートします。

All you need to do is to use the method `Core.addWebSocketEndpoint(String path, Endpoint endpoint)` to register an instance of `javax.websocket.Endpoint` to respond to web socket requests on the given path. クライアントのセッション ID は、 `エンドポイント` の `onOpen` メソッドの `EndpointConfig` から取得できます。

{{% alert type="info" %}}
`Core#addRequestHandler`と同様に、Webソケットのエンドポイントの追加は現在のクラスタノードでのみ行われます。 したがって、 **起動後** のマイクロフローで呼び出すことをお勧めします。
{{% /alert %}}

以下は、MendixアプリでWebSocketを登録する方法の例です。

## 2つの例

以下に、エンドポイントの簡単な実装を示します。

```java
import javax.websocket.CloseReason;
import javax.websocket.Endpoint;
import javax.websocket.EndpointConfig;
import javax.websocket.MessageHandler;
import javax.websocket.Session;
import java.io.IOException;
import java.util.HashSet;
import java.util.Set;
import java.util.UUID;

import com.mendix.core.Core;

public class TestEndpoint extends Endpoint {
  Set<Session> sessions = new HashSet<>();

  @Override
  public void onOpen(Session session, EndpointConfig config) {
    String sessionId = (String) config.getUserProperties().get("mxSessionId");
    ISession mxSession = Core.getSessionById(UUID.fromString(sessionId));
    String username = mxSession.getUserName();
    sessions.add(session);
    session.addMessageHandler(new MessageHandler.Whole<String>() {
      @Override
      public void onMessage(String message) {
        if ("test message".equals(message)) {
          try {
            session.getBasicRemote().sendText("test response:" + username);
            session.close();
          } catch (IOException e) {
            e.printStackTrace();
          }
        }
      }
    });

    try {
      session.getBasicRemote().sendText("socket opened");
    } catch (IOException e) {
      e.printStackTrace();
    }
  }

  @Override
  public void onClose(Session session, CloseReason closeReason) {
    System.out.println("Received onClose call with reason: " + closeReason);
    sessions.remove(session);
  }
}
```

このエンドポイントが `Core.addWebSocketEndpoint("/my-endpoint", new websockets.TestEndpoint());` を呼び出して登録されている場合、次の機能は `ws://.../my-endpoint` で利用できます。

* 接続が確立されると、サーバーはメッセージ `を送信します`
* クライアントがメッセージ `テスト メッセージ`を送信した場合、サーバーは `テスト応答で応答します: USERNAME` でウェブソケットを閉じます。
