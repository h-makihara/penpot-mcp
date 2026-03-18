# penpot-mcp

起動はそれぞれのディレクトリのdocker-composeをそのまま起動する。

```
$ docker compose up -d
```

ClaudeからMCPを使用する場合
公式（https://github.com/penpot/penpot/tree/develop/mcp#3-connect-an-mcp-client）に従って、mcp-remoteを入れる

## macでnodebrew利用の場合

nodebrewを使用している場合、以下の設定を入れる

- npxのPATHを調べてメモする
  ```
  $ which npx
  /path/to/npx
  ```
- nodeのパスを調べてメモする  
   `/Users/h-makihara/.nodebrew/current/bin/node`のようなパスが返ってくる  
   末尾の`/node`を除いたパスをメモする

  ```
  $ which node
  /path/to/node/node
  ```

- メモしたパスを設定ファイルに食わせる  
  ファイルパスは`~/Library/Application\ Support/Claude/claude_desktop_config.json`  
  Claudeの`設定`>`開発者`>`設定を編集`からでも開ける

  ```
  {
  "mcpServers": {
      "penpot": {
      "command": "/path/to/npx",
      "args": ["-y", "mcp-remote", "http://localhost:4401/sse", "--allow-http"],
      "env": {
          "PATH": "/path/to/node:/usr/local/bin:/usr/bin:/bin"
      }
      }
  },
  }
  ```
