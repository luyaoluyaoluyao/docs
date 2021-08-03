---
title: "WebSocket"
category: "Mendix 运行时间"
description: "如何在Mendix Runtime中使用websockets的描述"
#menu_order: 99
tags:
  - "运行时间"
  - "web 套接字"
  - "endpoint"
  - "贾瓦"
---

## 1 导言

Mendix Runtime 支持使用 `javax.websocket` API注册自定义 Web socket 端点。

您需要做的只是使用方法 `核心。 ddWebSocketEndpoint(路径，端点端点)` 注册一个 `javax的实例。 ebsocket.Endpoint` 响应给定路径上的 web 套接字请求。

{{% alert type="info" %}}
就像 `Core#addRequestHandler`一样，只在当前集群节点上添加一个 web 套接字结束点。 因此，在 **启动后** 微流程中调用它是一个好的做法。
{{% /报警 %}}

下面是如何在 Mendix 应用程序中注册Websocket 的一个例子。

## 2 个示例

以下是一个端点的简单实现方式。

```java
import javax.websocket.CloseReason;
import javax.websocket.Endpoint;
import javax.websocket.EndpointConfig;
import javax.websocket.MessageHandler;
import javax.websocket.Session;
import java.io.IOException;
import java.util.HashSet;
import java.util.Set;

public class TestEndpoint extends Endpoint {
  Set<Session> sessions = new HashSet<>();

  @Override
  public void onOpen(Session session, EndpointConfig config) {
    sessions.add(session);
    session.addMessageHandler(new MessageHandler.Whole<String>() {
      @Override
      public void onMessage(String message) {
        if ("test message".equals(message)) {
          try {
            session.getBasicRemote().sendText("test response");
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

如果此端点通过调用 `Core.addWebSocketEndpoint("/my-endpoint")，新的 websockets.TestEndpoint() 注册。` 然后在 `ws://.../my-endpoint` 上可以找到以下功能：

* 当连接建立时，服务器将发送消息 `套接字打开`
* 如果客户端发送消息 `测试消息`, 服务器响应 `测试响应` 并关闭Web 套接字
