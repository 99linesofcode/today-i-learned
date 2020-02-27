## Visual Studio Code

In order to use XDebug under VS Code install the [PHP Debug extension](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug) by Felix Becker from the extension marketplace. Be sure to check out the documentation for configuration settings and the section on [Remote Host Debugging](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug#remote-host-debugging).

Now, To make VS Code map the files on the server (usually a VM or Docker container) to the right files on your host machine, you have to set the `pathMappings` settings in your `launch.json`. The correct mapping differs and depends on the location of your web directory as well as the document root of your code/framework.

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Listen for XDebug",
      "type": "php",
      "request": "launch",
      "port": 9000,
      "pathMappings": {
        "/var/www/public": "${workspaceFolder}/public"
      }
    },
    {
      "name": "Launch currently open script",
      "type": "php",
      "request": "launch",
      "program": "${file}",
      "cwd": "${fileDirname}",
      "port": 9000
    }
  ]
}
```
