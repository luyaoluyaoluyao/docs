---
title: "トラブルシューティング"
category: "Javaプログラミング"
tags:
  - "studio pro"
---

## JAR互換性リスト

JARファイルに関しては、 `<app path>/userlib` ディレクトリに既知の互換性の制限があります。 このページには、問題のあるJARファイルと既知の回避策がリストされています。

| JARファイル           | ログ内の例外                                                                                                         | 回避策                                                                                 |
| ----------------- | -------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| *xml-apis.jar*    | _java.util.concurrent.ExecutionException: Boxed Error or java.lang.NoClassDefFoundError: org/w3c/dom/Document_ | 代替の *xml-apis.jar*を使用します。これは [こちら](attachments/16714056/16844051.jar) からダウンロードできます。 |
| *servlet-api.jar* | _java.lang.LinkageError: javax/servlet/http/HttpServletRequest_                                                | *servlet-api.jar* を *userlib* ディレクトリから削除します。                                        |
