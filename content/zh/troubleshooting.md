---
title: "故障排除"
category: "Java 程序"
---


## JAR 兼容性列表

`<project path>/userlib` 目录中已知的 JAR 文件兼容性问题。 此页列出问题的 JAR 文件和已知的工作区。

| JAR 文件              | 日志中的异常                                                                                           | 工作                                                             |
| ------------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------- |
| **xml-apis.jar**    | _java.util.burt.ExecutionException: Boxed 错误或 java.lang.NoClassDefFound错误: org/w3c/dom/Document_ | 使用替代的 xml-apis.jar [在这里下载](attachments/16714056/16844051.jar)。 |
| **servlet-api.jar** | _java.lang.Linkage错误：javax/servlet/http/HttpServletRequest_                                      | 从 userlib 目录中删除servlet-api.jar                                 |
